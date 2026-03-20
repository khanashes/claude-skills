---
name: dependency-check
description: Audit project dependencies for risks, bloat, and upgrade paths. Use for "should I add this dependency", "audit my deps", or before a major version upgrade.
---
Evaluate dependencies based on the context (adding new, auditing existing, or upgrading):

**Evaluating a new dependency**
- Is it actively maintained? (last release, open issues ratio, bus factor)
- License compatibility with the project
- Bundle/install size and transitive dependency count
- Are there lighter alternatives or can this be done in-house in <50 lines?
- Does it duplicate functionality already in the project's deps?

**Auditing existing dependencies**
- Identify outdated packages with known security advisories
- Flag unused dependencies (imported but never used, or used only in dead code)
- Flag duplicate packages (same purpose, different libraries)
- Check for packages that are unmaintained or archived
- Review lock file health (conflicts, resolution issues)

**Planning a major version upgrade**
- Read the changelog/migration guide for breaking changes
- Identify all usage sites in the codebase that are affected
- Sequence the migration steps (can it be done incrementally?)
- Check peer dependency compatibility
- Identify tests that will need updating

**General recommendations**
- Pinning strategy appropriate to the ecosystem (exact, caret, tilde)
- Separate dev/production dependencies correctly
- Supply chain risk surface (number of transitive deps, known compromised packages)

For each finding: the dependency name, the issue, the risk level, and the recommended action.
Read the project's package manifest and lock file before making recommendations.
