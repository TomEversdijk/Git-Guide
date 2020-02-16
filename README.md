# Git_Demo

After reading this tutorial you should understand the basic git commands. 

## What is git?
Git is a VCS (Version control system) which is used for two main purposes:
1. To store a back-up of your work in case something goes wrong.
2. To work with multiple developers on the same project without destroying others work.

## Installation
You start by [downloading](https://git-scm.com/downloads) and [installing](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) git for your operating system.

Verify that you've installed git correctly by open a command line and type the following command.
```bash
$ git --version
git version 2.24.1.windows.2
```

This command should return the installed git version as visible in the image below.
[git_version]

If you prefer using a graphical user interface (GUI), you can download any from this website:  
https://git-scm.com/downloads/guis

## New git repository
While on the command line you can navigate to the desired folder in order to initiate git and start keeping track of all your work. This folder has to be empty in order make it a git tracked folder. When navigated to the desired folder location, use the following commands to start git. This will create a hidden .git folder that will store git information. You can safely ignore this hidden .git folder.
```bash
$ git init
```

## Commit
Following the creation of the new git repository, we can start coding and save the code within this desired folder. After writing some lines of code, it is important to commit you changes. This makes a snapshot of your current work and when you made a mistake, you can reset your code to this exact snapshot. To make this snapshot you first have to define which files should be snapshotted by one of the following commands, this is called staging.
```bash
$ git add . # Adds all changed documents to the snapshot
$ git add <file-name> #Adds only the defined files to the snapshot
```
Finally the added files should be snapshotted with the following command. Every snapshot should have a commit message that describes the changes. This message is given by the  *-m* parameter. 

```bash
$ git commit -m "first commit"
```
After you've committed your changes, a message will display the number of changed files, deleted files and the inserted files. Besides this there will also be an unique git commit hash. This hash will be of great importance when we want to go back to this snapshot.

You can get an overview of the current status of your git project by typing the following command. 
```bash
$ git status
```
This will display the modified files, the staged file and the current branch you're working on. (Branches will be explained below)

## checkout
Besides getting an overview of the current status, it is useful the get some information about the status at previous snapshots. This can be retrieved with the following command. 
```bash
$ git log
```
This will display a complete list of all previous made changes on this branch. It will display the auther, the commit message and most important the git hash. 

In order to go back to a previous snapshot we have to use the checkout command together with the git hash as retrievable with the *git log* command. 
```bash
$ git checkout <git-hash> #e.g. $ git checkout da232268df22f3077ce8665ba16bc6efaf49c41f
```
After this command all files within the git folder should have been changed to their original state as they were when this commit was originally made.  
Going back to the last commit can be done in a similar fashion where the git hash should be replaced with master.
```bash
$ git checkout master
```

**Going back to a previous commit this way can be dangerous** and it is only adviced to do so when you want to visible see what you've done at this commit. This is because when you start to commit again from this point onwards, those new commits won't be saved on a branch. When you again checkout to you last commit with *git checkout master*, you wont be able to go back to the commits made from the previous point when you forgot the exact hash.

## Branches


## Fork

## .gitignore

## Github
Git and github are not the same. 
Git is a version control system that can be locally used.
Github on the other hand is a storage platform where you can upload and download your git work. 

## Push
git remote add origin https://github.com/KarelPeeters123/VHG-NER.git
git push -u origin master

## pull

# Cheat sheet
## Git
git log
## Github
## .gitignore


