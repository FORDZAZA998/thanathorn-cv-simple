# Oracle Skills CLI Architecture Overview (1145)

## System Abstract
The `oracle-skills-cli` is a cross-agent skill management engine built with **Bun** and **TypeScript**. Its primary purpose is to standardize the installation and management of "Oracle Skills" across multiple AI coding environments (Claude Code, Gemini CLI, Antigravity, etc.).

## Directory Structure
- `src/`: Core source code.
  - `cli/`: Entry point and command-line interface logic using `commander`.
  - `commands/`: Markdown-based skill definitions and installation logic.
  - `skills/`: Implementation of core skill logic (e.g., learn, trace).
  - `profiles.ts`: Management of agent profiles and their respective paths.
- `scripts/`: Build and maintenance utilities.
- `docs/`: Supplemental documentation.

## Core Abstractions
1. **Agent Profiles**: Standardized mapping of AI agents (e.g., Antigravity → `.agent/skills/`) to their respective filesystem paths.
2. **Skill Definitions**: Skills are defined as markdown files with YAML frontmatter, allowing them to be parsed and installed into agent directories.
3. **Universal Installer**: A `curl | bash` entry point that handles prerequisite checks (Bun, GHQ) and global installation.

## Key Technologies
- **Bun**: Runtime, bundler, and package manager.
- **Commander.js**: CLI framework for handling subcommands.
- **Clack Prompts**: Interactive UI for terminal prompts.
- **MQTT**: Used for real-time features (e.g., gemini skill).
