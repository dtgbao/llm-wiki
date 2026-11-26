---
title: "Claude Certified Architect: Coordinators and subagents"
kind: source
domain: software-engineering/ai-agents
summary: "Delegate complete, non-overlapping assignments and pass source-attributed findings explicitly to synthesis."
status: draft
confidence: high
tags: [claude-certified-architect, orchestration, delegation]
sources: [raw/software-engineering/ai-agents/cca-0002-coordinators-and-subagents.html]
created: 2026-11-26
updated: 2026-11-26
---

# Claude Certified Architect: Coordinators and subagents

## Provenance

- Claude Certified Architect course, lesson 2, tasks 1.2 and 1.3
- [Upstream lesson at the ingested revision](https://github.com/dtgbao/learning/blob/6ab55998ac976cce5852d3030458646f3acb6736/claude-certified-architect/lessons/0002-coordinators-and-subagents.html)
- [Local HTML snapshot](../../../raw/software-engineering/ai-agents/cca-0002-coordinators-and-subagents.html) (lesson content only; shared quiz scripts, styles and navigation remain upstream)

## Summary

A coordinator chooses which agents to run, assigns independent work and integrates it. Fresh subagents cannot rely on parent conversation history, so delegation must carry the evidence and constraints the next agent needs.

## Key takeaways

- **Coordinator’s four jobs:** Split by subject, check coverage and overlap, then select only the workers the query needs. When all workers succeed but the report is narrow, inspect assignments before tuning workers.
- **Context passing:** Give each worker an objective, evidence, an output format, allowed tools or sources, and clear boundaries. Pass findings as records with separate claim, excerpt and source locator fields.
- **Refinement:** Send targeted follow-up work for missing areas; then synthesize again instead of inferring missing facts.

## Impacted pages

- [Multi-agent orchestration blueprint](multi-agent-orchestration.md): adds the handoff and coverage checks.

## Contradictions and open questions

- The lesson routes all messages via the coordinator; the Codex blueprint also permits direct evidence handoffs. Use the hub when central auditing or filtering is required; otherwise make the route explicit and keep the coordinator informed.
- What context and tool restrictions does each supported host actually inherit when spawning or forking a worker?
