---
title: Troubleshooting
---

# Troubleshooting

## Failure-mode matrix

| Symptom | Likely cause | Fix | Prevention |
|---------|--------------|-----|------------|
| `gh repo create` fails with "name already exists" | Repo exists on GitHub | (a) Use existing remote: `git remote add origin <url>` then push, or (b) pick a new name | Run `gh repo view <owner>/<name>` before creation |
| Target folder contains `.git/` directory | Folder was already initialized as a repo | Refuse extraction; tell user it already looks like a repo | Check `ls -a skills/<name>` in preconditions |
| Scan returns >100 hits | Slug is too generic (e.g. `skill-test`) | Pause and ask user before continuing | Use more specific skill names during creation |
| `git rm --cached` succeeded but submodule add failed | Partial state: folder untracked but not re-added | Walk user through partial state manually; do not autorecover | Verify `gh auth status` and remote URL before destructive steps |
| Parent working tree is dirty | Uncommitted changes in parent repo | Name dirty files to user and ask whether to proceed | Check `git status` in preconditions |
| `gh auth status` fails | GitHub CLI not logged in | Run `gh auth login` | Verify auth before any `gh` operations |

## Partial state recovery

If extraction fails mid-way:

1. **Do not autorecover destructively.** Ask the user what they want to do.
2. Run `git status` in both the parent repo and the target folder.
3. Identify which steps completed and which did not.
4. Provide explicit commands to complete or roll back each completed step.
