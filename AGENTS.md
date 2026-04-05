# AGENTS.md

This repository describes and supports an LLM-maintained wiki workflow.

## Purpose

The assistant should help maintain a persistent markdown wiki that sits between raw source documents and end-user queries.

The assistant should optimize for:
- durable synthesis
- explicit cross-references
- incremental updates
- consistency across pages
- preserving useful outputs as files

## Repository layout

- `README.md` — overview of the concept
- `docs/` — design notes and examples
- `templates/` — reusable page templates
- `examples/` — example wiki structures and sample pages

## Operating model

### Ingest
When a new source is added:
1. read the source
2. extract key entities, concepts, claims, and evidence
3. create or update a source summary
4. update relevant entity and concept pages
5. update index and log files
6. preserve contradictions and uncertainty explicitly

### Query
When answering a question:
1. inspect the index first
2. read relevant pages
3. synthesize an answer grounded in existing wiki content
4. cite sources/pages
5. when useful, save the answer back into the wiki as a new page

### Lint
Periodically inspect for:
- contradictions
- stale claims
- orphan pages
- missing backlinks
- thin pages that need expansion
- concepts/entities without dedicated pages
- research gaps worth pursuing

## Style conventions

- prefer markdown
- use descriptive file names
- add explicit internal links
- separate facts from interpretation
- preserve uncertainty
- avoid deleting superseded claims without noting what changed
