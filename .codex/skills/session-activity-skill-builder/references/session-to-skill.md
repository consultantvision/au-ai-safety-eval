# Session-To-Skill Extraction

Use this reference when Mycodex needs to convert useful session work into a reusable skill.

## Candidate Signals

Create or update a skill when session activity includes:

- A workflow likely to recur.
- A command sequence that must be executed in a careful order.
- A repo-specific convention future agents should follow.
- A troubleshooting pattern with clear symptoms, checks, fixes, and verification.
- A governance, security, or delivery rule that should survive context loss.

Do not create a skill for one-off facts, temporary state, or broad project documentation.

## Extraction Template

Capture:

- Trigger wording: what future user requests should activate the skill.
- Scope: what the skill is responsible for and what it must not do.
- Workflow: the smallest reliable sequence of steps.
- Safety gates: checks that must happen before writes, commits, pushes, sends, deletes, or live system changes.
- Verification: the command or evidence required before claiming completion.
- References: any repo files, schemas, APIs, or project notes needed only when relevant.

## Placement

Prefer repo-local skills at `.codex/skills/<skill-name>/` when the workflow is project-specific.

Use a global skill location only when the user explicitly wants the workflow available across repositories.
