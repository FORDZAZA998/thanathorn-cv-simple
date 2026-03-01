# Oracle Skills CLI Code Snippets (1145)

## 1. Agent Profile Mapping
From `src/profiles.ts` (concept):
```typescript
const AGENT_PROFILES = {
  antigravity: {
    projectPath: '.agent/skills/',
    globalPath: '~/.gemini/antigravity/skills/',
  },
  gemini: {
    projectPath: '.gemini/skills/',
    globalPath: '~/.gemini/skills/',
  }
};
```

## 2. Skill Markdown Structure
Example from `src/commands/learn.md`:
```markdown
---
name: learn
description: Explore a codebase with parallel Haiku agents
---
# /learn - Deep Dive Learning Pattern
...
```

## 3. Global Installation Command
```bash
~/.bun/bin/bunx --bun \
  oracle-skills@github:Soul-Brews-Studio/oracle-skills-cli#main \
  install -g -y
```

## 4. Environment Prerequisite Check
Used in `install.sh`:
```bash
which bun || curl -fsSL https://bun.sh/install | bash
which ghq || brew install ghq
```
