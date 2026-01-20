# Git Commands Reference

This file contains essential basic to intermediate Git commands, ideal for learning, practicing, and interview preparation.


### Basic Commands

| Command                        | What It Does                                                     |
| ----------------------------- | ------------------------------------------------------------------|
| `git init`                    | Initialize a new Git repository                                   |
| `git clone <repo-url>`        | Clone a remote repository to local                                |
| `git status`                  | Show changes (staged/unstaged/untracked)                          |
| `git add <file>`              | Stage a specific file for commit                                  |
| `git add .`                   | Stage all changed files                                           |
| `git commit -m "message"`     | Save changes with a message                                       |
| `git help`                    | Show Git help manual                                              |
| `git log`                     | Show commit history                                               |
| `git log --oneline --graph`   | Compact graphical log (great for quick view)                      |
| `git diff`                    | See differences between changes not yet staged (not stagged)      |


> ⚠️ **Warning:** Avoid committing sensitive info (e.g., `.env`, secrets) — use [`.gitignore`](../automation-snippets/git/gitignore-guide.md).

---

### Branching & Merging

| Command                                  | What It Does                                               |
| ---------------------------------------- | -----------------------------------------------------------|
| `git branch`                             | List all local branches                                    |
| `git branch <name>`                      | Create a new branch                                        |
| `git checkout <name>`                    | Switch to a branch                                         |
| `git checkout -b <name>`                 | Create and switch to new branch                            |
| `git switch -c <name>`                   | Modern alternative to checkout                             |
| `git merge <branch>`                     | Merge given branch into current branch                     |
| `git merge --no-ff <branch>`             | Forces a merge commit, useful for clear history in teams.  |
| `git branch -d <name>`                   | Delete a branch (only if merged)                           |
| `git branch -D <name>`                   | Force delete branch (even if not merged)                   |
| `git rebase <branch>`                    | Reapply commits from current branch onto target branch     |
| `git cherry-pick <commit>`               | Apply a specific commit from another branch                |
| `git commit --no-edit`                   | Skip commit message during rebase or merge.                |


---

### Remote Repositories

| Command                                     | What It Does                                         |
| ------------------------------------------- | -----------------------------------------------------|
| `git remote add origin <url>`               | Connect local repo to a remote URL                   |
| `git remote -v`                             | Show current remote URLs                             |
| `git push origin <branch>`                  | Push branch to remote                                |
| `git push --set-upstream origin <branch>`   | Set upstream (link local to remote branch)           |
| `git pull`                                  | Pull latest changes and merge                        |
| `git fetch`                                 | Fetch updates without merging                        |
| `git fetch --all`                           | Fetch all branches and updates                       |
| `git push origin --delete <branch>`         | To delete remote branch                              |
| `git remote prune origin`                   | Cleanup stale branches                               |


> ⚠️ **Warning:** Don't force push (`--force`) unless you're 100% sure — it rewrites remote history.

---

### Undo & Cleanup

| Command                             | What It Does                                                 |
| ----------------------------------- | -------------------------------------------------------------|
| `git reset <file>`                  | Unstage a staged file                                        |
| `git restore --staged <file>`       | Also unstages                                                |
| `git reset HEAD^`                   | Useful to undo a wrong commit                                |
| `git reset --soft HEAD~1`           | Undo last commit, keep changes staged                        |
| `git reset --mixed HEAD~1`          | Undo last commit, unstage changes                            |
| `git reset --hard HEAD~1`           | Completely undo last commit and discard changes              |
| `git revert <commit>`               | Create a new commit to reverse a specific commit (non-destructive) |
| `git revert -m 1 <merge-commit-sha>`| Use this when you want to undo a merge without rewriting history.  |
| `git clean -fd`                     | Delete untracked files and folders                           |
| `git checkout -- <file>`            | Discard local changes to a file                              |
| `git restore <file>`                | (Newer syntax) Restore file to last commit state             |


> ⚠️ **Warning:** `git reset --hard` is **dangerous**. Always warn that it discards local changes **permanently**.

---

### Stash & Patch

| Command                    | What It Does                                         |
| -------------------------- | -----------------------------------------------------|
| `git stash`                | Save uncommitted changes temporarily                 |
| `git stash clear`          | Clear all stashes                                    |
| `git stash save "message"` | For clarity when using multiple stashes              |
| `git stash  branch <name>` | Create and switch to a branch from stash             |
| `git stash list`           | List saved stashes                                   |
| `git stash apply`          | Apply latest stash (without deleting it)             |
| `git stash pop`            | Apply and delete stash                               |
| `git stash drop`           | Delete a stash manually                              |
| `git format-patch`         | Create patch file from commits                       |


> 💡 **Tip:** Use `git stash` to temporarily save changes and switch context.

---

### Inspection & History

