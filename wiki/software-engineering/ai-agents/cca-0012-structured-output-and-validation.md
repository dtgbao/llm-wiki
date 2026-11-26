---
title: "Claude Certified Architect: Structured output and validation"
kind: source
domain: software-engineering/ai-agents
summary: "Use a schema for output shape, validate facts in code, and retry only when the input can support a correction."
status: draft
confidence: high
tags: [claude-certified-architect, structured-output, validation]
sources: [raw/software-engineering/ai-agents/cca-0012-structured-output-and-validation.html]
created: 2026-11-26
updated: 2026-11-26
---

# Claude Certified Architect: Structured output and validation

## Provenance

- Claude Certified Architect course, lesson 12, tasks 4.3 and 4.4
- [Upstream lesson at the ingested revision](https://github.com/dtgbao/learning/blob/6ab55998ac976cce5852d3030458646f3acb6736/claude-certified-architect/lessons/0012-structured-output-and-validation.html)
- [Local HTML snapshot](../../../raw/software-engineering/ai-agents/cca-0012-structured-output-and-validation.html) (lesson content only; shared quiz scripts, styles and navigation remain upstream)

## Summary

Strict structured output fixes shape, not truth. Model explicit missing or ambiguous states, then apply independent semantic checks before accepting the extraction.

## Key takeaways

- **Schema design:** Use nullable fields for missing information, an explicit unclear category for ambiguity, and an other category with a detail field for unknown types.
- **Validation and retry:** Compare extracted values with the source and recompute derived results. For recoverable failures, pass the original document, failed extraction and specific errors.
- **Evidence boundary:** A retry cannot supply a missing purchase order number or missing document. Preserve the unknown or request more evidence.

## Impacted pages

- [Validating structured model output](validating-structured-model-output.md)
- [Agent escalation and calibrated human review](agent-escalation-and-calibrated-human-review.md)

## Contradictions and open questions

- The lesson distinguishes the exam’s forced-tool options from actual model and mode support. Check the current API documentation before relying on those settings.
- What validation failures are expensive enough to warrant one retry versus immediate human review?
