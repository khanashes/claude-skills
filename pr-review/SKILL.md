---
name: pr-review
description: Perform a thorough senior engineer code review. Use when user asks for PR review, code review, or "review this diff".
---
Review this code as a senior backend engineer would. Structure feedback by severity:

**🔴 Blocking** — bugs, security issues, data loss risks, broken logic
**🟡 Should fix** — performance problems, missing error handling, bad abstractions  
**🟢 Suggestions** — style, naming, readability, tests

For each item:
- Quote the specific line(s)
- Explain the risk or reasoning
- Provide the corrected version

Also check:
- Are edge cases handled? (empty inputs, concurrent writes, timeouts)
- Is error handling correct and specific (not bare `except Exception`)?
- Are there N+1 query risks?
- Is anything untestable due to tight coupling?
- Does this match the existing patterns in the codebase?

End with: what's done well and should be kept.