| Command                            | What It Does                                             |
| ---------------------------------- | ---------------------------------------------------------|
| `git show <commit>`               | Show details of a commit                                  |
| `git diff <commit1> <commit2>`    | Compare two commits                                       |
| `git blame <file>`                | Show who last modified each line of a file                |
| `git reflog`                      | Show all HEAD changes (including deleted branches)        |
| `git log --stat`                  | Show files changed with each commit                       |
| `git shortlog -sne`               | Summary of commits by contributors                        |
| `git log -p`                      | Show commit diffs inline                                  |
| `git diff --staged`               | Show staged vs last commit                                |
| `git log --oneline --graph --all` | Use  to visualize complete commit tree                    |


---

### Configuration & Setup

| Command                                    | What It Does                                          |
| ------------------------------------------ | ----------------------------------------------------- |
| `git config --list`                        | Show all Git config                                   |
| `git config --global user.name "Name"`     | Set global username                                   |
| `git config --global user.email "Email"`   | Set global email                                      |
| `git config credential.helper store`       | Save credentials (not secure – for local/dev only)    |
| `git config core.autocrlf input`           | Prevent Windows vs Linux line ending issues           |
| `git config alias.<name>`                  | Custom command aliases                                |
| `git config --global init.defaultBranch main`| Set default branch name to main when initializing new repositories |


> 💡 **Tip:** Use `git config --global init.defaultBranch main` to avoid defaulting to `master`.

---

### Git Tracking & File State Commands

| Command                             | What It Does                                                  |
|-------------------------------------|---------------------------------------------------------------|
| `git status`                        | Shows tracked, untracked, staged, and modified files          |
| `git add <file>`                    | Start tracking a new or modified file                         |
| `git add .`                         | Stage all changes (new/modified files)                        |
| `git restore <file>`                | Restore file to last committed state (unstage or discard changes)  |
| `git restore --staged <file>`       | Unstage a file while keeping changes                          |
| `git rm --cached <file>`            | Remove file from Git tracking but keep it in working directory     |
| `git ls-files`                      | List all tracked files                                        |
| `git check-ignore -v <file>`        | Show which rule in `.gitignore` is causing the file to be ignored  |
| `git clean -fd`                     | Remove untracked files and directories                        |
| `git diff`                          | See unstaged changes between working dir and index            |
| `git diff --staged`                 | See staged changes (index vs last commit)                     |
| `git commit -am "msg"`              | Stage and commit tracked files only (skips new untracked files)    |
| `git log --name-status`             | Show commit logs with list of changed files                   |
| `git log --stat`                    | Show commit summary with number of lines added/removed per file    |
| `git blame <file>`                  | Show line-by-line last commit + author info                   |
| `git ls-tree -r HEAD`               | List all files in the current commit/tree                     |
| `git show <commit>:<file>`          | Show a file’s content from specific commit                    |

---

### Git Life Saver Commands Cheatsheet

| Category               | Command                                | Description                                                |
| ---------------------- | -------------------------------------- | -----------------------------------------------------------|
| **Merge & Rebase**     | `git merge --abort`                    | Abort ongoing merge (when conflicts are too messy).        |
|                        | `git rebase --abort`                   | Abort rebase process.                                      |
| **Reset & Clean**      | `git reset --hard`             | Reset working directory to last commit (discard all local changes).|
|                        | `git reset --hard <commit_id>`         | Reset repo to specific commit.                             |
|                        | `git reset HEAD <file>`                | Unstage file but keep changes.                             |
|                        | `git clean -fd`                        | Remove untracked files & directories.                      |
| **History & Recovery** | `git log --oneline --graph --decorate` | View simplified commit history with branches.              |
|                        | `git reflog`                           | Show all HEAD history (recover lost commits).              |
|                        | `git checkout <commit_id>`             | Restore/review a deleted commit.                           |
|                        | `git show <commit_id>:<path/to/file>`  | Show file content from old commit.                         |
| **Branch Management**  | `git checkout -`                       | Switch to previously checked out branch.                   |
|                        | `git branch -d <branch>`               | Delete local branch safely.                                |
|                        | `git push origin --delete <branch>`    | Delete remote branch.                                      |
| **Stash (Quick Save)** | `git stash`                            | Save current changes temporarily.                          |
|                        | `git stash list`                       | List saved stashes.                                        |
|                        | `git stash apply`                      | Apply last stash (keep it).                                |
|                        | `git stash pop`                        | Apply & remove last stash.                                 |
| **Quick Fix**          | `git reset --soft HEAD~1`              | Undo last commit but keep changes staged.                  |
|                        | `git commit --amend`                   | Amend last commit (fix message/add files).                 |
| **Remote & Sync**      | `git remote -v`                        | Show all configured remotes.                               |
|                        | `git pull --rebase`                    | Pull latest changes without merge commits.                 |
|                        | `git fetch --prune`                    | Remove deleted remote branches locally.                    |


