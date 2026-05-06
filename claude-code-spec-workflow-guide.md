# Claude Code: Spec-Driven Development Workflow Guide

A practical guide to installing Claude Code, setting up a GitHub project, and implementing a spec-driven development workflow for maximum productivity.

---

## 1. Installing Claude Code

The native installer is the recommended path (npm install is deprecated). No Node.js is required.

**macOS (Homebrew):**

```bash
brew install claude-code
```

**macOS / Linux (native installer):**

```bash
curl -fsSL https://claude.ai/install.sh | sh
```

**Windows (PowerShell):**

```powershell
irm https://claude.ai/install.ps1 | iex
```

**Prerequisites:**

- A Claude Pro ($20/mo), Max ($100/mo), or an Anthropic API key
- macOS, Linux, or Windows 10+
- An existing Pro subscription covers Claude Code access

After installing, open a terminal, navigate to any project directory, and run `claude`. It will open a browser to authenticate on first launch.

---

## 2. Setting Up Your GitHub Project

Create your repo and initialize the key structure:

```bash
mkdir my-project && cd my-project
git init
gh repo create my-project --private --source=. --push
```

Then bootstrap Claude Code's configuration:

```bash
claude
# Inside Claude Code:
/init
```

The `/init` command scans your project and generates a starter `CLAUDE.md`. This is the single most important file — Claude reads it at the start of every session.

### Writing an Effective CLAUDE.md

Aim for 50–100 lines. For each line, ask: "Would removing this cause Claude to make a mistake?" If not, cut it.

```markdown
# CLAUDE.md

## Project
[Company] — [One-line description of what this project does]

## Tech Stack
- [e.g., Python 3.12, FastAPI, PostgreSQL]
- [e.g., React 18, TypeScript, Tailwind]

## Commands
- `make dev` — Start dev server
- `make test` — Run test suite
- `make lint` — Lint and format

## Conventions
- [Coding standards and naming conventions]
- [Commit message format]
- [File organization rules]

## Architecture
- [Brief description of modules/layers]
```

Commit `CLAUDE.md` to version control so the whole team benefits. In monorepos or multi-package projects, add a `CLAUDE.md` in each subdirectory — Claude loads them hierarchically.

---

## 3. Spec-Driven Development Workflow

The core loop is: **Research → Spec → Plan → Implement → Verify**.

### Step A: Create a `/specs` Directory

```
project-root/
├── CLAUDE.md
├── specs/
│   ├── steering/
│   │   ├── product.md        # Product vision, personas, KPIs
│   │   ├── tech.md           # Tech stack decisions, constraints
│   │   └── structure.md      # Project architecture
│   ├── features/
│   │   └── user-auth-spec.md # Individual feature specs
│   └── tasks/
│       └── TASKS.md          # Decomposed, testable tasks
└── src/
```

**Steering docs come first.** Before any feature work, establish your product vision, technology decisions, and architecture in the `specs/steering/` directory. These documents anchor every downstream decision.

### Step B: Write a Feature Spec

Before writing any code, write (or have Claude help you write) a spec. A good spec includes:

```markdown
# Feature: User Authentication

## Requirements
- Users can register with email/password
- Users can log in and receive a JWT
- Passwords hashed with bcrypt, min 12 chars

## Acceptance Criteria
- POST /api/auth/register returns 201 with user object
- POST /api/auth/login returns 200 with JWT token
- Invalid credentials return 401

## Design Decisions
- JWT expires after 24 hours
- Refresh tokens stored in httpOnly cookies

## Files Affected
- src/api/auth/routes.py
- src/api/auth/models.py
- src/api/auth/tests/
```

Every requirement should be testable. Every acceptance criterion should be specific and verifiable.

### Step C: Use Plan Mode, Then Implement

In Claude Code, use **Shift+Tab** to toggle Plan Mode. Give it the spec:

```
Read specs/features/user-auth-spec.md and create an implementation plan.
Do not write code yet — just outline the approach and which files
you'll create or modify.
```

Review the plan. Push back if needed ("No, use X instead" or "I don't like this approach because Y"). Once you approve:

```
Implement @specs/features/user-auth-spec.md
Use the task tool and each task should only be done by a subagent
so that context is clear. After each task, do a commit before you continue.
You are the main agent and your subagents are your devs.
```

