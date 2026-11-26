---
title: "Claude Certified Architect: Hooks, gates and handoffs"
kind: source
domain: software-engineering/ai-agents
summary: "Enforce consequential tool prerequisites before execution and send a self-contained handoff when policy blocks an action."
status: draft
confidence: high
tags: [claude-certified-architect, tool-use, guardrails]
sources: [raw/software-engineering/ai-agents/cca-0003-hooks-gates-handoffs.html]
created: 2026-11-26
updated: 2026-11-26
---

# Claude Certified Architect: Hooks, gates and handoffs

## Provenance

- Claude Certified Architect course, lesson 3, tasks 1.4 and 1.5
- [Upstream lesson at the ingested revision](https://github.com/dtgbao/learning/blob/6ab55998ac976cce5852d3030458646f3acb6736/claude-certified-architect/lessons/0003-hooks-gates-handoffs.html)
- [Local HTML snapshot](../../../raw/software-engineering/ai-agents/cca-0003-hooks-gates-handoffs.html) (lesson content only; shared quiz scripts, styles and navigation remain upstream)

## Summary

A prompt can guide discretionary decisions but cannot guarantee that a prerequisite is checked. Run hard policy checks before the tool executes; normalize the results before the model sees them when different tools represent the same facts differently.

## Key takeaways

- **Prerequisite gate:** Deny a sensitive tool call when verified state is missing. Explain what the agent can do instead.
- **Policy interception:** Block an out-of-policy action and route it to a human when authorized review is possible.
- **Post-tool normalization:** Convert dates and status codes at the tool boundary rather than asking the model to interpret every source format.
- **Structured handoff:** Give the reviewer the issue, verified facts, attempts, blocking rule and recommended action, not a transcript pointer.

## Impacted pages

- [Deterministic tool gates and handoffs](deterministic-tool-gates-and-handoffs.md)
- [Agent escalation and calibrated human review](agent-escalation-and-calibrated-human-review.md)

## Contradictions and open questions

- No contradiction with existing wiki guidance. Which callers and retry paths bypass the host’s hooks and therefore need protection at the tool itself?