---

# Advanced Commands

This is an advanced Git reference. These commands are rarely used in daily workflows but are useful for scripting, automation, or working with Git internals.

---

### Used in Teams / DevSecOps

| Command                                          | What It Does                                     |
| ------------------------------------------------ | -------------------------------------------------|
| `git worktree add ../new-folder <branch>`        | Use multiple working trees for different branches     |
| `git filter-branch --force ...`                  | Remove files from Git history (e.g., secrets)         |
| `git bisect`                                     | Find commit that introduced a bug                     |
| `git submodule add <repo>`                       | Add repo as a submodule                               |
| `git tag <name>`                                 | Tag a specific commit (e.g., v1.0.0)                  |
| `git archive -o out.zip HEAD`                    | Export current branch as zip archive                  |
| `git clone --mirror`                             | Clone the entire repo including all refs; used for backup/migration  |


> 💡 **Tip:** `git bisect` is a power move in debugging. Definitely worth mastering.

---

### DevSecOps + GitOps Essentials

| Command                               | What It Does / Short Description                                |
| ------------------------------------- | ----------------------------------------------------------------|
| `git sparse-checkout init` + `set`    | Checkout only specific folders from a large repo (great for monorepos) |
| `git fsck`                            | Check repo for corruption and dangling commits                  |
| `git gc`                              | Clean up unnecessary files and optimize the local repository    |
| `git revert HEAD~2..HEAD`             | Revert a **range** of commits (last 2 commits in this example)  |
| `git rebase -i HEAD~3`                | Interactive rebase: squash, reorder, or edit last 3 commits     |
| `git worktree add ../folder <branch>` | Create a new working directory tied to a different branch (parallel workspace) |
| `git archive -o release.zip HEAD`     | Export current repo content as a `.zip` file (useful for releases/artifacts) |
| `git log --graph --all --decorate`    | Visualize entire repo history (useful in teams and large repos) |
| `git pull --rebase`                   | Preferred for linear history in teams.                          |


> 💡 **Tip:** Use `git worktree` to work on multiple branches without switching.
>
> ⚠️ **Warning:** Commands like `git filter-branch` and `git rebase -i` rewrite history — use them only on local or private branches.

---

### GitOps & CI/CD Relevance

| Concept / Command              | Use Case / Why It’s Useful                                           |
| ------------------------------ | ---------------------------------------------------------------------|
| GitOps                         | Git as the **single source of truth** for infrastructure (IaC) and deployments |
| `git tag <v1.0.0>`             | Mark a commit for a release; used in CI/CD pipelines                 |
| `git push origin --tags`       | Push all tags to remote (so CI/CD can trigger from them)             |
| `git checkout <tag>`           | Checkout a specific release state                                    |
| `git tag -d <tag>`             | Useful for deleting remote tags.                                     |
| `git push origin :refs/tags/<tag>`| Useful for deleting remote tags.                                  |
| `git diff <commit1> <commit2>` | Compare environments or code before/after deployment                 |



### Repository Plumbing (Low-level Internal Commands)

| Command           | Explanation                                                     |
| ----------------- | --------------------------------------------------------------- |
| `git cat-file`    | Show type, size, and content of Git objects                     |
| `git commit-tree` | Create commit object manually (used internally or in scripting) |
| `git diff-tree`   | Show differences between two trees (commits)                    |
| `git hash-object` | Hash a file and optionally write to Git database                |
| `git merge-tree`  | Show what a merge would look like                               |
| `git worktree`    | Manage multiple working directories for branches                |
| `git read-tree`   | Load tree into the staging area                                 |
| `git update-ref`  | Update ref files directly                                       |
| `git rev-parse`   | Convert ref/branch/tag into SHA or parse arguments              |
| `git fsck`        | Verify connectivity and validity of Git objects                 |
| `git gc`          | Cleanup unnecessary files to optimize repository                |
| `git prune`       | Remove unreachable objects                                      |
| `git verify-pack` | Verify contents of pack files                                   |



### Index & Working Directory Management

| Command              | Explanation                                   |
| -------------------- | --------------------------------------------- |
| `git checkout-index` | Restore files from index to working directory |
| `git ls-files`       | Show all tracked files in index               |


### References & Refs Handling

| Command            | Explanation                                 |
| ------------------ | ------------------------------------------- |
| `git for-each-ref` | Iterate over refs with custom format output |
| `git ls-remote`    | List references in a remote repository      |
| `git show-ref`     | List all references                         |
| `git symbolic-ref` | Read or modify symbolic refs like HEAD      |
| `git show-branch`  | Show branches and their commits             |
| `git show-ref --heads` | List all branch refs |
| `git show-ref --tags`  | List all tag refs    |



### Branching, Merging, History – Porcelain Commands

