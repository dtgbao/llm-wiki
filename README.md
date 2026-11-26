# LLM Wiki

A persistent, Git-synced software engineering knowledge base. Sources preserve
provenance; the wiki turns them into reusable concepts, decisions, blueprints,
practices, conventions, and system notes.

Start with [the content index](wiki/index.md). Use
[the activity log](wiki/log.md) to see when knowledge was ingested, queried, or
linted.

## Knowledge model

- `raw/<domain>/` holds immutable local source material.
- Source records in `wiki/<domain>/` track provenance, summary, extracted
  knowledge, impacted pages, and open questions.
- Durable pages live alongside source records. The frontmatter `kind` describes
  the type of reusable knowledge:

| Kind | Content |
| --- | --- |
| `overview` | A map and synthesis of a domain |
| `entity` | A named product, tool, person, or organization |
| `concept` | Ideas, tradeoffs, algorithms, patterns, and failure modes |
| `decision` | ADR-like decisions, alternatives, and consequences |
| `blueprint` | Reusable architectures, protocols, data flows, and build plans |
| `practice` | Checklists, testing strategies, and operational playbooks |
| `convention` | Coding, API, logging, documentation, and naming rules |
| `system` | Frameworks, libraries, services, tools, and vendors |
| `question` | Durable answers produced while querying the wiki |

Every durable claim should lead back to its source. Prefer updating an existing
page over creating a near-duplicate.

## Repository layout

```text
.
├── README.md
├── AGENTS.md
├── raw/<domain>/
├── wiki/
│   ├── index.md
│   ├── log.md
│   └── <domain>/       # source and durable pages, plus a generated index.md
└── .obsidian/          # Obsidian vault settings
```

The repository root can be opened directly as an Obsidian vault, but all
knowledge remains plain Markdown and works without Obsidian.

## Working with the wiki

Use the [`llm-wiki` skill](https://github.com/dtgbao/agent-skills/tree/main/plugins/llm-wiki) for maintained operations:

- **Ingest:** read one source fully, preserve its provenance, and update reusable
  pages.
- **Query:** search the index and existing synthesis before consulting raw
  sources.
- **Lint:** check schema, links, index coverage, contradictions, staleness,
  provenance, and diagrams.
- **Sync:** commit wiki changes, rebase on the configured remote branch, and push
  without force. Sync only when explicitly requested.

Repository-specific rules and completion checks live in [AGENTS.md](AGENTS.md).
