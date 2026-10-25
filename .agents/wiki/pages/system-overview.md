# Project System Overview

- **Last Compiled**: 2026-10-25
- **Status**: Active / Baseline Template
- **Maintainer**: Antigravity Pair Programming Agent

---

## 1. Executive Summary
This repository is configured with an autonomous agent template structure under `.agents/`. It establishes standardized workflows for:
* **Strict Git Versioning & Release**: Safe, user-authorized commits and patch-level version bumping.
* **Hardware & Software Component Documentation**: Modular, component-isolated documentation.
* **Karpathy LLM-Wiki Knowledge Compilation**: Incremental synthesis from raw sources to living markdown pages.
* **Persistent Debugging Logs**: Structured memory for complex, recurring bugs to prevent wasted effort.
* **Parallel Subagent Delegation**: Strategic decomposition and parallel execution of independent tasks.

---

## 2. Directory Navigation
- **Rules**: `[.agents/rules/](../rules/)`
- **Skills**: `[.agents/skills/](../skills/)`
- **Master Wiki Index**: `[index.md](../index.md)`
- **Persistent Bug Logs**: `[.agents/logs/](../logs/)`
- **Architecture Overview**: `[.agents/overview/](../overview/)`

---

## 3. Knowledge Ingestion Pipeline
When new project specifications, schematics, or API contracts are introduced:
1. Deposit the raw document in `[.agents/wiki/raw/](../raw/)`.
2. Compile or update specialized pages in `[.agents/wiki/pages/](./)`.
3. Link the new page in `[.agents/wiki/index.md](../index.md)`.
