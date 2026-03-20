---
name: incident
description: Guide through an active incident or draft a postmortem. Use when something is broken in production or user says "we have an incident".
---
Determine mode first: is this an **active incident** (fix now) or a **postmortem** (learn after)?

**Active incident mode:**
1. What is the customer impact right now? (errors, downtime, data loss?)
2. What's the fastest mitigation — rollback, feature flag, rate limit, kill switch?
3. What do we need to monitor to confirm mitigation worked?
4. Who needs to be notified?
Then work toward root cause while mitigation is in place.

**Postmortem mode — draft a blameless postmortem:**
- Summary (1-2 sentences, plain language)
- Timeline (UTC timestamps)
- Root cause (technical, specific)
- Contributing factors
- Impact (users affected, duration, data affected)
- What went well
- What went wrong
- Action items (each with owner + deadline)

Keep the postmortem factual and blameless. Systems failed, not people.
