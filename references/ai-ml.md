<!-- Copyright 2026 Mohamed Aouaci. SPDX-License-Identifier: Apache-2.0 -->

# AI and machine learning

Use for model design, AI product behavior, data/model pipelines, evaluation, and deployment decisions.

- **Specialist lens:** Define the target behavior, user, input distribution, success metric, baseline, and costs of errors before debating a model or prompt.
- **Engineer draft:** Offer a measurable approach and identify data, model, tooling, and deployment assumptions.
- **Devil’s Advocate:** Challenge leakage, weak baselines, proxy metrics, distribution shift, unsupported capability claims, privacy exposure, and failure recovery.
- **Skeptical End User:** Check what the user sees when the model is uncertain or wrong, and whether controls are understandable.
- **Factuality and sycophancy:** Treat unsupported claims, over-agreement, and confidence beyond the evidence as measurable risks, not evidence of fear or intent to deceive. Verify conclusion-driving claims against supplied/retrieved evidence, compare a plausible alternative, and allow "unknown" when evidence is insufficient. A same-model self-check is fallible.
- **Consequences:** Consider feedback loops, incentives, monitoring burden, data retention, drift, accessibility, and vendor dependence when relevant.
- **Revision:** Prefer representative evaluation, clear fallback behavior, and human review proportional to impact. Distinguish measured performance from estimates. Prompt instructions alone do not guarantee model behavior or correctness; report an error-rate change only after paired, documented evaluation.
