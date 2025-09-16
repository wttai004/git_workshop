# Exercise 2: Working with Branches

## Objective
Learn to create branches, make parallel changes, and merge them back together.

## Instructions

### Step 1: Create and switch to a new branch
```bash
git checkout -b feature-branch
# or alternatively:
# git branch feature-branch
# git checkout feature-branch
```

### Step 2: Make changes on your branch
1. Create a new file called `research-notes.txt`
2. Add some content about your research
3. Stage and commit: `git add research-notes.txt && git commit -m "Add research notes"`

### Step 3: Switch back to main and make different changes
```bash
git checkout main
```
1. Edit `student-info.txt` to add your email
2. Stage and commit these changes

### Step 4: View your branches and history
```bash
git branch
git log --oneline --graph --all
```

### Step 5: Merge your feature branch
```bash
git merge feature-branch
```

### Step 6: Clean up
```bash
git branch -d feature-branch
```

## Expected Outcome
- You understand how branches allow parallel development
- You can create, switch between, and merge branches
- You see how Git maintains separate histories that can be combined

## Common Issues
- **Merge conflicts**: If you edited the same lines in both branches, Git will ask you to resolve conflicts manually
- **Detached HEAD**: Make sure you're on a branch, not a specific commit

## Verification
Run `git log --oneline --graph` - you should see a merge commit if there were parallel changes.