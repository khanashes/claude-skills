# Claude Code Skills

A collection of reusable skills for [Claude Code](https://claude.ai/claude-code) — focused on backend development and architecture workflows.

## Skills

### Code Quality & Review
| Skill | Command | Description |
|-------|---------|-------------|
| PR Review | `/pr-review` | Senior engineer code review with severity-ranked feedback |
| Security Review | `/secure-review` | OWASP-focused security audit of backend code and configuration |
| Schema Review | `/schema-review` | Database schema and migration review for correctness and performance |
| API Design | `/api-design` | Review or design REST/GraphQL APIs for consistency and usability |

### Testing
| Skill | Command | Description |
|-------|---------|-------------|
| Test Strategy | `/test-strategy` | Design a testing approach — pyramid balance, mocks, edge cases |
| API Test Gen | `/api-test-gen` | Generate integration/API tests matching project conventions |

### Debugging & Performance
| Skill | Command | Description |
|-------|---------|-------------|
| Debug Mode | `/debug-mode` | Systematic root cause analysis for bugs |
| Performance Audit | `/perf-audit` | Audit code for performance issues across DB, app, cache, and infra layers |
| Error Handling | `/error-handling` | Audit error handling patterns and resilience strategies |

### Planning & Architecture
| Skill | Command | Description |
|-------|---------|-------------|
| ADR | `/adr` | Draft an Architecture Decision Record |
| Grill Me | `/grill-me` | Stress-test a plan or design with relentless questions |
| Refactor Plan | `/refactor-plan` | Plan safe, incremental refactoring with rollback steps |
| Dependency Check | `/dependency-check` | Evaluate new dependencies or audit existing ones for risks |

### Operations & Observability
| Skill | Command | Description |
|-------|---------|-------------|
| Incident | `/incident` | Guide through an active incident or draft a postmortem |
| Runbook | `/runbook` | Generate operational runbooks for on-call engineers |
| Observability | `/observability` | Design logging, metrics, tracing, and alerting |

### Developer Experience
| Skill | Command | Description |
|-------|---------|-------------|
| Standup | `/standup` | Generate a standup update from recent git commits |
| Env Setup | `/env-setup` | Local dev environment setup and onboarding |

## Usage

1. Clone this repo into your Claude Code skills directory
2. Use any skill by typing its command (e.g., `/api-design`) in Claude Code
3. Each skill will guide you through a structured workflow with clarifying questions

## Structure

Each skill lives in its own directory with a single `SKILL.md` file:

```
skill-name/
  SKILL.md    # YAML frontmatter (name, description) + markdown instructions
```

## Contributing

To add a new skill, create a new directory with a `SKILL.md` file following the existing format:

```yaml
---
name: skill-name
description: One-line description with trigger phrases.
---
Markdown instructions for the skill workflow.
```
