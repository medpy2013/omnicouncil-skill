<!-- Copyright 2026 Mohamed Aouaci. SPDX-License-Identifier: Apache-2.0 -->

# OmniCouncil output examples

These examples show the visible summary after the user explicitly invokes OmniCouncil. They are templates, not proof that the skill works on every model.

## Small request with a real usability issue

**OmniCouncil review**
- **Specialist:** The user needs a first action, not background theory.
- **Engineer:** Draft a short answer with the action first.
- **Devil’s Advocate:** “Open settings” is ambiguous because the product has two settings menus.
- **Skeptical End User:** A new user may not know which icon opens account settings.
- **Specialist:** Name the account menu and keep the rest brief.

**Maestro — final:** [Revised answer with the exact first action.]

## Straightforward request with no material flaw

**OmniCouncil review**
- **Specialist:** The task is a direct conversion; preserving the supplied meaning is the main criterion.
- **Engineer:** Convert the provided value using the requested format.
- **Devil’s Advocate:** No material flaw found; verify the units are preserved.
- **Skeptical End User:** No material usability issue found; the result should be shown directly.
- **Specialist:** The units are explicit, so no clarification is needed.

**Maestro — final:** [Requested conversion.]

## Cross-domain AI product request

**OmniCouncil review**
- **Specialist (AI product):** Define the user outcome and a representative measure of success.
- **Engineer:** Prototype the smallest workflow with a baseline and a correction path.
- **Devil’s Advocate:** A curated demo could hide poor performance on real inputs.
- **Skeptical End User:** Users need to know when an answer is uncertain and how to correct it.
- **Specialist:** Evaluate representative held-out cases and expose an edit/retry path before broader rollout.

**Maestro — final:** [Revised plan or deliverable.]

## Strict JSON output

If the user requires JSON only, do not prepend council prose. Apply the checks silently and return only valid JSON matching the requested schema.
