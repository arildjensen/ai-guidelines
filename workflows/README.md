# Workflows

Workflows define **what to do and in what order** for a multi-stage task. Where a skill says *how to think*, a workflow says *what steps to follow*.

A workflow has a clear trigger (when to use it), a sequence of steps, an expected output at each step, and a definition of done. If you find yourself doing the same multi-step process repeatedly with AI — and getting inconsistent results — that process belongs here.

---

## How to use a workflow

**Ask the AI to follow it explicitly:**
> *"Follow the feature-from-idea-to-spec workflow to help me plan this feature."*

**Use it as a conversation guide** — work through the steps one at a time across multiple messages, treating each step as a prompt.

**Combine with a skill** for higher-quality output at each step:
> *"Follow the feature-from-idea-to-spec workflow. Apply the spec-driven-development skill when writing the design and task breakdown."*

---

## Workflow index

### `development/`
Workflows for software planning, design, and delivery.

| File | Description | Status |
|---|---|---|
| [feature-from-idea-to-spec.md](./development/feature-from-idea-to-spec.md) | Takes a rough feature idea through requirements, design decisions, and a task breakdown | 🔧 Stub |

---

## Adding a new workflow

See [CONTRIBUTING.md](../CONTRIBUTING.md) for conventions. A workflow is ready to commit when it has:

- [ ] A clear trigger — one sentence on when to use it
- [ ] Numbered steps with an expected output for each
- [ ] A definition of done
- [ ] Frontmatter with `title`, `category: workflow`, `compatible_with`, and `tags`
- [ ] A row added to the index table above
