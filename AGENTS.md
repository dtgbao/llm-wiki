# Wiki schema

This file is the schema of this wiki. Agents: read it before every operation.
Where it differs from the generic llm-wiki skill, this file wins.
Use the `llm-wiki` skill for setup, ingestion, durable queries, linting, and sync.
When the user states a new convention, add it under "Local conventions".
Follow this wiki's log rules below.

## Layers

- `raw/<domain>/`: immutable sources. Never edit, move, rename or delete a file here.
  Add sources only with `llm_wiki.py ingest`.
- `wiki/<domain>/`: maintained synthesis. Cite source URLs, raw paths, or source
  pages. Update an existing durable page before creating a near-duplicate.
- `AGENTS.md`: this schema. The user and the agent change it together.

## Domains

- A domain is a path of lowercase kebab-case segments, for example `aws/iam`.
- Store each page and its raw material under exactly one primary domain. Use
  tags and cross-links for secondary domains.
- Every wiki directory has a generated `index.md`. Never edit it by hand.
  The root index lists top-level domains; nested indexes list immediate
  subdomains and local pages. Run `llm_wiki.py index` after page changes.

## Page kinds

- `overview`: the map of a domain and its current synthesis.
- `source`: one raw source: what it says, takeaways, contradictions.
- `entity`: a named thing (product, person, organization, tool).
- `concept`: an idea, mechanism or term.
- `decision`: a choice, its options, rationale and status.
- `practice`: a how-to or rule of thumb, with when to use it.
- `question`: a question that was asked, with the answer and citations.

- Local kinds: `blueprint`, `convention`, and `system`.

<!-- llm-wiki:extra-kinds: blueprint, convention, system -->

Record the kind in frontmatter, not in the directory name. Keep source records
alongside durable pages in their primary domain.

## Frontmatter

Every wiki page except `index.md` and `log.md` starts with this block.
`summary` is one plain sentence of 160 characters or fewer. Indexes use it as is.
`created` is optional.

```yaml
---
title: Page title
kind: concept
domain: area/topic
summary: One plain sentence that says what the page covers.
status: draft
tags: [tag-one, other-domain/topic]
sources: [raw/area/topic/file.md]
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: medium
---
```

Allowed `status` values: `draft`, `evergreen`, `superseded`. Allowed
`confidence` values: `high`, `medium`, `low`.

## Workflows

### Ingest

- Read the entire source, including code, diagrams, tables, footnotes, and
  available local images.
- Propose a primary domain, takeaways, related pages, and contradictions.
  Get explicit approval of the domain before any ingest mutation.
- Run `ingest` and write the source page with provenance, summary, extracted
  SWE atoms, impacted pages, and open questions.
- Merge reusable knowledge into the correct durable pages. Record contradictions
  and superseded claims.
- Run `index` and `lint`. Check that every changed page appears in its local
  index and that ancestor indexes reach the domain. Append a parseable
  `log ingest` entry.

### Query

- Start from `wiki/index.md`, then search and read relevant wiki pages.
- Prefer synthesized pages; use raw sources when the wiki points to them or
  synthesis is insufficient. Cite wiki paths in the answer.
- Save independently useful synthesis in its owning domain as `kind: question`,
  rebuild its indexes, and append a `log query` entry.

### Lint

- Run `lint`. Fix in-scope errors and report any that remain.
- Review contradictions, staleness, orphans, missing pages, provenance,
  domain/path agreement, cross-links, local indexes, and architecture diagrams.
- Fix in-scope drift and append a parseable `log lint` entry. Record suggested
  follow-ups with `--follow-up`.

### Sync

- Sync only after an explicit user request. Review the exact pending wiki
  changes first.
- Commit, fetch, rebase, and push without force. If rebase conflicts occur,
  abort the rebase and ask the user to resolve them.

## Local conventions

<!-- One bullet per convention the user states, with the date. -->
- Treat wiki Markdown as maintained data, not disposable notes.
- Keep `wiki/log.md` append-only. New events use `bootstrap`, `ingest`, `query`,
  or `lint`; Git history records syncs. The historical `migrate` event was
  relabeled to `schema` for lint compatibility.
- Use stable relative Markdown links.
- Add Mermaid diagrams to decisions and blueprints when relationships, flows,
  boundaries, or lifecycle matter.
- Keep credentials and machine-local configuration out of the repository.
