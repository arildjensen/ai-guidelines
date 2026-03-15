# Contributing

## File conventions

### Naming
- Use lowercase kebab-case: `executive-communication.md`, `feature-from-idea-to-spec.md`
- Be specific enough that the filename is self-explanatory without reading the file

### Frontmatter
Every file must start with a YAML frontmatter block:

```yaml
---
title: Short human-readable title
category: skill | workflow | template | snippet
compatible_with: [claude, kiro, cursor, generic]
tags: [tag1, tag2]
---
```

- `category`: Pick the one that best fits (see definitions below)
- `compatible_with`: Only list tools you have actually tested with; use `generic` if it's plain markdown with no tool-specific syntax
- `tags`: Lowercase, descriptive, reuse existing tags where possible

### Categories

| Category | Definition |
|---|---|
| `skill` | Teaches the AI how to think or behave in a domain. Behavioral instructions, frameworks, principles. |
| `workflow` | A sequence of steps for a multi-stage task. Has a clear start and end state. |
| `template` | A structured document with fill-in sections. Meant to be populated, not followed. |
| `snippet` | A short, reusable prompt fragment. Typically a few lines, dropped into a larger prompt. |

### Structure within a file

**Skills** should include:
- A short statement of purpose (1–2 sentences)
- The core framework or principles
- A checklist or quick reference if applicable
- Examples where helpful

**Workflows** should include:
- A clear trigger (when to use this workflow)
- Numbered steps
- Expected output at each step
- A definition of "done"

**Templates** should include:
- Instructions for use at the top
- Clearly marked fill-in sections (e.g., `[PROJECT NAME]`, `{{ description }}`)
- A completed example if the template is complex

**Snippets** should include:
- One sentence explaining when to use it
- The prompt text itself

## Where files go

```
skills/
  communication/   # writing, messaging, presenting
  development/     # coding, architecture, specs
  writing/         # general writing and editing

workflows/
  development/     # software development processes

prompts/
  templates/       # fill-in structured documents
  snippets/        # short reusable fragments

context/           # facts about you or your environment
```

If a new domain doesn't fit existing folders, add a new subfolder and note it in the relevant README.

## Quality bar

Before committing a file, check:
- [ ] Frontmatter is present and complete
- [ ] The file is useful without additional explanation
- [ ] Jargon is either avoided or defined
- [ ] It has been tested with at least one tool listed in `compatible_with`
