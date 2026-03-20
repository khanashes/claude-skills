---
name: observability
description: Design or review logging, metrics, and tracing for a service or feature. Use for "what should I log", "add monitoring to this", or "design alerts for this service".
---
Design (or audit) the observability setup across three pillars:

**Logging**
- Structured logging format (JSON with consistent fields)
- Required fields: timestamp, level, correlation/request ID, service name
- What to log at each level (ERROR: unexpected failures, WARN: degraded but functioning, INFO: key business events, DEBUG: diagnostic detail)
- What NOT to log (PII, secrets, full request/response bodies in production)
- Log sampling strategy for high-throughput paths

**Metrics**
- RED metrics for every endpoint: Rate, Errors, Duration (histograms, not averages)
- Resource metrics: connection pools, queue depths, cache hit rates
- Business metrics: signups, orders, key user actions
- Cardinality management — avoid high-cardinality labels (user IDs, request IDs)
- Naming conventions consistent with the project's metrics system

**Tracing**
- Span design for cross-service flows (what operations get their own span?)
- Context propagation between services
- Key attributes to attach to spans (user ID, tenant ID, feature flags)
- Sampling strategy (head-based vs tail-based, sample rate)

**Alerting**
- SLI/SLO definitions for the service (availability, latency, correctness)
- Alert on burn rate, not raw thresholds — avoid alert fatigue
- Runbook link in every alert
- Severity tiers (page vs ticket vs dashboard-only)

For each recommendation: what to instrument, where in the code, and the specific implementation.
Explore the codebase for existing logging/metrics libraries and patterns before recommending.
