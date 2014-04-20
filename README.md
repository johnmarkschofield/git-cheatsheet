# Git Cheatsheet


## Introduction

by John Mark Schofield

jms@schof.org

http://schof.org

## Core Concepts

### The Three Places of Git
* __working area__ -- The visible directory where you edit files.
* __staging area__ -- Where files live once you "git add" them, but before you commit them. AKA __cached area__.
* __committed__ -- Not referred to as an area, but where files go when they are committed.


### Creating and Cloning Repos and Modifying the Working Directory
* __git init__ -- Turns a regular directory into a git working area (with a hidden .git repo).
* __git clone URL__ -- Clones a repo (from github, etc.) to a local git repo with a working area.
* __git checkout -- FILENAME__ -- Disgard changes to a file and revert it to the last version committed.

### Modifying the Staging Area
* __git add FILENAME__ -- Adds a file and its contents to the staging area.
* __git rm FILENAME__ -- Removes a file from the staging area and the working area. Use with "-f" option if the file in the working area has unstaged changes.
* __git rm --cached FILENAME__ -- Removes a file from the staging area, *while leaving it in the working area.*
* __git mv FILENAME1 FILENAME2__ -- Renames (moves) a file. Equivalent to __mv FILENAME1 FILENAME2 && git rm FILENAME1 && git add FILENAME2__.
* __git reset HEAD FILENAME__ -- If you've just staged a file, "reset HEAD" will unstage that file (the staged version is the same as in HEAD, the most recent commit).

### Modifying Committed Files
* __git commit__ -- Commits the state (contents, if they've been removed or updated, etc.) of files in the staging area.
* __git commit --amend__ -- Modifies the previous commit. Ex: "git commit -m 'initial commit' && git add forgotten_file && git commit --amend"

### Asking Git Questions
* __git status__ -- Lists changed files in staging and working areas, and which branch is in use in the working area.
* __git diff__ -- Displays a diff between files in the working area and files in the staging area.
* __git diff --cached__ -- Displays a diff between files in the staging area and committed files. AKA __git diff --staged__.
* __git log__ -- Prints metadata about git commits, newest on top.
* __git log -p__ -- Displays the diff introduced with each commit.
* __git log -p -2__ -- Same as above, but only two commits. Use --n for n commits.
* __git log --stat__ -- Displays stats for each commit: list of modified files, how many files were changed, and how many lines in those files were added and removed.
* __git log --oneline__ -- Git log output with less information so each commit fits on one line.
* __git log --pretty=[oneline|short|full|fuller]__ -- Git log output with different formatting and levels of detail.
* __git log --graph__ -- Show branch and merge history.
* 

### Working with Remotes
* __git remote__ -- Shows the remote servers configured for this repo.
* __git remote -v__ -- Shows you the remote servers and their urls.