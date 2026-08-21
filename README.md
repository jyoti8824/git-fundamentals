# Git Fundamentals — Practice Repository

A hands-on sandbox for building a solid, first-principles understanding of Git — how branches, merges, rebase, cherry-pick, stash, and history-debugging tools actually work under the hood, not just the commands to run.

## Why this repo exists

Most Git tutorials teach commands. This repo was built to understand the **mental model** behind them — what a branch actually is, what moves when you commit, why rebased commits get new hashes, and how tools like `bisect` let you investigate a regression instead of guessing.

Each commit on `master` represents a deliberate step in that exploration — creating divergence, merging it back, and later re-creating similar scenarios on separate branches (`feature-login`, `feature-payment`) to practice fast-forward merges, three-way merges, and cherry-picking a fix across branches.

## What's covered

- **Branches & HEAD** — a branch is just a movable pointer to a commit; `HEAD` tracks which one you're on.
- **Fast-forward vs. three-way merges** — when Git can simply move a pointer, and when it must create a merge commit.
- **Merge conflicts** — resolving competing changes and completing the merge.
- **Rebase** — replaying commits onto a new base, and why that changes commit identity (`D ≠ D'`).
- **Cherry-pick** — pulling a single commit (e.g. a hotfix) across branches without merging the whole thing.
- **Stash** — parking incomplete work to switch context safely.
- **Debugging with Git** — using `log`, `show`, `diff`, and `bisect` to investigate *when* and *why* something broke, including binary-searching history with `git bisect`.

## Repo structure

```
.
├── app.txt      # scratch file used to generate real commits, branches, and merges
└── README.md
```

`app.txt` isn't a project deliverable — it's the object being modified across commits so that branching, merging, and rebasing operations have real content to act on.

## Branches

| Branch | Purpose |
|---|---|
| `master` | main line of practice commits |
| `feature-login` | practicing branch creation and fast-forward merges |
| `feature-payment` | practicing diverging history, three-way merges, and cherry-picking |

## Reference — commands practiced

```
git branch <name>                              # create a branch
git switch <name>                               # switch branches
git switch -c <name>                             # create + switch
git log --oneline --graph --decorate --all       # visualize history
git merge <branch>                                # merge a branch
git rebase <branch>                               # rebase onto a branch
git cherry-pick <commit>                          # apply one commit
git stash / git stash list / apply / pop          # shelve work in progress
git show <commit>                                 # inspect a commit
git diff <A> <B>                                  # compare commits/branches
git bisect start / good / bad / reset / run        # binary-search for a bad commit
```

## Notes

This is a learning repo, not production code — the value is in the Git history itself (visible via `git log --oneline --graph --decorate --all`), which documents the branching and merging scenarios practiced here.
