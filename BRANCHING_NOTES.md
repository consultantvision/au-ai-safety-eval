# Branching Notes

This repository is configured with two GitHub remotes:

- `origin`: `https://github.com/Consultantvision/au-ai-safety-eval.git`
- `upstream`: `https://github.com/rodneyloo/au-ai-safety-eval.git`

Local `main` tracks `origin/main`, which is the Consultantvision repository.
Keep `main` aligned with `origin` unless intentionally changing the repo's
primary publishing target.

## Create A Future Branch From Rodney Loo's Repo

When you are ready to prepare work based on Rodney Loo's repository, start from
the latest `upstream/main`:

```powershell
git fetch upstream
git switch -c rodneyloo-sync upstream/main
```

Alternative clearer branch name:

```powershell
git fetch upstream
git switch -c rodneyloo/contribution upstream/main
```

## Commit And Push The Branch

After making changes:

```powershell
git status
git add .
git commit -m "Your commit message"
git push -u origin rodneyloo-sync
```

If you used the alternative branch name:

```powershell
git push -u origin rodneyloo/contribution
```

This keeps the branch based on `rodneyloo/upstream` work, but publishes your
branch to the Consultantvision repository. From there, open a pull request from
`Consultantvision:<branch-name>` into `rodneyloo:main` when ready.
