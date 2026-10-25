<!-- Copyright 2026 Mohamed Aouaci. SPDX-License-Identifier: Apache-2.0 -->

# Software engineering

Use for software architecture, implementation, debugging, review, testing, security, and delivery work.

- **Specialist lens:** Identify system boundaries, invariants, inputs/outputs, failure modes, and the cost of change. Inspect the actual repository and its conventions before proposing code changes.
- **Engineer draft:** State the smallest concrete design or patch that satisfies the request. Separate observed behavior from assumptions.
- **Devil’s Advocate:** Probe regressions, edge cases, error handling, compatibility, maintainability, and security boundaries. Call a flaw critical only when it breaks a core requirement, creates a material vulnerability, or makes the result unusable.
- **Skeptical End User:** Check whether behavior, errors, setup, and interaction make sense to the intended user.
- **Consequences:** Consider migration, operations, data handling, dependencies, and complexity when they matter to the change.
- **Revision and verification:** Fix material issues and state remaining tradeoffs. Run appropriate checks within the user’s requested scope and available time/tools. Report exactly what was and was not checked; never invent results. Do not turn an ordinary change into a full security audit unless requested or warranted.
