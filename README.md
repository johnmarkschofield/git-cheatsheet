# Git Cheatsheet


## Introduction

### About the Author

by John Mark Schofield

jms@schof.org

http://schof.org


### Thanks

This cheatsheet is based on the ["Pro Git" book by Scott Chacon](http://git-scm.com/book).

In addition, I owe a debt to the Git class I took from Peter Bell ([GitHub](https://github.com/PeterBell) / [Twitter](https://twitter.com/peterbell)).

## Core Concepts

### The Three Places of Git

* __working area__ -- The visible directory where you edit files. AKA __Working Directory__.
* __staging area__ -- Where files go once you "git add" them, but before you commit them. AKA __cached area__, AKA __index__.
* __history__ -- Where files go when they are committed. AKA __committed area__.


### Writing Meaningful Commit Messages

Take the time to break changes up into separate, atomic commits. Each commit should be a unit of work.

Write meaningful commit messages. You should use commits to tell a story. We can see what files changed by looking at the commit; we don't need that in the commit message. Each commit should tell WHY you made the change. 


## Configuring Git

It's safe (and a good idea) to do all of these configuration steps on your computer. Once you've done that, you can move your ~/.gitconfig around by hand -- you don't have to re-enter the config every time.

### Identity
```
git config --global user.name
# Displays your username

git config --global user.name "Foobar Tweedly"
# Sets username

git config --global user.email
# Displays email

git config --global user.email foorbar@tweedly.com
# Sets email

git config --global credential.helper osxkeychain
# If this fails, read https://help.github.com/articles/set-up-git
```


### Cross Platform Operation

```
# On Mac and Linux:
git config --global core.autocrlf input

# On windows:
git config --global core.autocrlf true
```


### Making Git Behave better

Making git pretty:
```
git config --global color.ui true
```

Making git concise:
```
git config --global alias.hist "log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short"
git config --global alias.type "cat-file -t"
git config --global alias.dump "cat-file -p"
git config --global alias.lg "log --oneline --decorate --graph --all"
git config --global alias.p "pull --rebase"

git config --global push.default simple
```

Making git safe:
```
git config --global branch.autosetuprebase always
git config --global branch.*branch-name*.rebase true

git config --global merge.ff false
```


## Operations

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