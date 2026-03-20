---
name: test-strategy
description: Design or review a testing approach for a feature, service, or module. Use when asking "how should I test this", "is my test coverage right", or planning tests for a new feature.
---
Design (or review) the testing strategy. Work through these layers:

1. **Test pyramid balance** — what belongs in unit vs integration vs e2e for this specific feature? Don't default to "more unit tests" — match the layer to the risk.
2. **What to mock vs what to hit real** — mock external services and side effects; test against real databases and core logic. Justify each boundary.
3. **Critical paths** — identify the 3-5 scenarios that, if broken, cause the most damage. These get the most thorough coverage.
4. **Edge cases** — nulls, empty collections, boundary values, max lengths, concurrent access, clock-dependent behavior, unicode/encoding
5. **Error paths** — invalid input, downstream failures, timeouts, partial failures, auth failures
6. **Test data** — factories/fixtures vs inline data, seed data management, test isolation strategy (transactions, truncation)
7. **Async & background jobs** — how to test queued work, retries, idempotency
8. **Flaky test prevention** — time-dependent tests, ordering dependencies, shared mutable state, network calls in tests
9. **Contract tests** — if this service has consumers, what contracts need enforcement?

Output a prioritized list of test cases grouped by type (unit/integration/e2e).
If reviewing existing tests, identify gaps and over-tested areas (testing implementation details rather than behavior).
Ask what the most critical user-facing flow is if unclear.