| Command        | Explanation                                                       |
| -------------- | ----------------------------------------------------------------- |
| `git branch`   | *(implicit in other commands, not listed above but usually here)* |
| `git checkout` | Switch branches or restore files                                  |
| `git commit`   | Commit staged changes                                             |
| `git merge`    | Combine another branch into current one                           |
| `git rebase`   | Reapply commits on another base commit                            |
| `git reset`    | Reset index and/or working tree                                   |
| `git cherry-pick --upstream` | Apply commit from another branch with upstream awareness     |
| `git merge-ours`             | Use ‘ours’ strategy to resolve conflicts                     |
| `git merge-recursive`        | Merge strategy for multiple branches                         |
| `git merge-subtree`          | Merge external repositories as subtrees                      |
| `git mergetool`              | Open configured merge tool                                   |
| `git rebase`                 | Reapply commits on another base commit *(from earlier list)* |



### Log Customization & History Exploration

| Command                   | Explanation                                        |
| ------------------------- | -------------------------------------------------- |
| `git log`                 | View commit history                                |
| `git blame`               | Show who changed each line of a file and when      |
| `git show`                | Display objects like commits, tags, or files       |
| `git bisect`              | Binary search to find commit that introduced a bug |
| `git diff`                | Show file changes                                  |
| `git log --oneline`       | Show compact one-line-per-commit log               |
| `git log --stat`          | Show changes per commit                            |
| `git log --merges`        | Show only merge commits                            |
| `git log --pretty=`       | Customize log formatting                           |
| `git log --short-commit`  | Show brief commit hash + message                   |
| `git log --topo-order`    | Show topologically ordered commits                 |
| `git reflog`              | Show reference history including deleted commits   |
| `git describe`            | Name a commit using nearest tag + distance         |



### Remote Interactions

| Command         | Explanation                            |
| --------------- | -------------------------------------- |
| `git fetch`     | Download objects and refs from remote  |
| `git push`      | Upload local commits to remote         |
| `git ls-remote` | List references in a remote repository |


### Searching

| Command    | Explanation                                                      |
| ---------- | ---------------------------------------------------------------- |
| `git grep` | Search working directory or history for lines matching a pattern |


### Tags Management

| Command                  | Explanation                    |
| ------------------------ | ------------------------------ |
| `git tag`                | Create or list tags            |
| `git tag --list`         | *(from earlier)* List all tags |
| `git tag -l`             | List tags matching pattern     |
| `git tag --delete`       | Delete a tag                   |
| `git tag --force` / `-f` | Force (overwrite) tag          |
| `git tag --sign`         | Create GPG-signed tag          |
| `git tag --verify`       | Verify GPG signature on a tag  |
| `git mktag`              | Create tag object manually     |



### Configuration & Customization (Alias & Hook)

| Command                             | Explanation                           |
| ----------------------------------- | ------------------------------------- |
| `git config --global alias.*`       | Create short aliases for Git commands |
| `git config --local core.hooksPath` | Set custom path for Git hooks         |



### Push, Pull, & Syncing with Remotes

| Command             | Explanation                               |
| ------------------- | ----------------------------------------- |
| `git push --mirror` | Push all refs and tags; mirror local repo |
| `git push --tags`   | Push all local tags                       |
| `git pull --rebase` | Pull and rebase instead of merge          |


### Patch & Email Workflow

| Command            | Explanation                     |
| ------------------ | ------------------------------- |
| `git am`           | Apply patches from emails       |
| `git format-patch` | Create patch files from commits |
| `git patch-id`     | Generate stable patch ID        |


### Submodules / Subtrees / Large Files

| Command       | Explanation                             |
| ------------- | --------------------------------------- |
| `git annex`   | Manage large files outside the Git repo |
| `git p4`      | Work with Perforce repositories         |
| `git subtree` | Include sub-projects in one repository  |



### Index & File Operations

| Command             | Explanation                                       |
| ------------------- | ------------------------------------------------- |
| `git mv`            | Rename or move a file                             |
| `git rm`            | Remove file from working dir and index            |
| `git update-index`  | Add/modify index directly                         |
| `git unpack-file`   | Extract blob from Git database                    |
| `git replace`       | Replace Git objects                               |
| `git reset --hard`  | Reset everything to last commit (⚠️ destructive)  |
| `git reset --mixed` | Reset index and unstage, keep working dir changes |
| `git revert`        | Safely undo commit by creating a new one          |
| `git stash save`    | Save current working changes to stash             |


---

### Pro Tip: Use Aliases for Speed
Consider adding a section for DevOps alias shortcuts:

```sh
git config --global alias.cm "commit -m"
git config --global alias.co "checkout"
git config --global alias.br "branch"
git config --global alias.st "status"
git config --global alias.last "log -1 HEAD"
```
