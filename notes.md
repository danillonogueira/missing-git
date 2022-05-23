# Missing Git
https://missing.csail.mit.edu/2020/version-control/

## Introduction

* Data model: Trees (directories), Blobs (files), Commits (snapshots);
* <b>Commits</b> are snapshots of the state of a project at a certain point. Each commit <b>points to</b> the previous one and every commit has to have a commit message.
* <b>Branches</b> are ramifications inside a git repository. They provide the possibility of making changes and doing experimental work without compromising the rest. The production state of a project is usually kept in a branch called <b>master</b> and independent work in development is handled inside other branches. Inserting new content into the master branch from other branches (or between branches themselves) is called <b>merging</b>.
* Before commiting and thus creating a snapshot, git has a <b>staging area</b> as an intermediate stage to the next commit. Files that will be part of the snapshot are added to the staging area and changes in them will constitue the commit.

## Commands

Shows the current status of a branch:
```
$ git status
```

Adds a file to the staging area:
```
$ git add <file name>
```

Commits changes from files in the staging area:
```
$ git commit -m "<commit message>"
```

Shows log of commits:
```
# git log --oneline --decorate
```

Creates a branch:
```
$ git branch <name>
```

Creates a new branch and moves (HEAD) to it:
```
$ git checkout -b <name>
```

Moves (HEAD) to other commit/branch:
```
$ git checkout <commit hash/branch name>
```