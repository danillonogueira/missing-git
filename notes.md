# Missing Git
https://missing.csail.mit.edu/2020/version-control/

## Introduction

* Data model: Trees (directories), Blobs (files), Commits (snapshots);
* <b>Commits</b> are snapshots of the state of a project at a certain point. Each commit <b>points to</b> the previous one, is assigned a [SHA-1](https://en.wikipedia.org/wiki/SHA-1) hash once created and has to have a commit message.
* Before commiting and thus creating a snapshot, git has a <b>staging area</b> as an intermediate stage to the next commit. Files that will be part of the snapshot are added to the staging area and changes in them will constitue the commit.
* <b>Branches</b> are ramifications inside a git repository. They provide the possibility of making changes and doing experimental work without compromising the rest. The production state of a project is usually kept in a branch called <b>master</b> and independent work in development is handled inside other branches. Inserting new content into the master branch from other branches (or between branches themselves) is called <b>merging</b>.

## Commands summary

### Shows the current status of a branch:
```
$ git status
```

### Removes unstaged changes made to a file:
```
$ git checkout <file>
```
```
$ git restore <file>
```

### Adds a file to the staging area:
```
$ git add <file>
```

### Removes a file from the staging area:
```
$ git restore --staged <file>
```

### Commits changes from files added to the staging area:
```
$ git commit -m "<commit message>"
```

### Links local repository to a remote repository:
```
$ git remote add <name> <url>
```

### Pushes changes to the remote repository:
```
$ git push <name>
```

* Name might be omitted if there's only one remote repo added.

### Shows log of commits:
```
$ git log --oneline --decorate
```

### Moves HEAD to a previous commit keeping changes:
```
$ git reset HEAD~
```
* --soft will put changes in the staging area.

### Moves HEAD to a previous commit ERASING changes (caution):

```
$ git reset HEAD~ --hard
```

* This is not a good practice in Git and can be seen as coming back in time. Since the usage of reset in general modifies the history of the repository, pushing content like this might require the --force attribute.

### Moves HEAD to a commit:
```
$ git reset <commit>
```

  * Attributes can be passed as usual.

### Creates a new branch from current branch:
```
$ git branch <name>
```

### Creates a new branch from current branch and moves (HEAD) to it:
```
$ git checkout -b <name>
```

### Moves (HEAD) to other commit/branch:
```
$ git checkout <commit hash/branch name>
```

### Shows differences between two commits, files or branches.

```
$ git diff <commit/file/branch> <commit/file/branch>
```

* The first argument is the one that changes are being compared from;
* If no argument is supplied, compares current changes from HEAD.
* It is also possible to pass the name of a file as a third argument.

### Merges changes from a branch into HEAD since that diverged from it:

```
$ git merge <branch>
```

* Git's merge function works in a way that, while attempting a merge from branch 1 into branch 2, it will try to ignore changes made to branch 2 since branch 1 last pointed to branch 2. This is called <b>fast-forwarding</b>.
* `git merge --abort` can be used to abort a merge in case of conflicts;
* `git merge --continue` can be used to proceed with a merge after staging changes that solved reported conflicts.
