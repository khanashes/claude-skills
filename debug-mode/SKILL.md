---
name: debug-mode
description: Systematic root cause analysis for a bug or unexpected behavior. Use when user says "I have a bug", "this is broken", or "help me debug".
---
Guide a structured debugging session. Work through these stages — don't skip ahead:

1. **Understand the symptom** — exact error message or unexpected behavior, when it started, is it deterministic or intermittent?
2. **Gather context** — relevant stack trace, recent code changes, environment (dev/staging/prod), load characteristics
3. **Form hypotheses** — list 3-5 plausible root causes ranked by likelihood
4. **Design elimination tests** — for each hypothesis, what's the cheapest way to confirm or rule it out?
5. **Identify the root cause** — not just "the query is slow" but *why* it's slow
6. **Fix and verify** — propose the fix, then describe how to verify it worked and won't regress

Ask clarifying questions one at a time. Explore the codebase if relevant files are accessible.
Don't suggest "try restarting" type fixes — go for root cause.
