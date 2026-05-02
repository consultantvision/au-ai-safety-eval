---
name: session-activity-skill-builder
description: Mycodex workflow for creating or updating Codex skills from useful session activities, repeated workflows, troubleshooting patterns, repo conventions, and automation guardrails. Use when the user asks Mycodex to create skills based on session activities, capture what was learned as a reusable skill, turn a workflow into a Codex skill, or make future agents repeat a process consistently.
---

# Session Activity Skill Builder

## Overview

Use this skill when Mycodex needs to convert high-value session work into concise, reusable Codex skills. Prefer repo-local skills for project-specific workflows and global skills only when the user explicitly wants cross-repository reuse.

## Workflow

1. Identify the recurring workflow, decision rule, safety check, or troubleshooting pattern from the session.
2. Decide whether it belongs in an existing skill or a new skill.
3. Name new skills with lowercase letters, digits, and hyphens only.
4. Place project-specific skills under `.codex/skills/<skill-name>/`.
5. Write a compact `SKILL.md` with frontmatter containing only `name` and `description`.
6. Put trigger conditions in the description because that is what future Codex sessions see before loading the skill body.
7. Add references only when details are useful but not always needed.
8. Validate the skill folder with the skill validator when available.

## What To Capture

- Trigger wording that should activate the skill.
- Scope boundaries and non-goals.
- Ordered workflow steps.
- Safety gates before write, commit, push, send, delete, or live-system changes.
- Verification commands or evidence.
- Project-specific facts that are stable enough to preserve.

## What To Avoid

- Do not capture temporary shell state, one-off command output, or facts likely to drift quickly.
- Do not create broad documentation disguised as a skill.
- Do not duplicate the same guidance across multiple skills.
- Do not store secrets, private credentials, or sensitive project data in skills.

Read `references/session-to-skill.md` when deciding whether a session activity deserves a new skill.
