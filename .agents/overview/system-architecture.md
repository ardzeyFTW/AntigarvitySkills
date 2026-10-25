# Architecture & Operational Overview

## 1. System Vision & Purpose
This template provides an autonomous engineering environment designed for seamless human-agent collaboration across hardware and software engineering. It centralizes rules, domain knowledge, operational skills, bug history, and execution policies in a clean, standardized `.agents/` directory.

---

## 2. Directory Layout & Roles

```text
.agents/
├── README.md                      # Entry point and quick-start guide for agents and users
├── rules/                         # Enforceable behavioral & version control policies
│   ├── git-versioning-rules.md    # Strict push/commit rules & patch version bumping
│   └── operational-rules.md       # Quality, preservation, and subagent guidelines
├── skills/                        # Operational playbooks with templates
│   ├── hardware-documentation/    # Hardware specs, pinouts, power, and BOM
│   ├── software-documentation/    # Component-level isolation & contract docs
│   ├── karpathy-llm-wiki/         # Incremental compiler: raw -> pages -> index
│   ├── bug-fixing-logs/           # Persistent debugging memory & troubleshooting logs
│   └── subagent-parallelism/      # 3-step delegation: evaluate -> dispatch -> aggregate
├── wiki/                          # Compounding knowledge base (Karpathy LLM-Wiki)
│   ├── index.md                   # Fast routing registry for all compiled pages
│   ├── raw/                       # Immutable source documents (datasheets, transcripts)
│   └── pages/                     # Compiled markdown concept & architectural pages
├── logs/                          # Persistent issue tracking and bug trial memory
│   ├── bug-index.md               # Master registry of all past and current bugs
│   ├── README.md                  # Logging guidelines
│   └── templates/                 # Reusable issue logs
└── overview/                      # High-level system blueprints
    └── system-architecture.md     # This comprehensive architectural blueprint
```

---

## 3. Core Operational Workflows

### A. Git Commit & Push Workflow
```
[User Explicit Command: "commit" / "push"]
                  │
                  ▼
[Check Existing Version in VERSION/package/pubspec]
                  │
         ┌────────┴────────┐
         │                 │
    (Version Found)   (No Version)
         │                 │
[Bump Last Segment]   [Commit As-Is]
(v1.0.3 -> v1.0.4)         │
         │                 │
         └────────┬────────┘
                  ▼
       [Commit & Push to Remote]
```

### B. Karpathy LLM-Wiki Knowledge Compilation
Instead of re-parsing disparate files on every prompt:
1. **Drop Sources**: Deposit raw transcripts, datasheets, or spec files in `.agents/wiki/raw/`.
2. **Compile**: Use the `karpathy-llm-wiki` skill to distill key knowledge into `.agents/wiki/pages/`.
3. **Route**: Register new concepts in `.agents/wiki/index.md`.

### C. Persistent Bug Memory
1. When a bug occurs: Check `.agents/logs/bug-index.md` first.
2. Read previous attempts so you **never repeat disproven fixes**.
3. Log all new experiments in real-time.
4. Save root causes and verified diffs permanently.

### D. Subagent Parallelism
1. **Evaluate**: Check if the task involves $\ge 3$ independent units with zero write conflicts.
2. **Dispatch**: Deploy subagents with strict, non-overlapping file permissions and standardized output contracts.
3. **Aggregate**: Synthesize deliverables and run project verification tests.
