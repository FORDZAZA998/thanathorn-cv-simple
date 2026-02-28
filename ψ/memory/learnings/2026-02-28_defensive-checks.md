# Lesson Learned: Defensive Dependency Checks and Git Boundaries

**Date**: 2026-02-28
**Source**: rrr: thanathorn-cv-v2

## Context
During the `/awaken` and `/rrr` workflows on a fresh Windows workspace.

## Lesson
1. On Windows, assume bash-centric dependencies (`bun`, `ghq`) are missing. Use PowerShell (`irm ... | iex`) or `winget` as robust alternatives to `curl | bash`.
2. In new repositories, commands like `git diff HEAD~5` will crash if the commit history is shorter than the boundary. Always check git history length or use safe fallbacks.

## Application
- Pre-flight checks for tools must use OS-aware fallback installers.
- Retro scripts should wrap git commands in try/catch or conditional length checks.
