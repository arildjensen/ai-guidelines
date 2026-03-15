# Context

Persistent facts about you or your environment. Include these files in system prompts so AI tools start every session with stable background knowledge — your role, your preferences, your stack, your conventions — without you having to re-explain them each time.

Context files are not instructions for how the AI should behave (that's a [skill](../skills/)). They're facts the AI should *know* so it can calibrate its responses appropriately.

---

## How to use

**Claude Projects:** Add as project knowledge. Every conversation in the project will have access to it automatically.

**Kiro:** Reference in your steering docs or project context.

**Cursor / Windsurf:** Paste into `.cursorrules` or include in your system prompt.

**One-off sessions:** Paste the relevant file at the start of a conversation.

---

## Context index

| File | Description | Status |
|---|---|---|
| [principles.md](./principles.md) | Personal engineering and communication principles, working style, tech stack | 🔧 Stub — fill this in |

---

## What belongs in context

- Your role and the kind of decisions you typically make
- Your preferred communication style (direct, detailed, etc.)
- Your tech stack and environment — so the AI doesn't suggest tools you don't use
- Your team's conventions and vocabulary
- Things AI tools consistently get wrong about you or your work
- Standing preferences (e.g., "always include trade-offs," "prefer TypeScript over JavaScript")

## What does NOT belong in context

- **Secrets, API keys, or credentials** — never
- **Step-by-step processes** — put those in [workflows](../workflows/)
- **Domain expertise or frameworks** — put those in [skills](../skills/)
- **Information that changes frequently** — context files should be stable; update them when your situation changes, not per-project

---

## Adding a new context file

Context files don't require the same frontmatter as skills and workflows, but should include at minimum:

```yaml
---
title: Descriptive title
category: context
---
```

Add a row to the index table above when you add a file.
