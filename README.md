# Git & GitHub Workshop for Penn Graduate Students

This workshop provides a hands-on introduction to Git version control and GitHub collaboration for graduate students at the University of Pennsylvania.

## Workshop Overview

By the end of this workshop, you will be able to:
- Understand the fundamentals of version control with Git
- Create and manage repositories
- Track changes, commit code, and view history
- Work with branches for parallel development
- Collaborate with others using GitHub
- Handle common Git workflows and scenarios

## Prerequisites

- Basic command line familiarity
- A computer with Git installed
- A GitHub account (free)

## Getting Started

### Install Git
- **Windows**: Download from [git-scm.com](https://git-scm.com/)
- **macOS**: `brew install git` or download from git-scm.com
- **Linux**: `sudo apt-get install git` (Ubuntu/Debian) or `sudo yum install git` (RedHat/CentOS)

### Configure Git
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Workshop Agenda

### Part 1: Git Fundamentals (45 minutes)
1. [What is Version Control?](#what-is-version-control)
2. [Creating Your First Repository](#creating-your-first-repository)
3. [Basic Git Commands](#basic-git-commands)
4. [Tracking Changes](#tracking-changes)
5. [Viewing History](#viewing-history)

### Part 2: Branching and Merging (30 minutes)
1. [Understanding Branches](#understanding-branches)
2. [Creating and Switching Branches](#creating-and-switching-branches)
3. [Merging Changes](#merging-changes)
4. [Resolving Conflicts](#resolving-conflicts)

### Part 3: GitHub Collaboration (45 minutes)
1. [Introduction to GitHub](#introduction-to-github)
2. [Pushing to Remote Repositories](#pushing-to-remote-repositories)
3. [Cloning and Forking](#cloning-and-forking)
4. [Pull Requests](#pull-requests)
5. [Issues and Project Management](#issues-and-project-management)

## What is Version Control?

Version control is a system that records changes to files over time so you can recall specific versions later. Think of it as "track changes" for your entire project.

**Benefits:**
- Track all changes to your code
- Collaborate with others without conflicts
- Revert to previous versions if needed
- Create experimental branches safely
- Maintain a complete history of your project

## Creating Your First Repository

A repository (or "repo") is a directory that contains your project files and the complete history of changes.

### Initialize a new repository:
```bash
mkdir my-first-repo
cd my-first-repo
git init
```

### Check repository status:
```bash
git status
```

## Basic Git Commands

| Command | Purpose |
|---------|---------|
| `git init` | Initialize a new repository |
| `git status` | Show current status of files |
| `git add <file>` | Stage changes for commit |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Commit staged changes |
| `git log` | View commit history |
| `git diff` | Show unstaged changes |

## Tracking Changes

### The Git Workflow:
1. **Working Directory**: Make changes to files
2. **Staging Area**: Add changes you want to commit
3. **Repository**: Commit changes with a message

### Example workflow:
```bash
# Create a new file
echo "Hello, Git!" > hello.txt

# Check status
git status

# Stage the file
git add hello.txt

# Commit the change
git commit -m "Add hello.txt with greeting message"

# View the log
git log --oneline
```

## Understanding Branches

Branches allow you to work on different features or experiments without affecting the main codebase.

### Branch commands:
```bash
# List all branches
git branch

# Create a new branch
git branch feature-branch

# Switch to a branch
git checkout feature-branch

# Create and switch in one command
git checkout -b new-feature

# Switch back to main
git checkout main

# Merge a branch
git merge feature-branch

# Delete a branch
git branch -d feature-branch
```

## Introduction to GitHub

GitHub is a cloud-based platform that hosts Git repositories and provides collaboration features.

### Key GitHub Features:
- Remote repository hosting
- Issue tracking
- Pull requests for code review
- Project management tools
- Community features

### Connecting to GitHub:
```bash
# Add a remote repository
git remote add origin https://github.com/username/repository.git

# Push to GitHub
git push -u origin main

# Pull changes from GitHub
git pull origin main

# Clone a repository
git clone https://github.com/username/repository.git
```

## Hands-On Exercises

### Exercise 1: Create Your First Commit
1. Create a new file called `about.txt`
2. Add information about yourself
3. Stage and commit the file
4. View the commit in the log

### Exercise 2: Work with Branches
1. Create a new branch called `bio-update`
2. Switch to the branch
3. Modify `about.txt` to add more details
4. Commit the changes
5. Switch back to main and merge the branch

### Exercise 3: GitHub Collaboration
1. Fork this repository
2. Clone your fork locally
3. Make a change to this README
4. Push your changes
5. Create a pull request

## Common Git Scenarios

### Undo Changes
```bash
# Unstage a file
git reset HEAD <file>

# Discard changes in working directory
git checkout -- <file>

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1
```

### Working with Remote Repositories
```bash
# See configured remotes
git remote -v

# Fetch changes without merging
git fetch origin

# Pull and merge changes
git pull origin main

# Push to remote
git push origin main
```

## Best Practices

1. **Write clear commit messages**: Explain what and why, not how
2. **Commit often**: Small, logical commits are easier to track
3. **Use branches**: Keep experimental work separate
4. **Pull before pushing**: Stay up to date with remote changes
5. **Review before committing**: Use `git diff` to check your changes

## Troubleshooting

### Common Issues:
- **Merge conflicts**: When Git can't automatically merge changes
- **Detached HEAD**: Working on a specific commit instead of a branch
- **Authentication**: Setting up SSH keys or personal access tokens

### Getting Help:
```bash
# Get help for any command
git help <command>
git <command> --help

# Quick reference
git --help
```

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)
- [Git Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet/)

## Workshop Feedback

After completing this workshop, please provide feedback to help us improve future sessions. You can:
- Open an issue in this repository
- Submit a pull request with improvements
- Contact the workshop organizers

---

*This workshop was created for Penn graduate students to learn Git and GitHub fundamentals. Feel free to use and adapt these materials for your own learning or teaching needs.*
