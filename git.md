# Git Cheat Sheet

## 1. Workflow (Daily Use)

- `git status` — check which files have been modified
- `git add .` — stage all changes for commit
- `git add <file>` — stage a specific file only
- `git commit -m "message"` — save changes to local history
- `git commit --amend -m "new message"` — edit the last commit message (before pushing)
- `git commit -am "message"` — stage all tracked files and commit in one step

---

## 2. Syncing with Remote (GitHub)

- `git push` — upload local commits to the cloud
- `git push -u origin branch-name` — push a new branch and set upstream tracking
- `git push --force-with-lease` — force push safely (checks no one else pushed first)
- `git pull` — fetch and merge changes from the cloud
- `git pull --rebase` — fetch and rebase instead of merge (cleaner history)
- `git fetch` — download changes without merging them yet
- `git remote -v` — show remote repository URLs
- `git remote add origin <url>` — connect a local repo to a remote for the first time

---

## 3. Branching & Experimenting

- `git branch` — list all local branches
- `git branch -a` — list all branches including remote ones
- `git branch -d branch-name` — delete a branch (safe — only if merged)
- `git branch -D branch-name` — force delete a branch (even if not merged)
- `git checkout -b branch-name` — create and switch to a new branch
- `git checkout main` — switch back to the main branch
- `git switch branch-name` — modern way to switch branches (Git 2.23+)
- `git switch -c branch-name` — modern way to create and switch to a new branch
- `git merge branch-name` — combine changes from another branch into the current one
- `git rebase main` — replay your commits on top of main (cleaner than merge)
- `git stash` — temporarily save uncommitted changes without committing
- `git stash pop` — restore the last stashed changes
- `git stash list` — see all saved stashes
- `git stash drop` — delete the last stash without applying it

---

## 4. Undoing & Fixing Mistakes

- `git reset --hard` — discard all local changes and revert to last commit
- `git reset --soft HEAD~1` — undo last commit but keep changes staged
- `git reset --mixed HEAD~1` — undo last commit and unstage changes (keep files)
- `git restore <file>` — discard changes in a specific file (not yet staged)
- `git restore --staged <file>` — unstage a file (keep the changes)
- `git revert <commit-hash>` — create a new commit that undoes a previous one (safe for shared branches)
- `git clean -fd` — remove untracked files and directories

---

## 5. Inspection & History

- `git log` — full commit history
- `git log --oneline` — condensed list of previous commits
- `git log --oneline --graph --all` — visual branch history in terminal
- `git log --author="Ruben"` — filter commits by author
- `git diff` — show changes not yet staged
- `git diff --staged` — show changes that are staged but not yet committed
- `git diff main..branch-name` — compare two branches
- `git show <commit-hash>` — show details of a specific commit
- `git blame <file>` — show who changed each line of a file and when

---

## 6. Tags & Releases

- `git tag` — list all tags
- `git tag v1.0.0` — create a lightweight tag at the current commit
- `git tag -a v1.0.0 -m "Release v1.0.0"` — create an annotated tag with a message
- `git push origin v1.0.0` — push a specific tag to remote
- `git push origin --tags` — push all tags to remote

---

## 7. Configuration & Setup

- `git init` — initialise a new local repository
- `git clone <url>` — clone a remote repository locally
- `git config --global user.name "Your Name"` — set your name
- `git config --global user.email "you@email.com"` — set your email
- `git config --list` — show all current Git config settings
- `git config --global core.editor "code --wait"` — set VS Code as default editor

---

## 8. .gitignore Tips

```bash
# Ignore a file
secret.env

# Ignore a folder
node_modules/
__pycache__/

# Ignore all files with an extension
*.log
*.pyc

# Ignore everything except specific files
!important.log
```

- `git rm --cached <file>` — stop tracking a file that was already committed (add it to .gitignore first)

---

## 9. Useful Shortcuts

| Task | Command |
|---|---|
| Undo last commit (keep changes) | `git reset --soft HEAD~1` |
| Discard all local changes | `git reset --hard` |
| Save work in progress | `git stash` |
| See visual branch history | `git log --oneline --graph --all` |
| Compare with main branch | `git diff main` |
| Push new branch to GitHub | `git push -u origin branch-name` |
| Delete remote branch | `git push origin --delete branch-name` |
| Copy a commit from another branch | `git cherry-pick <commit-hash>` |

---

## 10. Common Workflows

### Feature branch workflow
```bash
git checkout main
git pull
git checkout -b feature/my-feature
# make changes
git add .
git commit -m "add my feature"
git push -u origin feature/my-feature
# open pull request on GitHub
```

### Fix a mistake on the last commit
```bash
# Fix the files, then:
git add .
git commit --amend -m "corrected commit message"
```

### Sync a forked repo
```bash
git remote add upstream <original-repo-url>
git fetch upstream
git merge upstream/main
```
