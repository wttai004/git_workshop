# Exercise 1: Your First Git Repository

## Objective
Learn to create a repository, make commits, and track changes.

## Instructions

### Step 1: Create a new directory and initialize Git
```bash
mkdir git-practice
cd git-practice
git init
```

### Step 2: Create your first file
Create a file called `student-info.txt` with the following content:
```
Name: [Your Name]
Program: [Your Graduate Program]
Year: [Your Year in Program]
Research Interest: [Brief description]
```

### Step 3: Stage and commit your file
```bash
git add student-info.txt
git commit -m "Add initial student information"
```

### Step 4: Make changes and commit again
1. Edit `student-info.txt` to add more details
2. Check the status: `git status`
3. See what changed: `git diff`
4. Stage and commit your changes

### Step 5: View your history
```bash
git log
git log --oneline
git log --graph --oneline
```

## Expected Outcome
- You have a Git repository with at least 2 commits
- You understand the basic Git workflow: edit → add → commit
- You can view your project history

## Verification
Run `git log --oneline` - you should see your commits listed.