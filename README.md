# ai-guidelines

A personal collection of skills, workflows, prompts, and context files for working effectively with AI tools like Claude, Kiro, and Cursor.

## What's in here

| Folder | Purpose |
|---|---|
| [`skills/`](./skills/) | Teach AI tools *how to think* about a domain |
| [`workflows/`](./workflows/) | Step-by-step processes for multi-stage tasks |
| [`prompts/`](./prompts/) | Reusable templates and prompt fragments |
| [`context/`](./context/) | Persistent facts and preferences to include in system prompts |

## How to use these files

### With Claude (claude.ai Projects)
Add files as project knowledge, or paste the contents into a system prompt. Reference a skill by name in your message: *"Using the executive-communication skill, help me draft this email."*

### With Kiro
Place relevant files in your `.kiro/` directory or reference them in your steering docs.

### With Cursor / Windsurf / Copilot
Add file contents to your `.cursorrules` file or include them as context in your prompt.

### General pattern
Most files are tool-agnostic. Each file's frontmatter includes a `compatible_with` field listing tools it has been tested with.

## File frontmatter

Every skill, workflow, and prompt file includes a YAML frontmatter block:

```yaml
---
title: Human-readable title
category: skill | workflow | template | snippet
compatible_with: [claude, kiro, cursor, generic]
tags: [relevant, tags, here]
---
```

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for conventions on adding new files.
