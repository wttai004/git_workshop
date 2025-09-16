# Git Commands Cheat Sheet

## Basic Commands

### Repository Setup
```bash
git init                    # Initialize a new repository
git clone <url>            # Clone a remote repository
git remote add origin <url> # Add a remote repository
```

### Tracking Changes
```bash
git status                 # Show working directory status
git add <file>            # Stage a specific file
git add .                 # Stage all changes
git add -A                # Stage all changes including deletions
git commit -m "message"   # Commit staged changes
git commit -am "message"  # Stage and commit all tracked files
```

### Viewing History
```bash
git log                   # Show commit history
git log --oneline         # Compact log format
git log --graph           # Show branch structure
git log --stat            # Show files changed in each commit
git show <commit-hash>    # Show details of a specific commit
git diff                  # Show unstaged changes
git diff --staged         # Show staged changes
```

## Branch Management

### Working with Branches
```bash
git branch                # List all branches
git branch <name>         # Create a new branch
git checkout <branch>     # Switch to a branch
git checkout -b <branch>  # Create and switch to new branch
git merge <branch>        # Merge branch into current branch
git branch -d <branch>    # Delete a branch
git branch -D <branch>    # Force delete a branch
```

### Remote Branches
```bash
git fetch                 # Download remote changes
git pull                  # Fetch and merge remote changes
git push origin <branch>  # Push branch to remote
git push -u origin <branch> # Push and set upstream
git branch -r             # List remote branches
git branch -a             # List all branches (local and remote)
```

## Undoing Changes

### Local Changes
```bash
git checkout -- <file>    # Discard changes in working directory
git reset HEAD <file>     # Unstage a file
git reset --soft HEAD~1   # Undo last commit, keep changes staged
git reset --hard HEAD~1   # Undo last commit, discard changes
git clean -fd             # Remove untracked files and directories
```

### Remote Changes
```bash
git revert <commit>       # Create new commit that undoes changes
git push origin --delete <branch> # Delete remote branch
```

## Collaboration

### Working with Remotes
```bash
git remote -v             # Show remote repositories
git remote add <name> <url> # Add a remote
git remote remove <name>  # Remove a remote
git fetch <remote>        # Fetch from specific remote
git pull <remote> <branch> # Pull from specific remote/branch
git push <remote> <branch> # Push to specific remote/branch
```

### Tags
```bash
git tag                   # List tags
git tag <tagname>         # Create a tag
git tag -a <tagname> -m "message" # Create annotated tag
git push origin <tagname> # Push tag to remote
git push origin --tags    # Push all tags
```

## Advanced Commands

### Stashing
```bash
git stash                 # Stash current changes
git stash pop             # Apply and remove latest stash
git stash list            # List all stashes
git stash apply <stash>   # Apply specific stash
git stash drop <stash>    # Delete specific stash
```

### Rebasing
```bash
git rebase <branch>       # Rebase current branch onto another
git rebase -i HEAD~n      # Interactive rebase for last n commits
git rebase --abort        # Cancel rebase
git rebase --continue     # Continue rebase after resolving conflicts
```

### Configuration
```bash
git config --global user.name "Name"     # Set global username
git config --global user.email "email"   # Set global email
git config --list                        # Show all configuration
git config --global core.editor "editor" # Set default editor
```

## Useful Aliases

Add these to your Git configuration:
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.lg "log --oneline --graph --all"
```

## Emergency Commands

### When things go wrong:
```bash
git reflog                # Show reference log (recent actions)
git fsck --full           # Check repository integrity
git gc                    # Clean up repository
```

Remember: Git is designed to preserve your work. Most "mistakes" can be undone!