---
title: Agent escalation and calibrated human review
kind: practice
domain: software-engineering/ai-agents
summary: "Define explicit support escalation criteria and use calibrated field-level evidence to route and audit extraction review."
status: draft
confidence: high
tags: [escalation, human-review]
sources: [cca-0015-escalation-and-human-review.md]
created: 2026-11-26
updated: 2026-11-26
---

# Agent escalation and calibrated human review

## When to use

Support escalation decides whether an agent can continue a live case. Extraction review decides whether a data record is safe to accept. Treat their decision signals separately; see the [course lesson](cca-0015-escalation-and-human-review.md).

## Steps

1. Escalate a support case on a direct request for a human, a policy exception or gap, or an inability to make meaningful progress. A covered case may still be complex or frustrating; resolve it within policy. Ask for an identifier if account matching is ambiguous.
2. Give the agent contrasting examples of each boundary and send a [structured handoff](deterministic-tool-gates-and-handoffs.md) when it escalates.
3. For extraction, label a representative validation set and measure field error rates by document type. Choose thresholds from observed error and acceptance rates, not arbitrary confidence scores.
4. Send low-confidence or ambiguous cases and conflicting source documents to review. Keep stratified random sampling of auto-accepted records to measure errors and detect new patterns. Revisit thresholds when the document mix or model changes.

## Pitfalls

- Do not equate angry tone with a policy exception or delay an explicit request for a person.
- Do not reduce review based on one overall accuracy number. A large invoice segment can conceal poor results for handwritten receipts.
- A field confidence score is useful only to the extent that labeled data supports it; calibration does not replace sampling.

## Related

- [Validating structured model output](validating-structured-model-output.md)
