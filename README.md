# ProjectTemplate & Antigravity Agent Configuration

A reusable template repository configured for high-velocity engineering with autonomous agents.
Upstream repository: [AntigarvitySkills on GitHub](https://github.com/ardzeyFTW/AntigarvitySkills)

---

## 🚀 Features & Agent Capabilities

This template includes a standardized **`.agents/`** ecosystem:

1. **Strict Version Control & Release Rules** (`.agents/rules/git-versioning-rules.md`):
   - Commits and pushes are strictly gated on explicit user authorization.
   - Automatically increments the patch version (`v1.0.3` $\rightarrow$ `v1.0.4`) when committing or releasing.
2. **Hardware Documentation Standard** (`.agents/skills/hardware-documentation/`):
   - Structured templates for microcontroller pinouts, logic voltage levels, power budgets, and sensor wiring maps.
3. **Modular Software Component Documentation** (`.agents/skills/software-documentation/`):
   - Isolated, single-responsibility documentation for every individual UI component, backend service, and data contract.
4. **Karpathy LLM-Wiki System** (`.agents/wiki/` and `.agents/skills/karpathy-llm-wiki/`):
   - Compounding project knowledge based on Andrej Karpathy's LLM-Wiki paradigm.
   - Raw immutable sources (`raw/`) $\rightarrow$ Compiled Markdown concept pages (`pages/`) $\rightarrow$ Master router (`index.md`).
5. **Persistent Bug Memory** (`.agents/logs/` and `.agents/skills/bug-fixing-logs/`):
   - Detailed troubleshooting records tracking every hypothesis and attempted solution.
   - When resuming work on difficult bugs, past failed attempts are never repeated.
6. **Subagent Parallelism & Delegation** (`.agents/skills/subagent-parallelism/`):
   - 3-step delegation framework: Evaluate $\rightarrow$ Decompose & Dispatch $\rightarrow$ Synthesize.

---

## 📁 Repository Structure

```text
├── .agents/
│   ├── rules/
│   │   ├── git-versioning-rules.md
│   │   └── operational-rules.md
│   ├── skills/
│   │   ├── hardware-documentation/
│   │   ├── software-documentation/
│   │   ├── karpathy-llm-wiki/
│   │   ├── bug-fixing-logs/
│   │   └── subagent-parallelism/
│   ├── wiki/
│   │   ├── index.md
│   │   ├── raw/
│   │   └── pages/
│   ├── logs/
│   │   ├── bug-index.md
│   │   ├── BUG-000-example.md
│   │   └── templates/
│   └── overview/
│       └── system-architecture.md
├── .gitignore
├── README.md
└── VERSION
```
