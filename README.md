# LLM Wiki

A pattern for using an LLM to incrementally build and maintain a persistent, structured wiki from raw sources.

Instead of re-discovering knowledge from scratch with retrieval on every question, the LLM incrementally reads new sources, updates a markdown wiki, maintains cross-references, flags contradictions, and keeps the synthesis current over time.

## Core idea

Most document workflows with LLMs look like RAG: you upload files, the model retrieves relevant chunks at query time, and generates an answer. This works, but there is no accumulation. The model must repeatedly rediscover and re-synthesize knowledge from raw material.

LLM Wiki uses a different pattern:

- raw sources are kept immutable
- the LLM maintains a persistent markdown wiki
- the wiki becomes a compounding artifact
- useful answers and analyses can be filed back into the wiki

The result is a maintained knowledge base instead of a temporary chat result.

## Three layers

### 1. Raw sources
Your curated collection of source documents:
- articles
- papers
- notes
- transcripts
- images
- data files

These are the source of truth and are never modified by the LLM.

### 2. The wiki
A directory of LLM-generated markdown files:
- summaries
- entity pages
- concept pages
- comparisons
- overviews
- syntheses

The LLM creates and maintains this layer.

### 3. The schema
A document such as `AGENTS.md` or `CLAUDE.md` that defines:
- structure
- naming conventions
- workflows
- ingest behavior
- query behavior
- maintenance rules

This turns the LLM from a generic chatbot into a disciplined wiki maintainer.

## Operations

### Ingest
When you add a new source, the LLM:
- reads it
- extracts key points
- writes a source summary
- updates relevant concept/entity pages
- updates the index
- appends to the log

### Query
You ask questions against the wiki. The LLM:
- consults the index
- reads relevant pages
- synthesizes an answer with citations
- optionally saves the answer back into the wiki as a new page

### Lint
The LLM periodically checks the wiki for:
- contradictions
- stale claims
- orphan pages
- missing concept pages
- weak cross-linking
- unanswered questions
- gaps worth filling with new sources

## Special files

### `index.md`
A content-oriented catalog of the wiki:
- links to pages
- one-line summaries
- optional metadata

### `log.md`
A chronological append-only record of:
- ingests
- queries
- lint passes
- notable updates

## Example use cases

- personal knowledge management
- research
- book reading companions
- internal business/team wikis
- competitive analysis
- due diligence
- trip planning
- course notes
- hobby deep-dives

## Why this works

The hard part of maintaining a knowledge base is not reading or thinking. It is bookkeeping:
- updating summaries
- maintaining links
- reconciling contradictions
- keeping pages current
- preserving useful outputs

LLMs are unusually well-suited to this maintenance work. Humans curate, direct, and interpret. The LLM handles the repetitive upkeep.

## Inspiration

This pattern is related in spirit to Vannevar Bush’s Memex: a personal, curated knowledge store with associative trails between documents. The missing piece was maintenance. LLMs make that practical.

## Status

This repository currently describes the pattern, not a single fixed implementation. The right structure, workflows, and tools will vary by domain and by LLM environment.

## Source

This repository was initialized from a concept note provided by the author in ChatGPT. :contentReference[oaicite:0]{index=0}
