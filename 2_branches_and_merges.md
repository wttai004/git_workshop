# Branches

One powerful—and potentially confusing—feature of git is its uses of branches, which is a movable pointer to a certain commit. A typical usage for software developers is that you have a "main" branch with a stable version, while different features are developed by different workers in separate branches. Once a feature is deemed stable, it'll be merged into the main branch. 

For individual researchers, here are common use cases:

- Start from a known-good commit: create a tag to bookmark it (e.g., v1.0), then branch from there to experiment without risking the tagged state.
- Work across devices: push your branches to a remote (e.g., GitHub) and pull them elsewhere; your local branches track remote-tracking branches like origin/main.

At the most basic user level, you don't have to worry about branches, but they can be very helpful.

<img width="1015" height="599" alt="Screenshot 2025-09-30 at 21 38 49" src="https://github.com/user-attachments/assets/4d1a9c5c-8db6-4648-932a-42b205846f60" />
Pictorial representation of branching. [Source](https://www.atlassian.com/git/tutorials/using-branches).

# Branching

To create a new branch:

```
>>> git branch dev
>>> git switch dev
Switched to branch 'dev'
>>> git status
On branch dev
nothing to commit, working tree clean
```

`git branch (branchname)` creates a new branch but _does not switch to the new branch_. To go to the new branch, you need to use either `git switch` or (in older versions) `git branch`. Alternatively,  `git switch -c (branchname)` or (in older versions) `git checkout -b (branchname)` is a shorthand to both create and switch to the branch. 

(Note: `git switch` is a newer syntax compared to `git checkout` for switching branches, which is overloaded because `git checkout` is used both to switch branches and to reset files to certain revisions.)


## Working on different branches

```
>>> git switch main
Switched to branch 'main'
>>> echo "Main branch" >> main_branch.txt
>>> git add main_branch.txt 
>>> git commit -m "Created main_branch.txt"
[main 1885bc8] Created main_branch.txt
 1 file changed, 1 insertion(+)
 create mode 100644 main_branch.txt
>>> ls
foo.txt		main_branch.txt pull.txt	push.txt	test.log
>>> git switch dev
Switched to branch 'dev'
>>> ls
foo.txt
```

Note that the files you created in the main branch doesn't impact the dev branch.

```
>>> echo "Dev branch" >> dev_branch.txt
>>> git add dev_branch.txt 
>>> git commit -m "Created dev_branch.txt"
[dev efe2181] Created dev_branch.txt
 1 file changed, 1 insertion(+)
 create mode 100644 dev_branch.txt
>>> ls
dev.txt foo.txt
```

You can also use `git show` to examine an individual file in a branch/commit, or `git checkout` to replace the working copy of the file with the version from the branch/commit.

```
>>> git switch dev
>>> git show main:main_branch.txt
Main branch # The file won't be in the dev branch
>>> git checkout main -- main_branch.txt
>>> ls
dev.txt foo.txt		main_branch.txt # Now the file exists
>>> rm main_branch.txt # Cleaning up the directory
```

Finally, you can use `git log` to show the history of your current hsitory's branch (and use `git log --all` to show the history of all branches)

```
>>> git log --all        
commit 25021c7a012e672a2ef528e40d2f9ff326077199 (HEAD -> dev)
Author: Terrence Tai <wt662606957@gmail.com>
Date:   Wed Oct 15 19:38:56 2025 -0400

    Created dev_branch.txt

commit fd497bd2bc4e241454c2c76c34e8aa46080e54e9 (main)
Author: Terrence Tai <wt662606957@gmail.com>
Date:   Wed Oct 15 19:38:02 2025 -0400

    Created main_branch.txt

commit 4692e1d3743845f714001551fe317991e556d746
Author: Terrence Tai <wt662606957@gmail.com>
Date:   Wed Oct 15 19:10:59 2025 -0400

    Created .gitignore

commit 673a07dbc6ca25cbd5276b2fba2322abc32ddf44
Author: Terrence Tai <wt662606957@gmail.com>
Date:   Wed Oct 15 18:39:39 2025 -0400

    Further changed foo.txt

commit 4bea9980615d04c916890fef79cee8f6e3e13bd8
Author: Terrence Tai <wt662606957@gmail.com>
Date:   Wed Oct 15 18:36:05 2025 -0400

    Created foo.txt

```

## Merging

```
>>> git switch dev
>>> git merge main
Merge made by the 'ort' strategy.
 main_branch.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 main_branch.txt
>>> ls
dev_branch.txt	foo.txt		main_branch.txt
```

## Merge conflicts

Conflicts happen when both branches change the same files.

```
>>> git checkout -b conflict
Switched to a new branch 'conflict'
>>> echo "Mainnnnnnnnn branch" > main_branch.txt
>>> git add main_branch.txt 
>>> git commit -m "Modified an existing file in conflict branch. This would cause conflict."
[conflict 8140a1e] Modified an existing file in conflict branch. This would cause conflict.
 1 file changed, 1 insertion(+)
>>> git switch main
Switched to branch 'main'
>>> echo "Branch" > main_branch.txt
>>> git add main_branch.txt
>>> git commit -m "Modified an existing file in main branch. This would cause conflict."
[main b081615] Modified an existing file in main branch. This would cause conflict.
 1 file changed, 1 insertion(+), 1 deletion(-)
>>> git merge main
Auto-merging main_branch.txt
CONFLICT (content): Merge conflict in main_branch.txt
Automatic merge failed; fix conflicts and then commit the result.
```

This **merge conflict** needs to be resolved manually. If you view the culprit file, you'll see that both the HEAD version and the version to be merged in the main branch are listed side by side:

```
>>> cat main_branch.txt
<<<<<<< HEAD
Mainnnnnnnnn branch
=======
Main branch
>>>>>>> main
```

In this case, you'll need to manually resolve the conflict by modifying it

```
>>> echo "Main branch—solved" > main_branch.txt
>>> git add main_branch.txt
>>> git commit -m "Manually resolved conflict"
```

To bring this fix onto main:

```
git switch main
git merge conflict
```

# Fast forward vs three-way merges

Under the hood, `git merge` has two operating modes: fast-forwarding and three-way merging. Fast-forward merges happen when there's a linear path from the current branch tip to the target branch—in this case, merging is as simple as moving the current branch tip to the target branch tip. On the other hand, when the two branches diverge (for example, when you are pulling a modified remote repository while your local one has been modified), git needs a dedicated commit to tie together the two histories. `git merge` attempts fast-forward merge if possible, and falls back to three-way merges if not. Some three-way merges can still be handled automatically: for example, the case above where the `main` and `dev` branches involve modifying different files. The schematics below visualizes the differences between the two merge modes (Source: [Atlassian](https://www.atlassian.com/git/tutorials/using-branches/git-merge))



<img width="427" height="662" alt="Screenshot 2025-10-08 at 00 25 35" src="https://github.com/user-attachments/assets/b8897bd9-40dc-4044-af8f-cdf7d9df78fe" />   

vs

<img width="427" height="662" alt="Screenshot 2025-10-08 at 00 26 00" src="https://github.com/user-attachments/assets/e3d44f86-692d-4b75-aed2-3a9e4431fe4d" />


# A note on merge vs rebase 

Merge and rebase are two different ways to combine two branches. They both create the same project states, but different histories. 

**Merge** (creates a new _merge commit_ that ties both lines together):

```

          I--J
         /    \
...--G--H      M   <-- your-branch (HEAD)
         \    /
          K--L   <-- origin/main
```


**Rebase** (replays your commits on top of a new base, creating new commits):

```
          I--J   [abandoned]
         /
...--G--H--K--L   <-- origin/main
               \
                I'-J'  <-- your-branch
```

**In solo work, the choice is mostly about how you want your history to look**; in larger collaborations, teams set policies to avoid rewriting shared history.

To illustrate the difference, imagine that Alice is working on a feature in her unpolished `dev` branch when Bob pushed a new stable feature in the `main` branch. Alice can *rebase* her `dev` branch to `main`, incorporating Bob's feature while keeping the history linear. After she's happy with her work, she then *merges* `dev`  into `main`—here, using rebase would be inappropriate as this would rewrite the public history of `main` branch to include her own personal ones in the `dev` branch.

**Rule of thumb**
- **Rebase your own, unpublished branch** onto origin/main to catch up and keep history linear
- **Merge when integrating into main.** Don’t rebase a public/shared branch.

Further read: 

**Merging vs rebasing—Atlassian**: https://www.atlassian.com/git/tutorials/merging-vs-rebasing

**Stack exchange answer elaborating subtleties in git pull and git merge**: https://stackoverflow.com/questions/71768999/how-to-merge-when-you-get-error-hint-you-have-divergent-branches-and-need-to-s


Merge/rebase operations on remote branches are identical to local ones, except you call them as origin/main, origin/branch_name, etc.

# Other useful commands

`git tag` is an alternative to `git branch` that affixes a tag to a given commit: for example

```
git tag v1.4
```

Whereas `git branch` is a movable pointer, `git tag` is fixed to a commit. It's best used to label a stable version that you may want to revisit later. 

`git reflog`  shows the history of where refs (HEAD/branches/stash) have pointed, letting you recover “lost” commits no longer reachable after resets, rebases, or branch deletions. It is local-only and expires after time.

When you find out that your code has broken down after a long series of commit, you can use `git bisect` to perform a binary search in the history to find a particular commit. See [this](https://stackoverflow.com/questions/4713088/how-do-i-use-git-bisect) Stack Exchange for info.

