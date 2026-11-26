---
title: Deterministic tool gates and handoffs
kind: practice
domain: software-engineering/ai-agents
summary: "Block unsafe or unauthorized tool calls before they run and give the next actor enough evidence to act."
status: draft
confidence: high
tags: [tool-use, guardrails]
sources: [cca-0003-hooks-gates-handoffs.md]
created: 2026-11-26
updated: 2026-11-26
---

# Deterministic tool gates and handoffs

## When to use

Use a code gate when a missed check could move money, expose data, act on the wrong identity, or violate policy. Prompts and examples are suitable for tone or judgment that can tolerate occasional mistakes. See the [course lesson](cca-0003-hooks-gates-handoffs.md).

## Steps

1. Check trusted, request-scoped state before the side effect. Verify that the identity or approval applies to this exact action; deny when proof is missing or does not match.
2. Couple denial with a clear next step: verify the account, ask for approval, or escalate. The denial enforces the policy; the message helps the model recover.
3. Normalize tool outputs in code before the model sees them. Use explicit units, stable timestamps and documented status values.
4. Hand off the relevant account or case ID, issue, verified evidence, actions attempted, blocking rule and suggested next action. Include source references when the recipient can access them.

## Pitfalls

- A post-call hook cannot undo an unsafe write. Check the authoritative boundary on every call path, including headless callers and retries.
- Test missing and mismatched identity, threshold boundaries, and approval expiry. Verify denied cases never reach the side-effecting operation.
- Do not assume the recipient has the transcript or send raw tool dumps with unrelated customer data.

## Related

- [Agent escalation and calibrated human review](agent-escalation-and-calibrated-human-review.md)
- [Multi-agent orchestration blueprint](multi-agent-orchestration.md)
