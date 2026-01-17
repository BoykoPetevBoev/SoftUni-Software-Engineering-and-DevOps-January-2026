# SoftUni-Software-Engineering-and-DevOps-January-2026

## Git Commands Reference

### Configuration Commands

#### `git config`
Configure Git settings such as username, email, and preferences.
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list  # View all configurations
```

### Repository Management

#### `git init`
Initialize a new Git repository in the current directory.
```bash
git init
```

#### `git clone`
Clone an existing repository from a remote source.
```bash
git clone <repository-url>
git clone <repository-url> <directory-name>
```

### Basic Snapshotting

#### `git add`
Add file contents to the staging area (index).
```bash
git add <file>           # Add specific file
git add .                # Add all files in current directory
git add -A               # Add all changes (new, modified, deleted)
git add *.js             # Add all JavaScript files
```

#### `git status`
Show the working tree status and staged changes.
```bash
git status
git status -s  # Short format
```

#### `git commit`
Record changes to the repository.
```bash
git commit -m "Commit message"
git commit -a -m "Message"  # Add and commit tracked files
git commit --amend          # Modify the last commit
```

#### `git diff`
Show changes between commits, commit and working tree, etc.
```bash
git diff                    # Changes not staged
git diff --staged           # Changes staged for commit
git diff <commit1> <commit2>  # Between two commits
```

#### `git reset`
Reset current HEAD to the specified state.
```bash
git reset <file>            # Unstage a file
git reset --soft HEAD~1     # Undo last commit, keep changes staged
git reset --mixed HEAD~1    # Undo last commit, unstage changes
git reset --hard HEAD~1     # Undo last commit, discard changes
```

#### `git rm`
Remove files from the working tree and index.
```bash
git rm <file>               # Remove file
git rm --cached <file>      # Remove from index only
```

#### `git mv`
Move or rename a file, directory, or symlink.
```bash
git mv <old-name> <new-name>
```

### Branching and Merging

#### `git branch`
List, create, or delete branches.
```bash
git branch                  # List all local branches
git branch <branch-name>    # Create new branch
git branch -d <branch-name> # Delete branch
git branch -D <branch-name> # Force delete branch
git branch -m <new-name>    # Rename current branch
git branch -a               # List all branches (local and remote)
```

#### `git checkout`
Switch branches or restore working tree files.
```bash
git checkout <branch-name>      # Switch to branch
git checkout -b <branch-name>   # Create and switch to new branch
git checkout <commit-hash>      # Checkout specific commit
git checkout -- <file>          # Discard changes in file
```

#### `git switch`
Switch to a specified branch (newer alternative to checkout for switching branches).
```bash
git switch <branch-name>        # Switch to branch
git switch -c <branch-name>     # Create and switch to new branch
```

#### `git merge`
Join two or more development histories together.
```bash
git merge <branch-name>         # Merge branch into current branch
git merge --no-ff <branch-name> # Merge with merge commit
git merge --abort               # Abort merge in case of conflicts
```

#### `git rebase`
Reapply commits on top of another base tip.
```bash
git rebase <branch-name>        # Rebase current branch
git rebase -i HEAD~3            # Interactive rebase last 3 commits
git rebase --continue           # Continue after resolving conflicts
git rebase --abort              # Abort rebase
```

### Sharing and Updating

#### `git fetch`
Download objects and refs from another repository.
```bash
git fetch                       # Fetch from default remote
git fetch <remote>              # Fetch from specific remote
git fetch --all                 # Fetch from all remotes
```

#### `git pull`
Fetch from and integrate with another repository or local branch.
```bash
git pull                        # Pull from default remote
git pull <remote> <branch>      # Pull from specific remote/branch
git pull --rebase               # Pull and rebase instead of merge
```

#### `git push`
Update remote refs along with associated objects.
```bash
git push                            # Push to default remote
git push <remote> <branch>          # Push to specific remote/branch
git push -u origin <branch>         # Push and set upstream
git push --all                      # Push all branches
git push --tags                     # Push all tags
git push --force                    # Force push (use with caution)
```

#### `git remote`
Manage set of tracked repositories.
```bash
git remote                      # List remotes
git remote -v                   # List remotes with URLs
git remote add <name> <url>     # Add new remote
git remote remove <name>        # Remove remote
git remote rename <old> <new>   # Rename remote
git remote show <name>          # Show remote details
```

### Inspection and Comparison

#### `git log`
Show commit logs.
```bash
git log                         # Show commit history
git log --oneline               # Condensed view
git log --graph                 # Show branch graph
git log --all --decorate --oneline --graph  # Detailed graph
git log -p                      # Show patches (diffs)
git log --author="Name"         # Filter by author
git log --since="2 weeks ago"   # Filter by date
git log <file>                  # Show commits for specific file
```

#### `git show`
Show various types of objects.
```bash
git show <commit-hash>          # Show commit details
git show <tag-name>             # Show tag details
git show HEAD                   # Show latest commit
```

#### `git blame`
Show what revision and author last modified each line of a file.
```bash
git blame <file>
git blame -L 10,20 <file>       # Blame specific lines
```

#### `git reflog`
Show reference logs (useful for recovering lost commits).
```bash
git reflog
git reflog show <branch>
```

### Stashing

#### `git stash`
Stash the changes in a dirty working directory.
```bash
git stash                       # Stash current changes
git stash save "message"        # Stash with message
git stash list                  # List all stashes
git stash apply                 # Apply most recent stash
git stash apply stash@{n}       # Apply specific stash
git stash pop                   # Apply and remove most recent stash
git stash drop stash@{n}        # Delete specific stash
git stash clear                 # Delete all stashes
```

### Tagging

#### `git tag`
Create, list, delete, or verify tags.
```bash
git tag                         # List all tags
git tag <tag-name>              # Create lightweight tag
git tag -a <tag-name> -m "msg"  # Create annotated tag
git tag -d <tag-name>           # Delete tag
git push origin <tag-name>      # Push tag to remote
git push origin --tags          # Push all tags
```

### Undoing Changes

#### `git revert`
Create new commit that undoes changes from a previous commit.
```bash
git revert <commit-hash>        # Revert specific commit
git revert HEAD                 # Revert last commit
```

#### `git restore`
Restore working tree files (newer alternative to checkout for file restoration).
```bash
git restore <file>              # Discard changes in file
git restore --staged <file>     # Unstage file
git restore --source=HEAD~1 <file>  # Restore from specific commit
```

#### `git clean`
Remove untracked files from the working tree.
```bash
git clean -n                    # Dry run (show what would be deleted)
git clean -f                    # Force delete untracked files
git clean -fd                   # Delete untracked files and directories
git clean -fx                   # Delete untracked and ignored files
```

### Advanced Commands

#### `git cherry-pick`
Apply the changes introduced by some existing commits.
```bash
git cherry-pick <commit-hash>   # Apply specific commit to current branch
git cherry-pick <hash1> <hash2> # Apply multiple commits
```

#### `git worktree`
Manage multiple working trees.
```bash
git worktree add <path> <branch>    # Add new working tree
git worktree list                   # List all working trees
git worktree remove <path>          # Remove working tree
```

#### `git bisect`
Use binary search to find the commit that introduced a bug.
```bash
git bisect start
git bisect bad                  # Current version is bad
git bisect good <commit-hash>   # Known good commit
git bisect reset                # End bisect session
```

#### `git submodule`
Initialize, update, or inspect submodules.
```bash
git submodule add <url> <path>      # Add submodule
git submodule init                  # Initialize submodules
git submodule update                # Update submodules
git submodule update --remote       # Update to latest remote
```

### Collaboration

#### `git archive`
Create an archive of files from a named tree.
```bash
git archive --format=zip HEAD > project.zip
git archive --format=tar --prefix=project/ HEAD | gzip > project.tar.gz
```

#### `git shortlog`
Summarize git log output.
```bash
git shortlog                    # Summary by author
git shortlog -sn                # Count commits by author
```

### Debugging and Maintenance

#### `git fsck`
Verify the connectivity and validity of objects in the database.
```bash
git fsck
```

#### `git gc`
Cleanup unnecessary files and optimize the local repository.
```bash
git gc
git gc --aggressive             # More thorough optimization
```

#### `git prune`
Remove unreachable objects from the object database.
```bash
git prune
```

---

## Common Git Workflows

### Feature Branch Workflow
```bash
git checkout -b feature/new-feature
# Make changes
git add .
git commit -m "Add new feature"
git push -u origin feature/new-feature
# Create pull request
# After merge
git checkout main
git pull
git branch -d feature/new-feature
```

### Hotfix Workflow
```bash
git checkout -b hotfix/bug-fix main
# Fix the bug
git add .
git commit -m "Fix critical bug"
git checkout main
git merge hotfix/bug-fix
git push
git branch -d hotfix/bug-fix
```

### Syncing Fork
```bash
git remote add upstream <original-repo-url>
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```