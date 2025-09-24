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


Now, let's create a simple file to demonstrate how git tracks them.

```
>>> echo hello >> foo.txt
>>> git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	foo.txt

nothing added to commit but untracked files present (use "git add" to track)
```

The first commands creates a text file `foo.txt`. You'll notice that it's considered 'untracked' by git–new files are not tracked by git by default. To have its versions be tracked,

```
>>>git add foo.txt 
>>>git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   foo.txt
```


Now, we can use `git commit` to create a version of our file

```
>>> git commit -m "Created foo.txt"
[main (root-commit) 76f9e71] Created foo.txt
 1 file changed, 1 insertion(+)
 create mode 100644 foo.txt
```

(`-m` sets a message for the commit—it's mandatory to include a message, and advisable for your future selves to set this to something that helps you understand what you changed.)

Now let's further change the text

```
>>> echo world >> foo.txt 
>>> git add foo.txt
>>> git commit -m "Further changed foo.txt"
[main 0d2cd7c] Further changed foo.txt
 1 file changed, 1 insertion(+)
```


# Viewing history and difference

To view the history of your file, you can use `git log`:

```
>>> git log
commit 0d2cd7c99362cf827294a1c91851c1dbd7e93ca3 (HEAD -> main)
Author: (Your name)  <(Your email)>
Date:   Wed Sep 24 12:58:29 2025 -0400

    Further changed foo.txt

commit 76f9e7107b763654eb94151baef62c0cd98e7264
Author: (Your name)  <(Your email)>
Date:   Wed Sep 24 12:50:22 2025 -0400

    Created foo.txt
```

You can see that each commit comes with a unique identifier, and that the most recent one is labeled (HEAD -> main). HEAD means that it is where git is at right now.


Note: `git diff` works best for files that are in plain text formats. Using this on more complicated files (e.g. pdf, Mathematica notebooks) will lead to outputs that are not human readable. 

# Other commands of note

`git reset` allows you to reset a commit. For example, `git reset HEAD^` resets to the previous commit,  `git reset HEAD^^` to two previous ones, etc. You can also use the commit ID in place.

`git revert` is another way to reset a commit, but it does so by creating a new commit that is identical to the desired one. This is a better choice for works with a remote repository where you have already pushed a commit. 

# A note on Jupyter notebook

Many researchers (myself included) routinely use Jupyter notebook to prototype or demosntrate a calculation. Unfortunately, Jupyter notebook don't play too well with git, because Jupyter notebook under the hood is a JSON file with metadata that changes every time you execute a cell (even if the cell itself is unchanged). This means that tracking differences in Jupyter notebook can be difficult, and also complicates team collaboration effort. There are extensions one can use to integrate Jupyter notebooks and git ([here](https://www.reviewnb.com/git-jupyter-notebook-ultimate-guide#git--jupyter-challenges) is a guide), but they are out of the scope for this workshop. There are also alternative python notebooks such as [Marimo](https://marimo.io) that explicitly aims to be more git-friendly.
