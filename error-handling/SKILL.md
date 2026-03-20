---
name: error-handling
description: Audit error handling or design an error strategy for a service. Use for "are my errors right", "design error handling", or reviewing try/catch patterns.
---
Audit the error handling (or design an error strategy from scratch) across these areas:

**Anti-patterns to flag**
- Bare/generic catches (`except Exception`, empty `catch {}`) that swallow errors silently
- Catching and re-raising without adding context
- Logging an error but continuing as if nothing happened
- Returning success status when an operation actually failed

**Error classification**
- Transient vs permanent errors — which should be retried?
- Client errors (4xx) vs server errors (5xx) — is the distinction correct?
- Expected errors (validation, not found) vs unexpected errors (bugs, infra failures)

**External call resilience**
- Timeouts on every external call (HTTP, DB, cache, queue)
- Circuit breaker pattern for unreliable dependencies
- Retry policy (exponential backoff, jitter, max attempts)
- Fallback/degradation paths when a dependency is down

**Error responses**
- Consistent error envelope across all endpoints
- Machine-readable error codes for client handling
- No stack traces, internal paths, or sensitive data leaked to clients
- Field-level validation errors for user input

**Logging & alerting**
- Errors logged at the right level (ERROR for unexpected, WARN for expected)
- Correlation IDs propagated through the error chain
- Enough context to debug without reproducing (request ID, user ID, input summary)

For each issue: show the problematic code, explain the failure scenario it enables, and provide the fix.
Explore the codebase for existing error handling patterns and middleware before making recommendations.
