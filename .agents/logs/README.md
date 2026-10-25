# Persistent Bug & Debugging Logs

This folder maintains long-term memory for bugs, race conditions, hardware quirks, and thorny issues encountered in this project.

## Why this exists
When an annoying or complex bug requires multiple attempted solutions, this folder ensures you **never start over from scratch**. Even if work on a bug is paused for days or weeks, all prior hypotheses, failed attempts, and lessons learned are permanently documented.

## How to use
1. **When a bug is reported**: Check `bug-index.md` first.
2. **If continuing an existing bug**: Read the corresponding `BUG-<ID>-<slug>.md` file to see what failed previously.
3. **If starting a new bug**: Copy `templates/issue-template.md` to `BUG-<ID>-<slug>.md` and add an entry in `bug-index.md`.
4. **During debugging**: Record each attempt in real-time (Hypothesis $\to$ Action $\to$ Observation $\to$ Verdict).
5. **Upon resolution**: Record the root cause, final code diff, and regression test.
