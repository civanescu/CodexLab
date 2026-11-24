---
name: change-docs
description: Record repository code, configuration, and feature changes in docs/CHANGELOG.md. Use this whenever implementing or modifying this repository.
---

# Document repository changes

For every implementation task in this repository:

1. Inspect relevant source files, repository instructions, Git status, and available setup and verification commands before editing.
2. Tell the user the findings that will guide the implementation before the first patch.
3. Apply the requested changes. After each code change, rerun the relevant verification commands and report the result. If a check fails, explain the failure and continue fixing and rechecking when appropriate.
4. Update `docs/CHANGELOG.md` before finishing. Add a dated entry at the top under the changelog heading. Describe what changed and why, list the important affected files, and summarize verification performed. If verification was not run or failed, say so accurately.
5. Keep existing entries intact. Do not rewrite old entries to make them appear more complete.

Do not create an entry for explanation-only questions or inspection that makes no repository changes. If the requested work itself is documentation-only, record it when it changes project guidance or user-facing project documentation.
