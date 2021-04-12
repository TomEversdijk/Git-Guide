# Git Guide

After reading this tutorial you should understand the basic git commands. 

## Git
### What is git?
Git is a VCS (Version Control System) which is used for two main purposes:
1. To store a back-up of your work in case something goes wrong.
2. To work with multiple developers on the same project without destroying others work.

### Installation
You start by [downloading](https://git-scm.com/downloads) and [installing](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) git for your operating system.

Verify that you've installed git correctly by open a command line and type the following command.
```bash
$ git --version
```

This command should return the installed git version.

If you prefer using a graphical user interface (GUI), you can download one from [this website](https://git-scm.com/downloads/guis).

### New git repository
While on the command line you can navigate to the desired folder in order to initiate git and start keeping track of all your changes. After navigating to the desired folder location, use the following command to start git. This will create a hidden .git folder which will store all git information. You can safely ignore this hidden .git folder.
```bash
$ git init
```

### Commit
Following the creation of the new git repository, we can start coding and save the code within the above mentioned folder. After writing some lines of code, it is important to commit you changes. This will make a snapshot of your current work and when you make a mistake, you can reset your code to this snapshot. To make a snapshot you first have to define which files should be snapshotted by one of the following commands, this is called staging.
```bash
$ git add . # Adds all changed documents to the snapshot
$ git add <file-name> #Adds only the defined files to the snapshot
```
Finally the staged files should be snapshotted with the following command. Every snapshot should have a commit message that describes the changes. This message is given by the  `-m` parameter. 

```bash
$ git commit -m "<commit-message>"
```
After you've committed your changes, a message will display the number of changed files, deleted files and the inserted files. Besides this there will also be an unique git commit hash. This hash will be of great importance when you want to go back to this snapshot.

If you aren't ready to commit yet, but want an overview of the current status of your git project, you can do so by typing the following command. 
```bash
$ git status
```
This will display the modified files, the staged file and the current branch you're working on. (Branches will be explained below)

### checkout
Besides getting an overview of the current status, it is useful the get some information about the status of previous snapshots. This can be retrieved with the following command. 
```bash
$ git log
```
This will display a complete list of all previous changes on this branch. It will display the author, the commit message and most important the git hash. 

In order to go back to a previous snapshot you have to use the checkout command together with the git hash as retrievable with the `git log` command. 
```bash
$ git checkout <git-hash> #e.g. $ git checkout da232268df22f3077ce8665ba16bc6efaf49c41f
```
After this command all files within the git folder should have been changed to their original state as they were when this snapshot was originally made.  
Going back to the last commit can be done in a similar way where the git hash should be replaced with master.
```bash
$ git checkout master
```

**Going back to a previous commit by entering a git hash can be dangerous** and it is only adviced to do so when you want to visibly see what you've done at this commit. This is because when you start to commit again from this point onwards, the new commits won't be saved on a branch. When you again checkout to you last commit with `git checkout master`, you wont be able to go back to the commits made from the previous point when you forgot the exact hash.

### Branches
A branch is used during development to develop seperate parts of a program independendly from eachother. When a certain part of your code is working, you can chose to merge the branches together meaning that code from branch A will be included in branch B. This can be extremely useful if you need to have a consistenly working application. For example say we have a branch called deployment which contains only working code and another branch called development. During development of the code we only work on the development branch, or even on another branch created from the development branch. When the new update is fully working, we can merge the development branch into the deployment branch keeping only working and finished parts in the deployment branch. 

Creating a branch is done with the `branch` command or with the same `checkout` command as going back to a previous snapshot. Using the `checkout` command with the `-b` makes a new branch from the current snapshot and is safe to use. You can also make a branch starting from a previous commit by first going to a specific commit using the git hash followed by creating a branch with the command below.
```bash
#Both commands are equivallent
$ git branch <branch-name> #Branch from the current state
$ git checkout <git-hash> -b <branch-name> #Branch from the state with corresponding git-hash.
```

If you want to show an overview of all branches you can use the following command without any branch name. 
```bash
$ git branch
```
If you try this command yourself you see that the result will show a branch called master. This is the main branch and in previous chapter we actually used this to go to the latest commit on the master branch.  

You can delete a branch with the following command.
```bash
$ git branch -d <branch-name> #Safe delete: only possible if the branch is fully merged
$ git branch -D <branch-name> #Unsafe delete: Always possible
```

Merging branches can be a bit tricky because you have to be careful which branch you merge into which branch. Retaking the previous example of a deployment and development branch. First you go to the deployment branch because this branch has to include code from another branch, namely the development branch. Then you use the following command to include code from the development branch into deployment branch.

```bash
$ git checkout <branch-name>  #$ git checkout deployment
$ git merge <branch-name>     #$ git merge development
```
This command will fail if changes were made and committed in both the development and the deployment branch and those changes cannot be resolved automatically. If this occures you are obligated to go to your source code. The source code will contain some new lines with `<<<<<<< HEAD`, `=======` and `>>>>>>>`. This is the place where the conlict occurces and you have to manually remove the wrong code. After resolving the conlicts you have to make a new commit and the merge will finish successfully. 


### .gitignore
Sometimes you dont want to keep track of all the files in your project. (e.g: files containing sensitive information or passwords) This can be done by creating a .gitignore file which contains information about the files that should **not** be tracked. 
Some useful .gitignore patterns are shown below:
| Pattern  | explanation |
| ------------- | ------------- |
| \*\*/foo   | Don't track the folder foo anywhere in the structure |
| \*.foo  | Don't track files with extention .foo |
| \foo.foo  | Don't track the file foo with extention .foo in the root folder |
| fo?.foo  | A questionmark marks exactly one character |
| foo[1-3].foo  | square brackets match any character |

It is important to include files in the .gitignore before your first commit after creating this file. If you create a file, make a commit and after commiting changes the .gitignore, the newly created file will still be tracked in subsequent commits.

## Github
Git and github are not the same. 
Git is a version control system that can be locally used while Github on the other hand is an online storage platform where you can upload and download your git work. This can be extremely useful if you are working with others on the same project or in case you want to share your final code with others. 

In order to link your local repository with the remote repository you have to add the online repository url in the following command. This url will be saved in the .git folder and will be used whenever you want to upload or download your progress online.
```bash
$ git remote add origin <remote-git-repository-url>.git
```

### Push
Pushing means that you want your local git repository to be uploaded onto the remote repository. The first time you do this you have to specify which remote repository you want to use by the following command.
```bash
$ git push -u origin master
```
After the upstream is determined, you dont have to specify it every time and you can just use the following command to upload your code.
```bash
$ git push
```

### pull
Pulling is the opposite from pushing, meaning that you are downloading code from the remote repository onto the local repository. This is not usefull if you are developing as a single developer using a single desktop. But if you are working with multiple developers at the same time, some developers have already pushed new code that needs te be pulled before you can push your newly written code onto the branch.
```bash
$ git pull
```

### Clone 
On Github some repositories are publically accessable, just like this repository is publically available. This means that any user can download the repository. You can either download this repository as a zip file using the github gui or you can use the command line to clone the repository into the desired location. The clone command can also be used to make a local copy of another local repository at a different location. Meaning that with clone you can download repositories from online or move local repositories.
```bash
$ git clone <remote-git-repository-url> #download remote repository
$ git clone <local-git-path> #Copy local repository
```

## Cheat sheet

### Git
```bash
$ git --version #Displays the installed git version on this machine
$ git init    #Initialize a new git repository. Can only start from an empty folder.
$ git add . # Stage all changed documents 
$ git add <file-name> #Stage only the defined files
$ git commit -m "<commit-message>" #Commit the staged files
$ git status  #Displays the status of the current commit, including branch, modified files, staged files
$ git log     #Displays a complete list of previous commits with hash, author details and commit message
$ git checkout <git-hash> #Retrieve your work at the given git-hash
$ git checkout master #Retrieve your work at the latest commit on the master branch
$ git branch <branch-name> #Create a new branch with name <branch-name>
$ git checkout -b <branch-name> #Create a new branch with name <branch-name>
$ git branch #Display all branches by name
$ git branch -d <branch-name> #Safe delete branch: only possible if the branch is fully merged
$ git branch -D <branch-name> #Unsafe delete branch: Always possible
$ git merge <branch-name> #Merge the named branch into the current branch. Possibly resulting in conflicts.
```
### Github
```bash
$ git remote add origin <remote-git-repository-url>.git # Save the remote git url as variable name origin
$ git push -u origin master #Explicitly push your git commits to the remote git url with variable name origin, only obligated the with the first push
$ git push #Push your git commits to the remote git url with previous defined origin
$ git pull #Pull git commits from the remote git url with previous defined origin
$ git clone <remote-git-repository-url> #download remote repository
$ git clone <local-git-path> #Copy local repository

```
### .gitignore
| Pattern  | explanation |
| ------------- | ------------- |
| \*\*/foo   | Don't track the folder foo anywhere in the structure |
| \*.foo  | Don't track files with extention .foo |
| \foo.foo  | Don't track the file foo with extention .foo in the root folder |
| fo?.foo  | A questionmark marks exactly one character |
| foo[1-3].foo  | square brackets match any character |



