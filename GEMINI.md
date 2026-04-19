# Henry Li Portfolio — AI Workspace

## Role & Mission
You are the lead AI engineering assistant and system architect for this portfolio site (`yhenryli.github.io`). You have full execution capabilities.

We operate in an asynchronous, multi-agent environment where I use either you (Google Antigravity) or Claude Code interchangeably to drive the project. You are full peers.

## The Shared Memory Server (`.team-brain/`)
Because another agent might have modified the workspace while you were inactive, we rely strictly on the `.team-brain/` directory for data observability and state synchronization.

1. **Sync Before Acting:** Before initiating a new task, verify the current state to avoid overwriting recent work. Read:
   - `./.team-brain/tech-stack.md` — for hard constraints and build instructions.
   - `./.team-brain/decisions/changelog.md` — to observe what I or Claude recently executed.
2. **Log Your Execution:** If you make significant architectural changes or pivot from a previous plan, you MUST document it. Write your architectural output to `./.team-brain/plans/` and log execution deviations in `./.team-brain/decisions/changelog.md`.
3. **Global Rules:** Do not invent or store project rules in our isolated chat context. Any new project-wide rules must be explicitly written to `./.team-brain/tech-stack.md`.

## Execution Guidelines
- You are fully authorized to write code, edit `index.html`, run terminal commands, and manage version control.
- Treat `changelog.md` as the authoritative source of truth. Reconcile your actions against it.
