<!-- Copyright 2026 Mohamed Aouaci. SPDX-License-Identifier: Apache-2.0 -->

# Hallucination-reduction evaluation

## What this protocol can establish

OmniCouncil adds claim checking, evidence retrieval where available, counterevidence review, uncertainty labels, and honest verification reports. A published study of Chain-of-Verification found reduced hallucinations on several evaluated tasks; that result supports testing verification workflows, but it does **not** predict the effect of this skill on another model, host, language, or task.

This file defines how to measure the change. It is not a benchmark report. No reduction percentage is currently claimed for OmniCouncil. A prompt cannot guarantee that a model stops hallucinating. If 15–20% is the desired target, treat it as a preregistered hypothesis for a specific host, model, language, and task set—not an achieved result. Specify whether the target is relative reduction or percentage-point change before testing.

Reference: Dhuliawala et al., [“Chain-of-Verification Reduces Hallucination in Large Language Models” (Findings of ACL 2024)](https://aclanthology.org/2024.findings-acl.212/).

## Define the outcome before testing

Use a factual task set with an answer key or evidence sources selected before running the model. Label each material claim as:

- **Supported** — the designated evidence directly supports it.
- **Contradicted** — reliable evidence conflicts with it.
- **Unsupported / unverifiable** — the evidence set does not establish it.
- **Not applicable** — creative content or a claim outside the task’s factual target.

Choose one primary measure and keep it fixed across both conditions:

1. **Response-level factual failure rate (recommended):** responses containing at least one material contradicted or unsupported claim divided by all evaluated responses.
2. **Claim-level unsupported rate (secondary):** contradicted or unsupported material claims divided by all material claims that can be checked.

Track refusal/abstention, answer completeness, citation support, task success, latency, and token/cost impact as guardrails. Lower factual error paired with sharply higher unnecessary refusal is not an unqualified win.

## Paired test procedure

1. **Freeze the test set.** Include answerable facts, false premises, ambiguous/unknown cases, current facts, source-grounded summaries, and Arabic prompts if Arabic use is part of the intended audience. Keep answers and authoritative evidence separate from the prompt shown to the model.
2. **Freeze the environment.** Record host, exact model/version, date, system settings, tools and tool access, temperature or equivalent, language, and whether memory is enabled. Do not combine different models or versions into one result.
3. **Run both conditions.** For each prompt, start clean sessions and run (A) the task without OmniCouncil and (B) the identical task with explicit OmniCouncil invocation. Give both the same tools and source access. Randomize condition order and avoid exposing the grader to condition labels.
4. **Grade the same unit.** Two reviewers familiar with the subject independently label material claims against the frozen evidence; resolve disagreements and record the adjudication rule. If only one reviewer is available, disclose this limitation. A second AI model can help triage, but is not ground truth.
5. **Compare paired outcomes.** Report raw counts and rates for both conditions, absolute percentage-point change, relative change, and a 95% confidence interval using a paired method appropriate to the data. Include each task category and language, not only a pooled average.
6. **Publish every limitation.** Include the test prompts or a reproducible description, evidence set, grading rules, failures, refusals, tool failures, and the exact versions tested. Keep a separate holdout set for later revisions where possible.

Use a power analysis to choose the sample size for the effect you want to detect. A small pilot can reveal obvious defects; it cannot substantiate a small percentage improvement. For example, a drop from 8% to 6.8% is a **15% relative reduction** but only a **1.2 percentage-point absolute reduction**. That is arithmetic for a hypothetical target, not an OmniCouncil result. A sufficiently precise test of a small difference can require thousands of examples; the needed number depends on baseline rate, pairing, variance, and desired confidence.

## Calculation

Let `p_base` be the response-level factual failure rate without the skill and `p_skill` the rate with it:

```text
absolute reduction (percentage points) = 100 × (p_base − p_skill)
relative reduction (percent) = 100 × (p_base − p_skill) / p_base
```

Do not report relative reduction if `p_base` is zero. Do not claim a verified improvement if the uncertainty interval includes no change or the test set is too small to distinguish the effect. State the observed result and interval instead.

## Results record

| Host / model version | Date | Language / task set | N paired prompts | Baseline failure rate | Skill failure rate | Absolute change | Relative change | 95% CI / method | Refusal and task-success changes | Reviewer notes |
| --- | --- | --- | ---: | ---: | ---: | ---: | ---: | --- | --- | --- |
| Not yet measured | — | — | — | — | — | — | — | — | — | This repository contains the protocol, not performance results. |

## Release wording

Before running this protocol, say that the skill **aims to reduce avoidable factual errors** through evidence checks. Afterward, report only the measured result for the exact host, model version, language, and test set. Do not generalize a result from one configuration to “AI models” broadly, and do not claim that a simulated council provides independent verification.
