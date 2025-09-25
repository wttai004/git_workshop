# Working with remote repository via GitHub

This section covers briefly how to push your repository to GitHub, clone a repository, and push your commits to the remote origin.


# Repositories on GitHub

First, to synchronize a local directory with a remote one, you need to first create a repository on GitHub: right click your icon->Repositories->New, then type "workdir" as the repository name. 

Now, you can add the github repo as the remote repository you want to push your data to:

```
>>> git remote add origin https://github.com/<your_username>/workdir.git
>>>  git remote -v
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


# On fetch vs push

(TODO)


Git branches and merging can be quite confusing. [Here](https://stackoverflow.com/questions/71768999/how-to-merge-when-you-get-error-hint-you-have-divergent-branches-and-need-to-s)'s a stack exchange that has a good explanation.
