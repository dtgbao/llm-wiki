---
title: "Claude Certified Architect: Escalation and human review"
kind: source
domain: software-engineering/ai-agents
summary: "Use policy-based escalation in support and calibrate extraction review with segmented accuracy and ongoing sampling."
status: draft
confidence: high
tags: [claude-certified-architect, escalation, human-review]
sources: [raw/software-engineering/ai-agents/cca-0015-escalation-and-human-review.html]
created: 2026-11-26
updated: 2026-11-26
---

# Claude Certified Architect: Escalation and human review

## Provenance

- Claude Certified Architect course, lesson 15, tasks 5.2 and 5.5
- [Upstream lesson at the ingested revision](https://github.com/dtgbao/learning/blob/6ab55998ac976cce5852d3030458646f3acb6736/claude-certified-architect/lessons/0015-escalation-and-human-review.html)
- [Local HTML snapshot](../../../raw/software-engineering/ai-agents/cca-0015-escalation-and-human-review.html) (lesson content only; shared quiz scripts, styles and navigation remain upstream)

## Summary

Escalation decisions need concrete triggers rather than proxies such as negative sentiment. Separately, some extraction output can bypass routine review when labeled evidence supports the acceptance policy and accepted output remains audited.

## Key takeaways

- **Escalation triggers:** Hand off immediately on request, hand off on policy gaps or when meaningful progress stops, and clarify ambiguous identity before guessing or acting.
- **Segmented accuracy:** Measure error rates by document type and field before removing review; an aggregate can hide poor performance on a rare segment.
- **Calibrated routing:** Validate confidence thresholds against labeled examples. Route uncertain or conflicting cases to review and sample auto-accepted results across segments.

## Impacted pages

- [Agent escalation and calibrated human review](agent-escalation-and-calibrated-human-review.md)
- [Deterministic tool gates and handoffs](deterministic-tool-gates-and-handoffs.md)

## Contradictions and open questions

- No contradiction with existing wiki guidance. What minimum labeled sample and acceptance error budget are appropriate for each document and field?
