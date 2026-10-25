---
name: bug-fixing-logs
description: Persistent debugging memory and troubleshooting log protocol. Prevents restarting investigations from scratch when dealing with stubborn, complex, or recurring bugs.
---

# Persistent Bug & Troubleshooting Logs Skill

## Purpose
When working on difficult or elusive bugs, teams and AI agents frequently waste hours re-testing dead ends, repeating failed hypotheses, or losing track of why earlier fixes failed.

This skill provides **persistent debugging memory**:
* Every complex bug is logged with its full trial history.
* When resuming work on a bug—even days or weeks later—the agent immediately reads previous attempts, observations, and disproven hypotheses, picking up exactly where previous sessions left off.

---

## The Debugging Protocol

### Step 1: Pre-Investigation Check (Mandatory)
Before writing any code or proposing solutions:
1. Open `.agents/logs/bug-index.md`.
2. Search for related keywords, error messages, or affected components.
3. If an existing log exists (e.g. `BUG-003-memory-leak.md`), read it completely!
4. Note all **disproven hypotheses** and **failed solutions** so you never repeat them.

### Step 2: Create or Update the Bug Log
If it is a new complex/annoying bug:
1. Assign the next Bug ID: `BUG-<XXX>-<slug>.md` (e.g., `BUG-004-i2c-bus-timeout.md`).
2. Copy `.agents/skills/bug-fixing-logs/templates/BUG_LOG_TEMPLATE.md` into `.agents/logs/`.
3. Register the issue in `.agents/logs/bug-index.md` with status `[INVESTIGATING]`.

### Step 3: Log Each Iteration in Real-Time
For every attempted fix or hypothesis test:
* State the **Hypothesis**: What do you believe is happening and why?
* State the **Action**: What specific file/setting was changed?
* State the **Observation / Outcome**: What was the exact result or error?
* State the **Verdict**: `[FAILED]`, `[PARTIALLY WORKED]`, or `[VALIDATED]`.
* Why did it fail? Document side effects or why the problem persisted.

### Step 4: Resolution & Prevention
Once fixed:
1. Document the exact root cause.
2. Link the verified fix (diff or commit reference).
3. Add a regression test or verification command.
4. Update status in `.agents/logs/bug-index.md` to `[RESOLVED]`.

---

## Reusable Template
Use: `.agents/skills/bug-fixing-logs/templates/BUG_LOG_TEMPLATE.md`
Store all active and closed logs in `.agents/logs/`.
