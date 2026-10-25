# Bug Log: [BUG-XXX] - [Short Descriptive Title]

- **Bug ID**: `BUG-[XXX]`
- **Status**: [OPEN | INVESTIGATING | WORKAROUND_APPLIED | RESOLVED | BLOCKED]
- **Severity**: [Low | Medium | High | Critical / Blocker]
- **Date Opened**: [YYYY-MM-DD]
- **Last Updated**: [YYYY-MM-DD]
- **Affected Area**: [Component / Hardware Pin / API Route / Database]

---

## 1. Symptoms & Reproduction

### Error Message / Stack Trace
```text
[Paste exact error messages, console logs, or panic outputs here]
```

### Steps to Reproduce
1. [Step 1]
2. [Step 2]
3. [Step 3]

### Expected Behavior
[What should happen]

### Observed Behavior
[What actually happens]

---

## 2. Environment & System State
- **OS / Platform**: [e.g., Windows 11 / Ubuntu 22.04 / ESP-IDF v5.1]
- **Runtime / Language Version**: [e.g., Node v20.10, Python 3.11, Dart 3.4]
- **Hardware Revision**: [e.g., Rev B, Sensor connected via I2C at 0x76]
- **Active Branch / Commit**: [git commit hash or branch name]

---

## 3. Investigation Log & Hypotheses Tested

> [!IMPORTANT]
> Keep this log complete and unfiltered. Never delete failed attempts—they prevent future regression loops!

### Attempt 1: [Short Title of Hypothesis 1]
* **Hypothesis**: [We suspected race condition in component mount]
* **Action Taken**: [Added debounce and mutex lock in `src/controller.ts`]
* **Result**: [Error still reproduced; mutex caused deadlock on unmount]
* **Verdict**: `[FAILED]`
* **Lesson Learned**: [Issue is not concurrency-related; trigger happens before mount]

### Attempt 2: [Short Title of Hypothesis 2]
* **Hypothesis**: [Payload schema mismatch during deserialization]
* **Action Taken**: [Adjusted JSON parser types]
* **Result**: [Fixed deserialization, but underlying data was still null]
* **Verdict**: `[PARTIALLY WORKED]`

---

## 4. Root Cause Analysis
[Once identified, explain precisely what caused the flaw at the architectural, memory, logic, or hardware level.]

---

## 5. Final Verified Solution
- **Resolution Summary**: [How the bug was definitively resolved]
- **Files Modified**:
  - `[file1.ts](path/to/file1.ts)`
  - `[file2.ts](path/to/file2.ts)`
- **Key Code Diff**:
```diff
- problematicCode();
+ correctedCode();
```

---

## 6. Regression Testing & Prevention
- **Regression Test Path**: `tests/unit/bug_xxx_regression_test.ts`
- **Verification Command**:
```bash
npm test tests/unit/bug_xxx_regression_test.ts
```
- **Preventative Measures**: [Linters, static analysis rules, or hardware pull-ups added to prevent recurrence]
