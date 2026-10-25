# Raw Knowledge Drop Zone (Immutable Sources)

This directory is part of the **Karpathy LLM-Wiki** system.

## Rules for this Directory
1. **Immutable Ground Truth**: Files placed here (datasheets, transcripts, issue dumps, RFCs, specification PDFs/text) should **NEVER be manually edited** once added.
2. **Audit Trail**: This folder serves as the permanent source of truth for the project.
3. **Naming Convention**: `YYYY-MM-DD-<source-slug>.[md|txt|json|pdf]`
   - Example: `2026-10-25-esp32-wroom-datasheet.md`
   - Example: `2026-10-25-client-interview-requirements.txt`
4. **Compilation**: When a new file is added here, run the `karpathy-llm-wiki` skill to ingest and compile facts into `.agents/wiki/pages/` and update `.agents/wiki/index.md`.
