# Lesson Learned: Passing Long Text to CLI on Windows PowerShell

**Date**: 2026-02-28
**Source**: rrr: thanathorn-cv-v2

## Context
Attempting to post a long, multiline markdown string as a GitHub comment using `gh issue comment --body`.

## Lesson
Directly passing long, multiline strings (even using PowerShell here-strings `@""@`) to external executables like `gh.exe` often fails with argument parsing errors (e.g., "accepts 1 arg(s), received 3"). The shell attempts to split the text based on newlines or quotes before passing it to the binary.

## Application
Always use the `--body-file` argument (or equivalent) when available for CLI tools on Windows if the payload is long or contains complex formatting.

```powershell
$body = @"
... long text ...
"@
$body | Out-File -Encoding UTF8 temp.txt
gh issue comment 123 --body-file temp.txt
Remove-Item temp.txt
```
