---
name: runbook
description: Generate an operational runbook for a service, job, or infrastructure component. Use for on-call docs, "how do I operate this", or documenting a new service.
---
Generate a runbook by exploring the codebase and producing these sections:

1. **Service overview** — what it does, who owns it, upstream/downstream dependencies, tech stack
2. **Health & monitoring** — health check endpoints, key dashboards, critical metrics to watch
3. **Common failure modes** — for each:
   - Symptoms (what the alert/error looks like)
   - Likely root cause
   - Step-by-step remediation
   - Escalation path if remediation fails
4. **Scaling** — how to scale up/down, autoscaling configuration, manual intervention procedures
5. **Deployment** — how to deploy, how to rollback, any pre/post-deployment checks
6. **Data** — database access, backup/restore procedures, data retention policies
7. **Logs** — where to find logs, useful log queries for common investigations
8. **Configuration** — environment variables, feature flags, secrets rotation
9. **Emergency procedures** — how to disable the service gracefully, circuit breakers, kill switches

Format as a reference document an on-call engineer can follow at 3 AM under pressure — clear steps, no ambiguity.
Explore the codebase for Dockerfiles, CI config, infra-as-code, and config files to populate details.
Ask what service or component to document if not specified.
