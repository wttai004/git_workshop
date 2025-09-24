# Basic commands

This section will walk you through basic commands.

# Creating a directory

We first create a local directory to use as a testbed, which we initialize as a git directory:

```
>> mkdir ~/workdir
>> cd ~/workdir
>> git init
(base) wttai@MacBook-Pro-109 workdir % git init
Initialized empty Git repository in (your home directory)/workdir/.git/
```

This would create a hidden folder `.git` where the version history information are stored. 

Using `git status` allows you to view the status of your repository.

```
>>> git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

You should see that you're on the "main" branch (older git versions might set you to a default "master" branch instead—they are identical except in name)

