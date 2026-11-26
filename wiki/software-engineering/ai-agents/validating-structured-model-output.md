---
title: Validating structured model output
kind: practice
domain: software-engineering/ai-agents
summary: "Validate meaning independently of schema compliance and retry only when the source can support a correction."
status: draft
confidence: high
tags: [structured-output, validation]
sources: [cca-0012-structured-output-and-validation.md]
created: 2026-11-26
updated: 2026-11-26
---

# Validating structured model output

## When to use

Use this pattern when extracting facts into records that drive automated decisions or writes. A valid field type does not prove the value is correct. See the [course lesson](cca-0012-structured-output-and-validation.md).

## Steps

1. Require the expected structure, but let fields represent missing or uncertain values explicitly. For example, require the purchase-order key while allowing null when the invoice has no purchase order.
2. Apply semantic checks in code. For invoices, independently sum line items with the correct currency precision and compare the result to the stated total. Keep both values when they disagree.
3. For a recoverable error, re-run extraction with the original input, previous output and a precise message such as “line items sum to 410.00, stated total is 440.00.” Bound retries and validate again before using the result.
4. When data is missing or sources conflict, preserve the unknown or conflict, request missing evidence, and use [human review](agent-escalation-and-calibrated-human-review.md) when the risk warrants it.

## Pitfalls

- A schema cannot detect swapped vendor and customer fields or invented numbers that have valid types.
- Forcing a tool and validating its arguments are different guarantees. Check that the selected model and mode support the tool-choice setting; test the branch where no tool call is returned.

## Related

- [Deterministic tool gates and handoffs](deterministic-tool-gates-and-handoffs.md)
