---
name: karpathy-llm-wiki
description: Incremental knowledge compilation and wiki maintenance based on Andrej Karpathy's LLM-Wiki paradigm. Compiles immutable raw sources into interlinked Markdown pages.
---

# Karpathy LLM-Wiki Skill

Based on Andrej Karpathy's **`llm-wiki.md`** pattern for compounding personal and project knowledge bases without relying on heavy vector databases or repetitive raw retrieval.

## The Problem It Solves
Traditional RAG (Retrieval-Augmented Generation) re-searches and re-synthesizes knowledge from raw documents *from scratch on every query*. Over time, context windows fill up with redundant chunks and conflicting observations.

The **LLM-Wiki** paradigm operates like an **incremental compiler**:
1. Raw source materials are dropped into `raw/` as immutable artifacts.
2. The agent reads raw inputs and incrementally compiles distilled, cross-referenced Markdown pages in `pages/`.
3. A top-level `index.md` routes queries to relevant pages within seconds.

```
[Raw Sources: PDFs, specs, transcripts] (Immutable)
                  │
                  ▼  (Incremental Compilation / Ingestion)
[Wiki Pages: Concepts, Entities, Systems] (Compounding Markdown)
                  ▲
                  │  (Fast Routing & Discovery)
[index.md: Master Schema & Topic Registry]
```

---

## Directory Layout in `.agents/wiki/`
```
.agents/wiki/
├── index.md             # Master catalog and routing table of all wiki pages
├── raw/                 # Immutable ground-truth drop zone
│   ├── 2026-10-datasheet-bme280.md
│   └── 2026-10-api-spec-v1.md
└── pages/               # LLM-maintained synthesized topic pages
    ├── architecture-core.md
    ├── sensor-pipeline.md
    └── authentication-flow.md
```

---

## The Three Core Agent Operations

### 1. Ingestion (`ingest`)
When new documents, logs, datasheets, or transcripts are added to `raw/`:
1. Read the new raw file.
2. Identify existing pages in `pages/` that are affected, or decide if a new page is required.
3. Update or create the target pages in `pages/`:
   - Incorporate the new facts.
   - Resolve any contradictions with existing text.
   - Link related concepts using standard markdown links: `[Related Page](related-page.md)`.
   - Provide citations referencing the source: `(Source: [[raw/filename.md]])`.
4. Update `.agents/wiki/index.md` with links and 1-line summaries.

### 2. Querying (`query`)
When answering architectural, domain, or design questions:
1. First read `.agents/wiki/index.md` to identify the most relevant pages.
2. Load only the targeted wiki pages.
3. Answer the user's question directly with high confidence and concise citations.

### 3. Linting & Consolidation (`lint`)
Periodically inspect `pages/`:
- Check for dead markdown links.
- Merge duplicate or overlapping concepts into canonical pages.
- Highlight unresolved contradictions between historical raw sources.
- Refresh the index file.

---

## Reusable Templates
* Raw Entry Template: `.agents/skills/karpathy-llm-wiki/templates/RAW_ENTRY_TEMPLATE.md`
* Compiled Page Template: `.agents/skills/karpathy-llm-wiki/templates/WIKI_PAGE_TEMPLATE.md`
