# Skills

Skills teach AI tools **how to think** about a domain. Each skill file contains a framework, principles, and behavioral guidance that shapes how the AI approaches any task in that area.

A skill is not a step-by-step process (that's a [workflow](../workflows/)) and it's not a fill-in document (that's a [template](../prompts/templates/)). It's a lens — a way of thinking the AI applies to whatever you ask it to do.

---

## How to use a skill

**Reference it by name in your prompt:**
> *"Using the executive-communication skill, help me draft this status update."*

**Include it in a system prompt or project context** so it applies automatically for an entire session:
> *Paste the file contents into a Claude Project's knowledge base, a Kiro steering doc, or a `.cursorrules` file.*

**Chain it with a workflow:**
> *"Follow the feature-from-idea-to-spec workflow, applying the spec-driven-development skill throughout."*

---

## Skill index

### `communication/`
Skills for written and verbal communication.

| File | Description | Status |
|---|---|---|
| [executive-communication.md](./communication/executive-communication.md) | Four C's framework for communicating clearly to senior leaders — via email, docs, presentations, or conversation | ✅ Complete |

### `development/`
Skills for software design, architecture, and engineering process.

| File | Description | Status |
|---|---|---|
| [spec-driven-development.md](./development/spec-driven-development.md) | Principles and process for writing specs before writing code | 🔧 Stub |

### `writing/`
Skills for general writing, editing, and content quality.

| File | Description | Status |
|---|---|---|
| — | No skills yet | — |

---

## Adding a new skill

See [CONTRIBUTING.md](../CONTRIBUTING.md) for naming conventions, required frontmatter, and the quality bar a skill should meet before being committed.

Quick checklist:
- [ ] File is in the right subfolder (add one if the domain doesn't exist yet)
- [ ] Frontmatter is present with `title`, `category: skill`, `compatible_with`, and `tags`
- [ ] The skill has been tested with at least one tool in `compatible_with`
- [ ] A row has been added to the index table above
