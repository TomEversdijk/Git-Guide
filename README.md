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
Following the creation of the new git repository, we can start coding and save the code within this desired folder. After writing some lines of code, it is important to commit you changes. This makes a snapshot of your current work and when you made a mistake, you can rebase your code to this exact snapshot. To make this snapshot you first have to define which files should be snapshotted by one of the following commands.
```bash
$ git add . # Adds all changed documents to the snapshot
$ git add <file-name> #Adds only the defined file to the snapshot
```
Finally the added files should be snapshotted with the following command. Every snapshot should have a commit message that describes the changes. This message is given by the  *-m* parameter.

```bash
$ git commit -m "first commit"
```

## Rebase

## Branches

## Fork

## .gitignore

### Github
Git and github are not the same. 
Git is a version control system that can be locally used.
Github on the other hand is a storage platform where you can upload and download your git work. 

## Push
git remote add origin https://github.com/KarelPeeters123/VHG-NER.git
git push -u origin master

## pull

## Cheat sheet


