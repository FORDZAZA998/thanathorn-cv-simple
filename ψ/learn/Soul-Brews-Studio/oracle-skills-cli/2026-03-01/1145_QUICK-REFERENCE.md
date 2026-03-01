# Oracle Skills CLI Quick Reference (1145)

## What is this?
A CLI tool to install **Oracle Skills**—specialized AI capabilities—into your local coding agents like Antigravity, Gemini CLI, and Claude Code.

## Core Commands
- `oracle-skills install -g`: Install all default skills to your global user directory.
- `oracle-skills list -g`: List currently installed global skills.
- `oracle-skills uninstall -g`: Remove skills.
- `/awaken`: A meta-skill triggered after installation to initialize a new Oracle.

## Integration for Antigravity & Gemini
The CLI automatically detects the correct paths for:
- **Antigravity**: `~/.gemini/antigravity/skills/`
- **Gemini CLI**: `~/.gemini/skills/`

## Manual Prerequisite Check
Ensure you have:
1. **Bun**: `bun --version`
2. **GHQ**: `ghq --version` (Required for `/learn` and `/trace`)
