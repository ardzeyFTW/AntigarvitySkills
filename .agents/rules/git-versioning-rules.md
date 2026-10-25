# Git Commit, Push & Versioning Rules

> [!IMPORTANT]
> This rule strictly governs all Git version control operations. It must be adhered to at all times without exception.

## 1. Explicit User Authorization Required
* **DO NOT** run `git commit`, `git push`, or create version tags autonomously.
* **ONLY** execute a commit or push when the user **explicitly and unambiguously requests it** (e.g., *"commit these changes"*, *"push to GitHub"*, *"please commit and push"*).
* Performing intermediate commits, automatic checkpoint commits, or unsolicited pushes is strictly forbidden.

## 2. Version Increment Protocol
When the user explicitly commands a commit or push:

1. **Check for Existing Version**:
   * Inspect the repository for a version identifier:
     - `VERSION` file
     - `package.json` (`"version": "x.y.z"`)
     - `pubspec.yaml` (`version: x.y.z+build`)
     - `pyproject.toml` / `setup.py` / `Cargo.toml`
     - Git tags (`git describe --tags --abbrev=0`)
2. **Increment Logic**:
   * **If and only if** a version number is defined, increment the **last variable** (the patch version / minor revision) unless the user explicitly gave a different version string.
   * **Example**:
     - `v1.0.3` $\rightarrow$ `v1.0.4`
     - `1.2.9` $\rightarrow$ `1.2.10`
     - `0.0.1` $\rightarrow$ `0.0.2`
   * **User Override**: If the user explicitly specifies the version (e.g., *"commit as v2.0.0"* or *"bump to 1.1.0"*), use the user's requested version string instead.
3. **Apply Version Update**:
   * Update the relevant version file(s) on disk.
   * Stage the updated version file along with the rest of the changes.

## 3. Commit & Push Execution Workflow
When authorized:
```bash
# 1. Verify what is modified
git status

# 2. Stage required files
git add <target-files>

# 3. Commit with semantic message and version tag
git commit -m "chore(release): vX.Y.Z - <summary of changes>"

# 4. Push only if push was explicitly requested
git push origin <branch>
```

## 4. Summary Table

| Action | User Prompted? | Version Exists? | Result |
| :--- | :--- | :--- | :--- |
| Any edit / test run | No | Any | **Do NOT commit or push** |
| "Commit changes" | Yes | Yes (e.g. `v1.0.3`) | Bump last number $\rightarrow$ `v1.0.4`, commit |
| "Commit as v2.0.0" | Yes | Any | Set version to `v2.0.0`, commit |
| "Commit changes" | Yes | No | Commit without version bump |
| "Push to origin" | Yes | Yes (e.g. `v1.0.4`) | Bump version if committing new work, push |
