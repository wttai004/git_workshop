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


# Basic operations

(git status, add, commit, stash, diff)

(gitignore)


Note: `git diff` works best for files that are in plain text formats. Using this on more complicated files (e.g. pdf, Mathematica notebooks) will lead to outputs that are not human readable. 

# A note on Jupyter notebook

Many researchers (myself included) routinely use Jupyter notebook to prototype or demosntrate a calculation. Unfortunately, Jupyter notebook don't play too well with git, because Jupyter notebook under the hood is a JSON file with metadata that changes every time you execute a cell (even if the cell itself is unchanged). This means that tracking differences in Jupyter notebook can be difficult, and also complicates team collaboration effort. There are extensions one can use to integrate Jupyter notebooks and git ([here](https://www.reviewnb.com/git-jupyter-notebook-ultimate-guide#git--jupyter-challenges) is a guide), but they are out of the scope for this workshop. There are also alternative python notebooks such as [Marimo](https://marimo.io) that explicitly aims to be more git-friendly.
