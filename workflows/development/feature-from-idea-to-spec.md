---
title: Feature from Idea to Spec
category: workflow
compatible_with: [claude, kiro, cursor, generic]
tags: [development, planning, specs, features]
status: stub
---

# Feature from Idea to Spec

> **Status: stub.** Fill this in as your process becomes clear.

## When to use this

When you have a rough idea for a feature and need to turn it into something concrete enough to build — with requirements, a design, and a task list.

## Trigger

> *"I have an idea for [X]. Help me work through it using the feature-from-idea-to-spec workflow."*

---

## Steps

### Step 1: Idea capture
*Goal: Get the idea out of your head without filtering.*

- What is the feature?
- Who is it for?
- What problem does it solve?
- What does success look like?

**Output:** A short problem statement (2–4 sentences).

---

### Step 2: Requirements
*Goal: Define what the feature must do. Not how — what.*

- Functional requirements (what it does)
- Non-functional requirements (performance, security, scale)
- Out of scope (explicit list of what this does NOT include)

**Output:** A numbered requirements list.

---

### Step 3: Design
*Goal: Decide how it will work at a high level.*

- Key technical decisions
- Trade-offs considered and chosen path
- Risks and open questions

**Output:** A short design doc or ADR (Architecture Decision Record).

---

### Step 4: Task breakdown
*Goal: Turn the design into discrete, buildable units of work.*

- Each task should be completable in a single session
- Tasks should be ordered by dependency
- Each task should have a clear definition of done

**Output:** An ordered task list.

---

## Definition of done

The workflow is complete when:
- [ ] Problem statement written
- [ ] Requirements listed and reviewed
- [ ] Key design decisions documented
- [ ] Task list created and ordered
- [ ] No open blocking questions remain
