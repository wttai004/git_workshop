# Working with remote repository via GitHub

This section covers briefly how to push your repository to GitHub, clone a repository, and push your commits to the remote origin.


# Repositories on GitHub

First, to synchronize a local directory with a remote one, you need to first create a repository on GitHub: right click your icon->Repositories->New, then type "workdir" as the repository name. 

Now, you can add the GitHub repo as the remote repository you want to push your data to:

```
>>> git remote add origin https://github.com/<your_username>/workdir.git
>>> git remote -v
origin	https://github.com/<your_username>/workdir.git (fetch)
origin	https://github.com/<your_username>/workdir.git (push)
```

Now, you can push your repository to the git repo

```
>>> git push -u origin main  
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 10 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (9/9), 708 bytes | 708.00 KiB/s, done.
Total 9 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/<your_username>/workdir.git
 * [new branch]      main -> main

```

The `-u` in `git push -u origin main` sets `main`'s upstream to be `origin/main`. Do this the first time you push a branch. See [here](https://stackoverflow.com/questions/5697750/what-exactly-does-the-u-do-git-push-u-origin-master-vs-git-push-origin-ma) for more info.

# Synchronizing local changes to remote repository

Suppose you modify your local repository:

```
>>> echo "Testing file to be pushed" >> push.txt
>>> git add push.txt 
>>> git commit -m "Added push.txt."
[main 55336bf] Added push.txt.
 1 file changed, 1 insertion(+)
 create mode 100644 push.txt
```

Pushing this to remote is as simple as using `git push`: 

```
>>> git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 10 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 335 bytes | 335.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/(your username)/workdir.git
   0c44a25..55336bf  main -> main
```

Here, `origin` is the alias on your system for the remote repository, and `main` is the branch you are currently in (more on this in next section).

On the other hand, let's say that you create a new file named `pull.txt` remotely on your GitHub in this folder (click "Add file->Create New File") . Now, your remote repository would look like this:

<img width="1477" height="387" alt="Screenshot 2025-09-30 at 21 25 11" src="https://github.com/user-attachments/assets/9862564f-9918-4c5d-9488-a4d17f88a334" />

To get this new file on your device, you would need `git pull` on your local device:

```
>>> git pull origin main
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 1009 bytes | 336.00 KiB/s, done.
From https://github.com/(your username)/workdir
 * branch            main       -> FETCH_HEAD
   55336bf..ab2df85  main       -> origin/main
Updating 55336bf..ab2df85
Fast-forward
 pull.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 pull.txt
```

# Getting a repository from GitHub

`Fork` refers to copying someone's GitHub repository and putting it in your GitHub account, so that you have your own copy to work with. You can try this with the git workshop: simply click the **Fork** icon near the top right corner

To clone a directory (whether your own or someone else) to your own local computer, simply use `clone`:

```
>>> git clone https://github.com/(your_username)/git_workshop.git ~/git_workshop
```

This will clone the directory to your local device at the directory `~/workshop`. Note that by cloning a repository, it is already associated with the remote repository, so you don't need to run the `git remote add origin` in order to push your commits to your remote repo later on. 


# Branches and remote repositores

Remotes repositories (e.g., GitHub) have their own branches. Locally you track them via remote-tracking refs like `origin/main`. A local branch typically has an upstream it tracks (e.g., dev ↔ origin/dev). Fundamentally, when you pull for remote branches, you are simply merging the remote branch with your local branch. 

git pull is shorthand for:
	1.	git fetch (update your remote-tracking branches), then
	2.	integrate those fetched commits into your current branch — by default via merge, or via rebase if configured/asked.

Under the hood, if you are using  `git pull` to merge the remote `main` branch to the local one, it is equivalent to `git fetch` and then `git merge origin/main`. 

For best practice, always fetch/merge and pull before making local changes. Otherwise, merge conflicts would happen and need to be solved manually. 
