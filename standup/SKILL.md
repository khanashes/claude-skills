---
name: standup
description: Generate a standup update from recent git commits and TODO comments. Use when user asks for standup, daily update, or "what did I do today".
---
Generate a standup update by:

1. Run: `git log --oneline --since="yesterday" --author="$(git config user.name)"`
2. Run: `git diff --stat HEAD~5..HEAD` for file-level context
3. Check for any TODO/FIXME comments I added recently if relevant

Then write a standup in this format:

**Yesterday**
[3-5 bullet points from commits, translated from technical commit messages to plain impact language]

**Today**
[Infer from incomplete work, open branches, or ask me if unclear]

**Blockers**
[Ask me explicitly — don't invent blockers]

Keep bullets under 15 words each. No jargon in the "Yesterday" section.
