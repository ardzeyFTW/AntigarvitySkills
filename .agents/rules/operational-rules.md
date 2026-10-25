# Operational & Development Rules

## 1. Documentation Integrity & Preservation
* Preserve existing comments, docstrings, and architectural markdown documentation.
* Do not delete or clobber documentation unless explicitly directed by the user.
* When adding or refactoring code, always update the corresponding component or wiki documentation under `.agents/`.

## 2. Bug History & Debugging Memory
* Before attempting to diagnose or fix a recurring, complex, or annoying bug, **always consult `.agents/logs/bug-index.md`**.
* Check prior attempts and failed hypotheses so time is never wasted repeating dead ends.
* Any non-trivial bug that requires multiple iterations or debugging cycles **must** be logged in `.agents/logs/BUG-<ID>-<name>.md`.

## 3. Modular Software & Hardware Documentation
* Hardware systems must have their dedicated markdown file under documentation or wiki, detailing pinouts, electrical ratings, communication protocols, and components.
* Software systems must be modularly documented: each distinct component, service, or module with separate concerns must have its own section or `.md` file.

## 4. Subagent Delegation Discipline
* Only invoke subagents when parallel execution or isolated exploration clearly adds efficiency.
* Avoid redundant subagent creation for quick, linear tasks.
* Always define concrete file boundaries and output formats for each subagent.
