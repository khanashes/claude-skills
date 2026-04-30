---
name: new-branch
description: Create a new feature or hotfix branch from a Jira ticket following TRP gitflow conventions. Use when starting work on a new ticket.
user-invocable: true
disable-model-invocation: true
argument-hint: <ticket-number> [title] [feature|hotfix]
---

# Create New Branch from Jira Ticket

You are creating a new git branch for TRP development following gitflow conventions.

## Input

`$ARGUMENTS` contains:
1. **Jira ticket number** (required) — e.g., `1509` or `TRPSB-1509`. If only a number is given, prefix with `TRPSB-`.
2. **Title** (optional) — a short description of the work, e.g., `"Add Monday.com Import Support"`. May be multiple words. If omitted, it will be fetched from Jira automatically.
3. **Branch type** (optional) — `feature` (default) or `hotfix`.

Example invocations:
- `/new-branch 1509` (title fetched from Jira)
- `/new-branch 1509 hotfix` (title fetched from Jira, hotfix branch)
- `/new-branch 1509 Add Monday.com Import Support`
- `/new-branch TRPSB-1509 Add Monday.com Import Support hotfix`
- `/new-branch 1510 Fix login redirect feature`

Parse the arguments: the first token is always the ticket number. The last token may be `feature` or `hotfix` (case-insensitive) — if so, treat it as the branch type. Everything between the ticket number and the branch type keyword (if present) is the title. If no title tokens are found, fetch the title from Jira (see below).

If the ticket number is missing, use `AskUserQuestion` to ask for it.

## Fetching Ticket Details from Jira

When the title is not provided in the arguments, OR if you want to enrich the confirmation step with more context, fetch the ticket from Jira using the Atlassian MCP tools:

1. Use `mcp__claude_ai_Atlassian__getJiraIssue` with:
   - `cloudId`: `b0c0cf72-295c-4c52-a466-ec79c20b4a3f`
   - `issueIdOrKey`: the full ticket key (e.g., `TRPSB-1509`)

2. From the response, extract:
   - **Summary** (`fields.summary`) — use as the branch title if none was provided
   - **Issue type** (`fields.issuetype.name`) — if the issue type is `Bug` and no branch type was explicitly specified, suggest `hotfix` to the user (but still default to `feature` — let them confirm)
   - **Status** (`fields.status.name`) — show in the confirmation step for context

## Step 1: Fetch Jira Details & Confirm with User

First, fetch the ticket details from Jira using `mcp__claude_ai_Atlassian__getJiraIssue` (cloudId: `b0c0cf72-295c-4c52-a466-ec79c20b4a3f`). This is done regardless of whether a title was provided, so you can show the user full context.

Before creating any branch, use `AskUserQuestion` to confirm with the user. Show them:
- Jira ticket key (e.g., `TRPSB-1509`)
- Jira summary (from API)
- Issue type and status (from API)
- Title being used for the branch name (user-provided or from Jira summary)
- Branch type (`feature` or `hotfix`) — if issue type is `Bug` and no explicit branch type given, mention this and suggest `hotfix`
- Generated branch name (see naming convention below)
- Base branch that will be used
- PR merge behavior (see rules below)

Ask them to confirm or adjust.

## Step 2: Create and Push the Branch

### Branch Naming Convention

```
<type>/TRPSB-<ticket_number>_<snake_case_title>
```

- `<type>`: `feature` or `hotfix`
- `<snake_case_title>`: Convert the title to lowercase, replace spaces and special characters with underscores, remove consecutive underscores, trim to a reasonable length (max ~50 chars).

Example: Ticket `1509` with title "Add Monday.com Import Support" becomes:
```
feature/TRPSB-1509_add_monday_com_import_support
```

### Base Branch Rules (Gitflow)

| Branch Type | Default Base | PR Merges Into |
|-------------|-------------|----------------|
| `feature`   | `develop`   | `develop` only |
| `hotfix`    | `master`    | Both `master` AND `develop` |

- If the user explicitly specifies a different base branch for a hotfix (e.g., base on `develop`), use that instead of `master`.
- Feature branches are ALWAYS based on `develop`.

### Git Commands

1. Fetch latest from origin:
   ```bash
   git fetch origin
   ```

2. Create the branch from the appropriate base:
   ```bash
   git checkout -b <branch_name> origin/<base_branch>
   ```

3. Push the branch to origin and set upstream:
   ```bash
   git push -u origin <branch_name>
   ```

## Step 3: Summary

After successfully creating and pushing the branch, display a summary:

- Branch name
- Base branch
- Jira ticket key
- PR merge target(s) reminder:
  - If base is `develop`: "When PR is closed, it will merge into `develop` only."
  - If base is `master`: "When PR is closed, it will merge into both `master` and `develop`."

## Important Notes

- ALWAYS ask the user to confirm before creating the branch.
- NEVER force-push or delete existing branches.
- If the branch already exists (locally or on origin), warn the user and ask how to proceed.
