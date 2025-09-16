# Exercise 3: GitHub Collaboration

## Objective
Learn to work with remote repositories, forks, and pull requests.

## Instructions

### Step 1: Fork this repository
1. Go to https://github.com/wttai004/git_workshop
2. Click the "Fork" button in the top right
3. This creates your own copy of the repository

### Step 2: Clone your fork
```bash
git clone https://github.com/YOUR_USERNAME/git_workshop.git
cd git_workshop
```

### Step 3: Create a branch for your changes
```bash
git checkout -b add-my-info
```

### Step 4: Add yourself to the participants list
1. Create or edit the file `participants.md`
2. Add your information:
   ```markdown
   ## Workshop Participants
   
   - [Your Name] - [Your Program] - [Research Area]
   ```

### Step 5: Commit and push your changes
```bash
git add participants.md
git commit -m "Add [Your Name] to participants list"
git push origin add-my-info
```

### Step 6: Create a Pull Request
1. Go to your fork on GitHub
2. Click "Compare & pull request"
3. Add a description of your changes
4. Submit the pull request

### Step 7: Explore collaboration features
- Look at the Issues tab
- Check out other people's pull requests
- Try reviewing someone else's code

## Expected Outcome
- You understand the fork → clone → branch → commit → push → pull request workflow
- You've contributed to a collaborative project
- You see how GitHub facilitates code review and collaboration

## Best Practices for Pull Requests
- Write clear, descriptive titles
- Explain what you changed and why
- Keep changes focused and small
- Test your changes before submitting

## Verification
Your pull request should appear in the original repository's pull requests tab.