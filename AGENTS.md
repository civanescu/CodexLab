# Repository instructions

## Implementation workflow

For implementation requests, inspect the relevant code, project guidance, and current Git state before editing. Check the available setup and verification commands; use the existing environment and run required setup when needed. Before the first patch, tell the user the findings that shape the implementation. After each code change, rerun the relevant verification commands and report the results. If verification fails, explain the failure and continue fixing and rechecking when appropriate.

## Record implementation work

When a user asks for a code, configuration, or feature change in this repository, update `docs/CHANGELOG.md` in the same task. Add a dated entry that explains what changed, why it changed, the affected files, and any verification performed (including verification that could not be completed). Keep entries concise and append newest work at the top. Do not add an entry for explanation-only questions or routine inspection that makes no repository changes.

Use the `change-docs` skill in `.agents/skills/change-docs/SKILL.md` for the detailed workflow. Treat this instruction as part of every implementation task, even when the skill is not explicitly invoked.
