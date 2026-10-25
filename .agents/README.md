# `.agents` Configuration & Operational Hub

Welcome to the `.agents` control directory. This folder organizes rules, skills, domain knowledge, persistent debugging history, and high-level overviews to ensure reliable, high-velocity engineering.

---

## 📂 Structure Overview

| Folder | Purpose |
| :--- | :--- |
| **`rules/`** | Enforceable rules. Defines the strict commit/push authorization policy and patch version increment protocol (`v1.0.3` $\rightarrow$ `v1.0.4`). |
| **`skills/`** | Standardized operational procedures for hardware documentation, software component documentation, Karpathy LLM-Wiki knowledge compilation, persistent bug logs, and subagent delegation. |
| **`wiki/`** | Karpathy LLM-Wiki directory structure (`raw/`, `pages/`, `index.md`) enabling compounding project memory without re-parsing raw sources. |
| **`logs/`** | Long-term debugging memory for difficult bugs. Documents all tested hypotheses and failed attempts so you never start from scratch. |
| **`overview/`** | High-level system architecture and operational blueprints. |

---

## ⚡ Key Rules at a Glance
1. **Push & Commit Policy**:
   * Commit or push **ONLY** when explicitly requested by the user.
   * **If and only if** a version number is defined, increment the **last variable** (e.g., `v1.0.3` $\rightarrow$ `v1.0.4`) unless the user specified a custom version string.
2. **Modular Documentation**:
   * Hardware has its own dedicated `.md` file detailing pinouts, voltages, and components.
   * Software components each have their own dedicated `.md` file with interface contracts and invariants.
3. **No Repeated Dead Ends**:
   * Consult `.agents/logs/bug-index.md` before troubleshooting. Never repeat disproven hypotheses.
4. **Smart Parallelism**:
   * Evaluate before delegating. Parallelize repetitive or independent workloads across subagents with isolated file boundaries.
