<!-- Copyright 2026 Mohamed Aouaci. SPDX-License-Identifier: Apache-2.0 -->

# Hallucination-reduction evaluation

## What this document can establish

OmniCouncil asks for neutral claim checks, source inspection where available, counterevidence, uncertainty labels, and truthful verification reports. Research on Chain-of-Verification found reductions on several evaluated tasks, but does not predict the effect of this skill on another model, host, language, or task: [Dhuliawala et al., Findings of ACL 2024](https://aclanthology.org/2024.findings-acl.212/).

This is a measurement protocol, not a benchmark report. No hallucination-reduction percentage has been measured for OmniCouncil. A prompt cannot guarantee that a model stops hallucinating.

## Define the outcome

Freeze a factual task set with answer keys or sources before testing. Label each material claim as supported, contradicted, unsupported/unverifiable, or not applicable. Choose one primary measure and keep it fixed:

- Response-level factual failure rate: responses containing at least one material contradicted or unsupported claim divided by all responses.
- Claim-level unsupported rate: contradicted or unsupported material claims divided by all checkable material claims.

Track refusal/abstention, answer completeness, citation support, task success, latency, and token/cost impact as guardrails.

## Paired test procedure

1. Freeze test prompts and evidence. Include answerable facts, false premises, unknown cases, current facts, source-grounded summaries, and Arabic prompts if relevant.
2. Freeze the host, exact model/version, date, tools, settings, language, and memory state. Do not pool different models or versions.
3. Run clean paired sessions: A without OmniCouncil and B with explicit invocation. Keep tools and source access equal; randomize order.
4. Have two subject-familiar reviewers independently label claims against the frozen evidence, blind to condition where possible. Record adjudication rules. If one reviewer is used, disclose it. Another AI is not ground truth.
5. Report raw counts and rates, absolute percentage-point change, relative change, and a paired 95% confidence interval. Break results down by task and language. Choose sample size with a power analysis for the effect you want to detect.
6. Publish prompts, evidence, grading rules, refusals, failures, tool limits, versions, and holdout policy.

Relative reduction = 100 × (baseline rate − skill rate) / baseline rate. Absolute reduction in percentage points = 100 × (baseline rate − skill rate). Do not report relative reduction if baseline is zero.

For example, a hypothetical drop from 8% to 6.8% is a 15% relative reduction but only a 1.2 percentage-point absolute reduction. This is arithmetic, not an OmniCouncil result. Small differences may require thousands of paired examples; sample size depends on baseline, pairing, and variance.

## Results record

| Host/model/version | Date | Language/tasks | Paired N | Baseline rate | Skill rate | Absolute change | Relative change | 95% CI/method | Refusal and success changes |
| --- | --- | --- | ---: | ---: | ---: | ---: | ---: | --- | --- |
| Not measured | — | — | — | — | — | — | — | — | This repository contains a protocol, not performance results. |

## Release wording

Before testing, say the skill aims to reduce avoidable factual errors through checks. After testing, claim only the measured result for the exact configuration. Do not generalize one model’s result to all AI or imply simulated roles provide independent verification.
