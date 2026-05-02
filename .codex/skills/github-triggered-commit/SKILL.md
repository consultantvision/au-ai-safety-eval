---
name: github-triggered-commit
description: Mycodex commit workflow for committing and pushing repository changes to GitHub only after an explicit user trigger. Use when the user says to run Mycodex, commit to GitHub, push to GitHub, publish a branch, run the Mycodex GitHub commit agent, use github-triggered-commit, or commit approved changes; includes diff review, staging discipline, validation, secret checks, remote selection, commit creation, and push behavior.
---

# Github Triggered Commit

## Overview

Use this skill when Mycodex needs to safely turn approved local work into a GitHub commit and push. It is intentionally trigger-gated: never commit or push just because implementation is complete.

## Workflow

1. Confirm the trigger is explicit. If the user intent is ambiguous, ask one concise confirmation question.
2. Run `git status --short` and inspect the diff for every file that may be staged.
3. Separate agent-made changes from unrelated or user-owned changes. Stage only the approved files.
4. Check for secrets, credentials, tokens, local environment files, generated binaries, and accidental large files.
5. Run relevant validation for the changed surface area. If no validation exists, state that clearly.
6. Confirm the branch and remote. Prefer `origin` unless the user explicitly names another target.
7. Commit with a concise message that describes the actual change.
8. Push to the configured branch, or use `git push -u origin <branch>` for a new branch.
9. Report the commit hash, branch, remote, validation result, and any files intentionally left unstaged.

## Guardrails

- Do not use `git reset --hard`, destructive cleanup, force push, or history rewrite unless the user explicitly requests it.
- Do not stage unrelated user changes.
- Do not commit secrets or local-only configuration.
- Do not push to `upstream` unless explicitly requested.
- Do not present a commit as complete unless the commit and push commands actually succeeded.

## Repository Notes

For this repository, `origin` is the normal working fork and `upstream` is Rodney Loo's source repository. Keep `main` aligned with `origin/main` unless the user explicitly asks for a different branch strategy.

Read `references/trigger-policy.md` when the trigger or target remote is unclear.
