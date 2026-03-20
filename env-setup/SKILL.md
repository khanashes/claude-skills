---
name: env-setup
description: Generate or audit local development environment setup for a project. Use for "help me set up this project", onboarding a new developer, or "why won't this run locally".
---
Analyze the project and produce (or fix) the local development setup:

1. **Prerequisites** — required language runtimes, package managers, and system dependencies with exact version requirements
2. **Services** — databases, caches, queues, and external services needed locally. Review or generate Docker Compose / devcontainer config.
3. **Environment variables** — document every required env var: what it does, whether it has a sensible default, and where to get secrets for local dev
4. **Installation steps** — dependency installation, database setup, migrations, seed data — in copy-paste-ready commands
5. **Verification** — how to confirm the setup works (run tests, hit a health endpoint, see a specific log line)
6. **Common issues** — troubleshoot the most likely failures:
   - Port conflicts
   - Wrong runtime version
   - Missing system dependencies
   - Database connection refused
   - Migration failures
   - Permission issues
7. **Development workflow** — how to run the server, run tests, run linters, access the database, and tail logs
8. **CI parity** — flag any differences between local and CI environments that could cause "works on my machine" issues

Explore the project for Dockerfiles, docker-compose files, Makefiles, CI configs, and README files before generating.
Output should be actionable — a new developer should go from `git clone` to running server by following the output.
Ask what operating system the developer is on if setup is OS-specific.
