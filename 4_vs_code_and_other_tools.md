# Git and IDEs

In practice, a lot of developers use a combination of terminals, integradted development environment (IDE) and other specialized tools with git and other VCS (see [survey](https://www.jetbrains.com/lp/devecosystem-2023/team-tools/)). While using git from the terminal is the simplest method to set up, allows mouse-free control, gives you the widest range of operations, etc, it's oftentimes tedious (as you need to remember every command and option) and hard to visualize changes (just try calling git diff on a Jupyter notebook). Third-party can offer convenience, a GUI and make the experience easier, expecially if you're already using an IDE or editor with innate Git integration. Here, I'll cover Visual Studio Code (VS Code) as an example of IDE with git integration, to offer a sense of how this works.

# Using Git in VS code

VS Code is the [most commonly used code editor by software developers](https://survey.stackoverflow.co/2024/technology#1-integrated-development-environment), with many functionalities that can be useful for code development. One of its many features is integration with source control, including with git. A lot of the previous commands can be replicated with it. In fact, if you launch VS Code at the directory you were just working on, you should be able to see its history, commits, and what each commit changes in each document. You can also checkout to one particular commit. From personal experience, I can perform version control on Visual Studio Code most of the time without worrying about Git syntax at all.

The workshop below would show you the interface for creating files and using version control on them. For the sake of time, I won't cover how to actually run scripts or jupyter notebooks. Sometimes, VS code's source control functionalities would fail at more complicated commands (e.g. if your local and remote repositories are out of sync). In this case, you'll need to fall back to git control using terminal (and VS code comes with a convenient terminal interface as well). 

# Interface in VS Code

Once you launch VS Code, you need to launch a folder as a workspace. Create a new folder named workdir_vscode in your desired repository and open it.

<img width="1918" height="1017" alt="Screenshot 2025-10-06 at 17 04 39" src="https://github.com/user-attachments/assets/7f1e41ee-72c8-4b47-a3ca-0e14c664cfec" />

This folder would be empty. Let's create a new file. Make sure you are on the explorer tab (should be the first button on the activity bar to the left). Then, click on the button to the right of the folder name 

<img width="1913" height="994" alt="Screenshot 2025-10-06 at 17 06 27" src="https://github.com/user-attachments/assets/cd1a0685-f831-4e5b-8369-75237382bd63" />

Write something in the text file you created. The interface should now look like

<img width="1917" height="991" alt="Screenshot 2025-10-06 at 17 08 20" src="https://github.com/user-attachments/assets/5fc87254-ba01-4e78-ba7c-87ce98cbe5b0" />


# Using Git via VS Code

To use version control, you need to click the source control panel on the activity bar:

<img width="326" height="937" alt="Screenshot 2025-10-06 at 17 10 49" src="https://github.com/user-attachments/assets/61162156-43d4-4f32-b7db-ad7724f270a9" />

Clicking "Initialize Repository" should initialize the repository! Now, you can see the name of the repository and the list of changes made. It has a convenient panel for you to commit.

<img width="322" height="939" alt="Screenshot 2025-10-06 at 17 11 57" src="https://github.com/user-attachments/assets/5c57d517-4a14-4aab-a6e7-f58f7fb00b33" />

Here, I've created a couple more files. Right-clicking any files on the staging area would allow you to perform most other commands discussed before:

<img width="1918" height="991" alt="Screenshot 2025-10-06 at 17 13 33" src="https://github.com/user-attachments/assets/a40faeb4-9f7e-4c4c-9187-5ce93189964d" />

Here, I've make a couple other commits. You can see the commits on the commit graph below. Right-clicking on any of the commits would allow you to checkout to them at a detached HEAD state, create a new branch at them, etc.  

<img width="1916" height="993" alt="Screenshot 2025-10-06 at 17 15 47" src="https://github.com/user-attachments/assets/9e93f971-128d-48ef-996c-1bb7da29cc5b" />

Further, clicking a file in a commit shows a nice comparison of the changes you made in any given commit.

<img width="1918" height="963" alt="Screenshot 2025-10-06 at 17 17 54" src="https://github.com/user-attachments/assets/3e76971f-1734-4653-9048-2df692df0e35" />


Note: the innate git track history works wonderfully for small projects. For larger group projects with 15 collaborators, 10 branches and 5 commits a day, however, it tends to get bloated with histories not of your interest. In this case, one might want to fall back to command line or other tools.


# Remote control with VS Code

Clicking "Publich Branch" allows you to publish your branch to a connected GitHub account, assuming you have one set up.

<img width="1920" height="992" alt="Screenshot 2025-10-06 at 17 16 53" src="https://github.com/user-attachments/assets/475219ef-93b5-452c-8e5d-b1d5cef2f3d2" />

Now, if you created a new coommit, you can push the commit to remote origin in this panel:

<img width="1920" height="1000" alt="Screenshot 2025-10-06 at 17 19 17" src="https://github.com/user-attachments/assets/7460e21a-f0d7-41c6-a8c9-d7c6fbd7b793" />


# Other useful tools


Here are other tools that I personally have no experience with but heard good things from other git users:

- [Difftastic](https://github.com/Wilfred/difftastic): a command-line tool for comparing files based on syntax. Whereas git diff highlights every single change made, including formatting changes as simple as an extra space bar, difftastic understands nesting, alighmet and line-wrapping, allowing you to focus only on the meaningful changes.
- [Sublime Merge](https://www.sublimemerge.com): a git client with a nice GUI, line-by-line and hunk staging, syntax highlighting for commit, and commit searching. Works with its own text editor [Sublime Text](https://www.sublimetext.com) and can be a good option for users not interested in an IDE.
