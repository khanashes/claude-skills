---
name: refactor-plan
description: Plan a safe, incremental refactoring of a module or system. Use when code is tangled, you need to restructure without breaking things, or "how do I refactor this safely".
---
Plan the refactoring as a sequence of safe, independently-deployable steps:

1. **Identify the problems** — what specific code smells or structural issues exist? Name them concretely (god class, feature envy, shotgun surgery, circular deps, etc.)
2. **Define the target** — what does the end state look like? Draw the boundary between what changes and what stays.
3. **Assess test coverage** — what tests exist today? What tests must be added *before* any refactoring begins to catch regressions?
4. **Sequence the steps** — order changes so each step is:
   - Independently deployable (no half-finished states in production)
   - Small enough to review in one PR
   - Reversible if something goes wrong
5. **Migration strategy** — if data or interfaces change:
   - Strangler fig pattern for gradual cutover
   - Feature flags to control rollout
   - Backward-compatible intermediate states
6. **Risk assessment** — for each step, what's the blast radius if it goes wrong? What's the rollback procedure?
7. **Dependencies** — what other teams/services are affected? What coordination is needed?

Output a numbered checklist of steps with: what changes, what to test, and how to roll back.
Explore the codebase to understand the current structure before proposing changes.
Ask what the trigger for this refactoring is — that shapes the priority and scope.