This orchestration pattern keeps each task in a clean context window and creates atomic commits — much easier to review and revert.

### Step D: Verify Against the Spec

```
Run the test suite and verify all acceptance criteria
from specs/features/user-auth-spec.md are met.
```

Always close the loop by validating implementation against the original spec.

---

## 4. Custom Slash Commands

Create reusable prompts at `.claude/commands/` in your project:

### Spec Review Command

```markdown
# .claude/commands/spec-review.md
Review the spec at $ARGUMENTS for completeness:
- Are all requirements testable?
- Are edge cases covered?
- Are files affected listed?
- Are acceptance criteria specific enough?
Flag any gaps and suggest improvements.
```

Usage: `/spec-review specs/features/user-auth-spec.md`

### Implementation Command

```markdown
# .claude/commands/implement-spec.md
Implement the spec at $ARGUMENTS using the following workflow:
1. Read the spec thoroughly
2. Create an implementation plan
3. Use the task tool — each task handled by a subagent
4. Commit after each completed task
5. Run tests after all tasks complete
6. Report which acceptance criteria pass/fail
```

Usage: `/implement-spec specs/features/user-auth-spec.md`

---

## 5. Hooks for Automation

Configure hooks in `.claude/settings.json` to automate repetitive tasks:

```json
{
  "hooks": {
    "postToolUse": [
      {
        "matcher": "edit_file|write_file",
        "type": "command",
        "command": "prettier --write $FILE_PATH"
      }
    ],
    "preToolUse": [
      {
        "matcher": "bash",
        "type": "command",
        "command": "echo 'Running: $TOOL_INPUT'"
      }
    ]
  }
}
```

Common hook patterns include auto-formatting files after edits, blocking dangerous commands, and logging tool usage.

---

## 6. Context Management

Long sessions degrade quality. Follow these practices:

- **Never exceed ~60% context.** Split work into phases: Research → Plan → Implement → Validate. Clear context between each.
- **Use `/compact`** to free up context when sessions run long.
- **Use `/clear`** to reset the conversation while keeping `CLAUDE.md` context.
- **Write progress to disk.** Midway through a complex task, ask Claude to write a `progress.md` summarizing what's done and what remains. Start a fresh session that reads it.
- **Subagents get their own context.** When Claude spawns a subagent for a focused task, it prevents bloating your main session.
- **Keep `CLAUDE.md` concise.** It loads into every session — link to external docs for detail rather than inlining everything.

---

## 7. Workflow Summary

| Phase | Action | Tool |
|-------|--------|------|
| **Steer** | Write `product.md`, `tech.md`, `structure.md` | Editor / Claude |
| **Spec** | Write feature spec with requirements + acceptance criteria | Editor / Claude |
| **Review** | `/spec-review specs/features/my-feature.md` | Claude Code |
| **Plan** | Shift+Tab → Plan Mode → review approach | Claude Code |
| **Implement** | Subagent orchestration with atomic commits | Claude Code |
| **Verify** | Run tests mapped to acceptance criteria | Claude Code |
| **Commit** | Review diff, merge PR | Git / GitHub |

---

## 8. Community Plugins & Resources

- **Official docs:** [code.claude.com/docs/en/common-workflows](https://code.claude.com/docs/en/common-workflows) — Explore → Plan → Implement → Commit pattern
- **shinpr/claude-code-workflows** (GitHub) — Plugin-based workflow system; install with `/plugin marketplace add shinpr/claude-code-workflows`
- **Pimzino/claude-code-spec-workflow** (GitHub) — Spec-driven development templates with built-in validation agents

---

## 9. Quick Reference: Essential Claude Code Commands

| Command | Description |
|---------|-------------|
| `claude` | Start an interactive session |
| `/init` | Generate a starter `CLAUDE.md` from your project |
| `/compact` | Free up context in a long session |
| `/clear` | Reset conversation, keep `CLAUDE.md` |
| `/cost` | Check token usage and cost |
| `/plan` | Enter plan mode (also Shift+Tab) |
| `/bug` | Report an issue to Anthropic |
| `Ctrl+C` | Cancel current response |
| `Alt+T` | Toggle extended thinking |

---

*Guide compiled May 2026. For the most current Claude Code information, see [code.claude.com](https://code.claude.com).*
