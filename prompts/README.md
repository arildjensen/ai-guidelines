# Prompts

Reusable prompt assets in two forms: structured document templates and short drop-in snippets.

The distinction from skills and workflows: prompts are **text you give to the AI directly**, not instructions about how it should behave. A template gives the AI (or you) a document structure to fill in. A snippet gives the AI a specific instruction to follow for one aspect of a task.

---

## `templates/`

Structured documents with clearly marked fill-in sections. Use these when you need a consistent format for a recurring deliverable — PRDs, technical specs, architecture decision records, status updates, incident reports, and so on.

**How to use:**
> *"Use the technical-spec template to help me write a spec for [feature]."*

Or open the template yourself, fill in what you know, and ask the AI to complete or improve the rest.

| File | Description | Status |
|---|---|---|
| — | No templates yet | — |

---

## `snippets/`

Short prompt fragments — typically one to five lines — that you drop into a larger prompt to add a specific, consistent behavior.

**Examples of what snippets do:**
- *"Always end your response with a 'Risks and trade-offs' section."*
- *"Respond at the level of a senior engineer who is not familiar with this specific codebase."*
- *"If you make an assumption, flag it explicitly."*

Snippets are the smallest unit in this repo. They're valuable precisely because they're easy to forget to include and make a measurable difference when you do.

| File | Description | Status |
|---|---|---|
| — | No snippets yet | — |

---

## Adding a new prompt

See [CONTRIBUTING.md](../CONTRIBUTING.md) for conventions.

**Templates** should include instructions for use, clearly marked fill-in sections (e.g., `[PROJECT NAME]` or `{{ description }}`), and a completed example if the structure is non-obvious.

**Snippets** should include one sentence on when to use them, followed by the prompt text itself. Keep them short — if it's longer than a paragraph, it's probably a skill.

Checklist before committing:
- [ ] Frontmatter present with `title`, `category: template` or `category: snippet`, `compatible_with`, and `tags`
- [ ] Tested with at least one tool in `compatible_with`
- [ ] Row added to the appropriate index table above
