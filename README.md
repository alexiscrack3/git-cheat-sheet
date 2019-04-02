# Git Cheat Sheet

A collection of some of the most useful Git commands

## Table of Contents

1. [Settings](#settings)
    * [Setting Configs](#setting-configs)
    * [Getting Configs](#getting-configs)
    * [Removing Configs](#removing-configs)
2. [Aliases](#aliases)
3. [Setting Up Repository](#setting-up-repository)
    * [Initializing Repository](#initializing-repository)
    * [Initializing Shared Repository](#initializing-shared-repository)
    * [Cloning Repository](#cloning-repository)
4. [Saving Changes](#saving-changes)
    * [Adding Files](#adding-files)
        * [Tracking New or Modified Files](#tracking-new-or-modified-files)
        * [Interactive Staging](#interactive-staging)
    * [Removing Files](#removing-files)
    * [Renaming Files](#renaming-files)
    * [Committing Files](#committing-files)
    * [Stashing Files](#stashing-files)
5. [Inspecting Changes](#inspecting-changes)
    * [Display State](#display-state)
    * [Display Objects](#display-objects)
    * [Logging](#logging)
    * [Display Differences](#display-differences)
    * [Blaming](#blaming)
6. [Listing Files](#listing-files)
7. [Undoing Changes](#undoing-changes)
    * [Reverting Files](#reverting-files)
    * [Reverting Commit](#reverting-commit)
    * [Unstaging Staged File](#unstaging-staged-file)
    * [Resetting Current Commit](#resetting-current-commit)
    * [Removing Untracked Files](#removing-untracked-files)
8. [Rewriting History](#rewriting-history)
    * [Fix Up Commit](#fix-up-commit)
    * [Rebase Commits](#rebase-commits)
    * [Copy Commits](#copy-commits)
9. [Synchronize](#synchronize)
    * [Remotes](#remotes)
    * [Fetching](#fetching)
    * [Pulling](#pulling)
    * [Pushing](#pushing)
10. [Branches](#branches)
    * [Create Branches](#create-branches)
    * [Rename Branches](#rename-branches)
    * [Delete Branches](#delete-branches)
    * [List Branches](#list-branches)
    * [Merge Branches](#merge-branches)
    * [Track Branches](#track-branches)
    * [Switch to Branch](#switch-to-branch)
11. [Debugging](#debugging)
    * [Binary Search](#binary-search)
12. [Tagging](#tagging)
13. [Submodules](#submodules)
14. [Refs and the Reflog](#refs-and-the-reflog)
    * [Hashes](#hashes)
    * [Refs](#refs)
    * [Special Refs](#special-refs)
    * [Relative Refs](#relative-refs)
    * [Reflog](#reflog)
15. [Others](#others)
16. [Getting Help](#getting-help)

## Settings

There are 3 configuration levels:

* User-specific settings. Options set with the --global flag are stored in ~/.gitconfig
* Repository-specific settings. Options set with or without the --local flag are stored in \<repo\>/.git/config
* System-wide settings. Options set with the --system flag are stored in $(prefix)/etc/gitconfig

### Setting Configs

Set username.

```bash
git config [<config-level>] user.name "<name>"
```

Set email.

```bash
git config [<config-level>] user.email "<email>"
```

A boolean to make git-clean do nothing unless given -f, -i or -n. Possible values: true, false

```bash
git config [<config-level>] clean.requireForce <value>
```

Turn on/off all Git’s colored terminal output. Possible values: true, false, auto.

```bash
git config [<config-level>] color.ui <value>
```

Set up default text editor.

```bash
git config [<config-level>] core.editor <editor>
```

Makes git case sensitive. Possible values: true, false.

```bash
git config [<config-level>] core.ignorecase <value>
```

Sets a diff algorithm. Possible values: default, histogram, minimal, myers, patience.

```bash
git config [<config-level>] diff.algorithm <value>
```

Specify the style in which conflicted hunks are written out to working tree files upon merge. The default is "merge", which shows a <<<<<<< conflict marker, changes made by one side, a ======= marker, changes made by the other side, and then a >>>>>>> marker. An alternate style, "diff3", adds a ||||||| marker and the original text before the ======= marker.

```bash
git config [<config-level>] merge.conflictstyle <style>
```

Set up your custom merge resolution and diff tools.

```bash
git config [<config-level>] merge.tool <editor>
```

Defines the action git push should take. Possible values: nothing, matching, upstream, current, simple (safest option and is well-suited for beginners).

```bash
git config [<config-level>] push.default <value>
```

When set to true, automatically create a temporary stash entry before the operation begins, and apply it after the operation ends. Possible values: true, false.

```bash
git config [<config-level>] rebase.autostash <value>
```

Show full by default diff when using git stash show. Possible values: true, false.

```bash
git config [<config-level>] stash.showPatch <value>
```

Open the configuration file in a text editor for manual editing.

```bash
git config [<config-level> --edit
```

### Getting Configs

List all variables set in config file, along with their values.

```bash
git config [<config-level>] -l
                            --list
```

Get username.

```bash
git config [<config-level>] [--get] user.name
```

Get email.

```bash
git config [<config-level>] [--get] user.email
```

### Removing Configs

Remove username.

```bash
git config [<config-level>] --unset user.name
```

Remove email.

```bash
git config [<config-level>] --unset user.email
```

## Aliases

Create an alias for git commands.

```bash
git config [<config-level>] alias.<alias> '<command>'
```

## Setting Up Repository

### Initializing Repository

Create empty git repository or re-initialize an existing one.

```bash
git init
```

Create empty git repository in directory

```bash
git init <directory>
```

Create empty git repository and apply template.

```bash
git init --template=<template-path> <repository>
```

### Initializing Shared Repository

Create a repository that doesn’t have a working directory, making it impossible to edit files and commit changes in that repository.

```bash
git init --bare
```

### Cloning Repository

Clone repository in the current directory.

```bash
git clone <repository>
```

Clone repository into directory.

```bash
git clone <repository> <directory>
```

Clone repository and set remote name.

```bash
git clone --origin <new-remote-name> <repository>
```

Clone repository and point HEAD to the given branch.

```bash
git clone -b <branch> <repository>
          --branch
```

Clone only history leading up to the main branch or the one specified by -b

```bash
git clone -b <branch> --single-branch <repository>
```

Clone repository and all its submodules recursively.

```bash
git clone --recursive <repository>
```

Clone the repository and apply template.

```bash
git clone --template=<template-path> <repository>
```

Clone the repository and only clone the history of commits specified by the option depth. In this example a clone of the repository is made and only the most recent commit is included.

```bash
git clone -depth=1 <repository>
```

## Saving Changes

### Adding Files

#### Tracking New or Modified Files

Add all files.

```bash
git add .
```

Add a specific file.

```bash
git add <file>

```

Add a specific directory.

```bash
git add <directory>
```

Add files with an extension file.

```bash
git add *.<extension>
```

Allow adding otherwise ignored files.

```bash
git add -f <file>
        --force
```

Do not actually add files; only show which ones would be added.

```bash
git add -n
        --dry-run
```

Add to index modified and deleted tracked files but it will never stage new files.

```bash
git add -u
        --update
```

Begin an interactive staging session that lets you choose portions of a file to add to the next commit.

```bash
git add -p
        --patch
# y - stage this hunk
# n - do not stage this hunk
# q - quit; do not stage this hunk nor any of the remaining ones
# a - stage this hunk and all later hunks in the file
# d - do not stage this hunk nor any of the later hunks in the file
# g - select a hunk to go to
# / - search for a hunk matching the given regex
# j - leave this hunk undecided, see next undecided hunk
# J - leave this hunk undecided, see next hunk
# k - leave this hunk undecided, see previous undecided hunk
# K - leave this hunk undecided, see previous hunk
# s - split the current hunk into smaller hunks
# e - manually edit the current hunk
# ? - print help
```

Add modified files to index.

```bash
git add $(git ls-files --modified)
```

#### Interactive Staging

Staging only untracked files.

```bash
git add -i
        --interactive
#   Type a (for "add untracked")
#   Then * (for "all")
#   Then q (to quit)
```

### Removing Files

Remove file from the working directory.

```bash
git rm <file>
```

Remove recursively directory from the working directory.

```bash
git rm -r <directory>
```

Remove a file from index but not from disk.

```bash
git rm --cached <file>
```

Remove recursively a directory from index but not from disk.

```bash
git rm --cached -r <directory>
```

Remove files from the working directory.

```bash
git rm $(git ls-files --deleted)
```

Do not actually remove the files, just show if they exist in the index.

```bash
git rm -n
       --dry-run
```

### Renaming Files

First way.

```bash
mv <old-name> <new-name>
git rm <old-name>
git add <new-name>
```

Second way.

```bash
git mv <file-from> <file-to>
```

### Committing Files

Use the given message as the commit message.

```bash
git commit -m "<message>"
            --message
```

Use the given message as the commit message and override the author name used in the commit.

```bash
git commit -m "<message>" --author="Name <your_email@youremail.com>"
```

Stage all modified and deleted paths, but new files you have not told git about are not affected.

```bash
git commit -a
           --all
```

Stage all modified and deleted path using the given message, but new files you have not told git about are not affected.

```bash
git commit -am "<message>"
```

Allow recording an empty commit with no file changes.

```bash
git commit --allow-empty -m "<message>"
```

Show unified diff of all file changes.

```bash
git commit -v
           --verbose
```

Show list of paths that are to be commited or not, and any untracked.

```bash
git commit --dry-run --short
```

Skip staging area and commit files, this only works with tracked files.

```bash
git commit --only <file>
```

### Stashing Files

Stash away changes to dirty working directory.

```bash
git stash
```

Interactively select hunks from diff between HEAD and working directory to stash.

```bash
git stash -p
          --patch
```

Stash only unstaged changes.

```bash
git stash -k
```

Save local changes including untracked files.

```bash
git stash save -u
               --include-untracked
```

All changes already added to the index are left intact.

```bash
git stash --keep-index
```

All changes already added to the index are undone.

```bash
git stash --no-keep-index
```

Save local changes to a new stash with message.

```bash
git stash save "<message>"
```

List the stashes stored in the stack.

```bash
git stash list
```

Apply the changes recorded in the stash.

```bash
git stash apply stash@{n}
```

Remove and apply a single stashed state from the stack.

```bash
git stash pop
```

Show the changes recorder in the latest stash as a diff.

```bash
git stash show
```

Show the changes recorded in the stash as a diff.

```bash
git stash show stash@{n}
```

Show the changes recorded in the stash as a diff in patch format.

```bash
git stash show -p stash@{n}
               --patch
```

Creates and checks out a new branch named starting from the commit at which the latest stash was originally created, applies the changes recorded in stash to the new working tree and index. If that succeeds, then drops the latest stash.

```bash
git stash branch <name>
```

Creates and checks out a new branch named starting from the commit at which the stash was originally created, applies the changes recorded in stash to the new working tree and index. If that succeeds, then drops the stash.

```bash
git stash branch <name> stash@{n}
```

Remove a single stashed state from the stack.

```bash
git stash drop stash@{n}
```

Remove all the stashed states.

```bash
git stash clear
```

## Inspecting Changes

### Display State

Show working directory status.

```bash
git status
```

Output in short format.

```bash
git status -s
           --short
```

Status of ignored files.

```bash
git status --ignored
```

### Display Objects

Show details of the most recent commit.

```bash
git show
```

Show details of the most recent commit.

```bash
git show HEAD
```

Show details of the object (blobs, trees, tags and commits).

```bash
git show <object>
```

Ignore white space when comparing lines.

```bash
git show <object> -w
                  --ignore-all-space
```

Show only names of changed files without the diffs.

```bash
git show --name-only <object>
```

Show only names and status of changed files without the diffs.

```bash
git show --name-status <object>
```

Generate diffstat instead of patch.

```bash
git show --stat
```

Show details of an object with pretty format.

```bash
git show --format="<format>" <object>
         --pretty
```

Show details of commit via commit message pattern matching.

```bash
git show :/<commit>
```

Show details of a file on a object.

```bash
git show <object>:<file>
```

Export file to path.

```bash
git show <branch>:<file> > <path>
```

Show branches and their commits.

```bash
git show-branch
```

### Logging

Show all commits.

```bash
git log
```

Show changes over time for a specific file.

```bash
git log <file>
```

Generate diff in patch format for a specific file.

```bash
git log -p <file>
        --patch
```

Show changes over time for a specific file even if the file was renamed.

```bash
git log --follow <file>
```

Exports git log to text file.

```bash
git log > <file>
```

Show only commits that occur in the range.

```bash
git log <since>..<until>
```

Maximum number of commits to display.

```bash
git log -n
        --max-count
```

Condense each commit to a single line.

```bash
git log --oneline
```

Get a list of commits made in the last two weeks.

```bash
git log --since='2 weeks'
```

Show statistics for files modified in each commit.

```bash
git log --stat
```

Display only the changed/insertions/deletions line from the --stat command.

```bash
git log --shortstat
```

Generate condensed summary of extended header information.

```bash
git log --summary
```

Search for commits by a particular author. The argument can be a plain string or a regular expression.

```bash
git log --author="<pattern>"
```

Search for commits with a commit message. The argument can be a plain string or a regular expression.

```bash
git log --grep="<pattern>"
```

Display commits without merge commits.

```bash
git log --no-merges
```

Dsplay only merge commits.

```bash
git log --merges
```

Show what every contributor has been getting up to across all branches.

```bash
git log --all --oneline --no-merges
```

Show changes since two weeks.

```bash
git log --no-merges --raw --since='2 weeks ago'
```

Generate a Changelog.

```bash
git log --oneline --no-merges <last tag>..HEAD
```

Check which changes you’re about to pull.

```bash
git log --oneline --no-merges HEAD..<remote>/<branch>
```

Review what you’re about to push.

```bash
git log --oneline --no-merges <remote>/<branch>..HEAD
```

View complex logs.

```bash
git log --graph --all --decorate --stat --date=iso
```

Summarize commits of current branch.

```bash
git shortlog
```

Summarize commits of all refs.

```bash
git shortlog --all
```

Summarize commits and supress the ones with more than one parent (merge commits).

```bash
git shortlog --no-merges
```

Summarize commits and suppress commit message.

```bash
git shortlog -s
             --summary
```

Sort according to number of commits.

```bash
git shortlog -n
             --numbered
```

Number of commits of each contributor.

```bash
git shortlog -sn
```

Number of commits of each contributor and ensures that merge commits aren’t being counted.

```bash
git shortlog -sn --all --no-merges
```

### Display Differences

What's different from our most recent commit (staged and unstaged changes).

```bash
git diff
```

Ignore white space when comparing lines.

```bash
git diff -w
         --ignore-all-space
```

What's different from our most recent commit (staged and unstaged changes).

```bash
git diff HEAD
```

What's different from our previous commit.

```bash
git diff HEAD~
         HEAD~1
```

What's different from two previous commits.

```bash
git diff HEAD~2
```

Show staged changes against your HEAD.

```bash
git diff --cached
         --staged
```

Show changes between commits.

```bash
git diff <commit> <commit>
```

Show changes in file between commits.

```bash
git diff <commit> <commit> <file>
```

Show inline word diff.

```bash
git diff --word-diff
```

Look for differences whose added or removed line matches the given pattern.

```bash
git diff -G <pattern>
```

Print out changes.

```bash
git diff > <file>
```

### Blaming

Show what revision and author last modified each line of a file.

```bash
git blame <file>
```

Show the authors email address instead of username.

```bash
git blame -e <file>
```

Ignore whitespace changes. If a previous author has modified the spacing of a file by switching from tabs to spaces or adding new lines this, unfortunately, obscures the output of git blame by showing these changes.

```bash
git blame -w <file>
```

Detect moved or copied lines within in the same file. This will report the original author of the lines instead of the last author that moved or copied the lines.

```bash
git blame -M <file>
```

Detect lines that were moved or copied from other files. This will report the original author of the lines instead of the last author that moved or copied the lines.

```bash
git blame -C <file>
```

Restrict the output to the requested line range.

```bash
git blame -L <starting-line>,<ending-line> <file>
```

## Listing Files

Show information about files in the index and the working directory.

```bash
git ls-files
```

Show cached files.

```bash
git ls-files -c
             --cached
```

Show staged contents (mode bits, object name and stage number).

```bash
git ls-files -s
             --stage
```

Show modified files.

```bash
git ls-files -m
             --modified
```

Show deleted files.

```bash
git ls-files -d
             --deleted
```

This option identifies the file status with the following tags.

```bash
git ls-files -t
# H - cached
# S - skip-worktree
# M - unmerged
# R - removed/deleted
# C - modified/changed
# K - to be killed
# ? - other
```

Similar to -t, but use lowercase letters for files that are marked as assume unchanged.

```bash
git ls-files -v
```

Show only ignored files in the output. When showing files in the index, print only those matched by an exclude pattern. When showing "other" files, show only those matched by an exclude pattern.

```bash
git ls-files -i
             --ignored
```

Show all untracked or ignored files.

```bash
git ls-files -o
             --others
```

Show all untracked files.

```bash
git ls-files --others --exclude-standard
```

Show all ignored files.

```bash
git ls-files --others --ignored --exclude-standard
```

## Undoing Changes

### Reverting Files

Return the state of your unstaged files as they were in your last commit.

```bash
git checkout .
```

Return the state of your unstaged files as they were in your HEAD (last commit).

```bash
git checkout HEAD
```

Return the state of your unstaged files that match the regular expression as they were in your last commit.

```bash
git checkout \*.txt
```

Return the state of your file as it was in your last commit.

```bash
git checkout <file>
```

Return the state of your file as it was in your last commit. Use two consecutive hyphens if file and branch have the same name.

```bash
git checkout -- <file>
```

This turns the file that resides in the working directory into an exact copy of the one from commit and adds it to the staging area.

```bash
git checkout <commit> <file>
```

This turns the file that resides in the working directory into an exact copy of the one from stash@{n} and adds it to the staging area.

```bash
git checkout stash@{n} <file>
```

Update all files in the working directory to match the specified commit. This will put you in a detached HEAD state.

```bash
git checkout <commit> .
```

Interactively select hunks in diff.

```bash
git checkout -p
             --patch
```

Interactively select hunks in diff for a specific file.

```bash
git checkout -p <file>
             --patch
```

Restore a deleted file.

```bash
git checkout <deleting-commit>^ -- <file>
```

### Reverting Commit

Generate a new commit that undoes all of the changes introduced in the commit.

```bash
git revert <commit>
```

This is a default option and doesn't need to be specified. This option will open the configured system editor and prompts you to edit the commit message prior to committing the revert.

```bash
git revert -e <commit>
           --edit
```

This is the inverse of the -e option. The revert will not open the editor.

```bash
git revert --no-edit <commit>
```

Passing this option will prevent git revert from creating a new commit that inverses the target commit. Instead of creating the new commit this option will add the inverse changes to the Staging Index and Working Directory.

```bash
git revert -n <commit>
           --no-commit
```

Cancel the revert operation.

```bash
git revert --abort
```

Revert initial commit.

```bash
git update-ref -d HEAD
```

Delete ref.

```bash
git update-ref -d <ref>
```

Revert merge commit. The -m followed by the 1 indicates that we want to keep the parent side of the merge (the branch we are merging into).

```bash
git revert -m 1 <commit>
           --mainline
```

### Unstaging Staged File

Unstage all files and leave the working directory unchanged.

```bash
git reset
```

Unstage all files and leave the working directory unchanged.

```bash
git reset HEAD
```

Unstage a file.

```bash
git reset <file>
```

Select diff hunks to remove from the index.

```bash
git reset -p
          --patch
```

### Resetting Current Commit

Reset the index and working directory to the given commit.

```bash
git reset --hard <commit>
```

Reset the index but not the working directory (default).

```bash
git reset --mixed <commit>
```

Do not reset the index file nor the working directory.

```bash
git reset --soft <commit>
```

Like --hard, but keep local working directory changes.

```bash
git reset --keep <commit>
```

Get back to where things were a period of time ago (e.g. when you screw up a merge).

```bash
git reset --hard master@{"300 minutes ago"}
```

### Removing Untracked Files

Remove untracked files from working directory.

```bash
git clean
```

Required when clean.requireForce is true (default).

```bash
git clean -f
          --force
```

Only show what would and what would not be removed.

```bash
git clean -n
          --dry-run
```

Remove untracked directories.

```bash
git clean -d
```

Remove only ignored files.

```bash
git clean -x
          -X
```

Show what would be done and clean files interactively.

```bash
git clean -i
          --interactive
```

## Rewriting History

### Fix Up Commit

Add forgotten files and edit the last commit's message.

```bash
git commit --amend
```

Add forgotten files without changing commit's message.

```bash
git commit --amend --no-edit
```

Change commit's message. NEVER amend commits that have been pushed to a public repository.

```bash
git commit --amend -m "<message>"
```

Override the author name used in the commit.

```bash
git commit --amend --author="Name <your_email@youremail.com>"
```

### Rebase Commits

Rebase your current HEAD onto branch. NEVER rebase published commits.

```bash
git rebase <branch>
```

 Automatically stashes any local changes made to your working copy before rebasing and reapplies them after the rebase is completed.

```bash
git rebase <branch> --autostash
```

Abort current rebase.

```bash
git rebase --abort
```

Continue after resolving merge conflict.

```bash
git rebase --continue
```

Make a list of commits to be rebased and open in $EDITOR.

```bash
git rebase -i
           --interactive
```

Rebase the current branch onto branch

```bash
git rebase -i <branch>
           --interactive
```

### Copy Commits

Jump into the branch that you want to insert the commit into.

```bash
git cherry-pick <commit>
```

Introduce particular commits from one branch onto a different branch.

```bash
git cherry-pick <branch>
```

Cancel revert or cherry-pick sequence.

```bash
git cherry-pick --abort
```

Resume revert or cherry-pick sequence.

```bash
git cherry-pick --continue
```

End revert or cherry-pick sequence.

```bash
git cherry-pick --quit
```

## Synchronize

### Remotes

Create a new connection to a remote repository. After adding a remote, you’ll be able to use remote as a convenient shortcut for url in other Git commands. HTTP is an easy way to allow anonymous, read-only access to a repository. For read-write access, you should use SSH instead.

```bash
git remote add <remote> <url>
```

Change URL for a remote.

```bash
git remote set-url <remote> <url>
```

Rename a remote and update all associated tracking branches.

```bash
git remote rename <old-remote> <new-remote>
```

Remove a remote and all associated tracking branches.

```bash
git remote rm <remote>
```

List remote names.

```bash
git remote
```

Show remote url after name.

```bash
git remote -v
           --verbose
```

Show information about a given remote.

```bash
git remote show <remote>
```

### Fetching

Fetch objects and refs from repository to see what everybody else has been working on. It has absolutely no affect on local development work because it doesn’t force to merge changes. When no remote is specified, by default the origin remote will be used.

```bash
git fetch
```

Fetch objects and refs from all remotes.

```bash
git fetch --all
```

Fetch objects and refs from the specified remote.

```bash
git fetch <remote>
```

Fetch objects and refs from the specified remote. Dot means to use the local repository as the remote.

```bash
git fetch .
```

Fetch objects and refs from the specified remote and branch.

```bash
git fetch <remote> <local-branch>
```

Merge local branch into local branch master without having to checkout master first. Here `.` means to use the local repository as the remote.

```bash
git fetch . <local-branch>:master
```

Merge remote branch into local branch without having to checkout local branch first.

```bash
git fetch origin <remote-branch>:<local-branch>
```

Remove any remote-tracking references that no longer exist on the remote.

```bash
git fetch -p
          --prune
```

Fetch from all remotes, not just one.

```bash
git remote update
```

### Pulling

Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy.

```bash
git pull
```

Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy.

```bash
git pull <remote>
```

Fetch the specified remote’s copy of the branch and merge it into the local copy.

```bash
git pull <remote> <branch>
```

Instead of using git merge to integrate the remote branch with the local one, use git rebase.

```bash
git pull --rebase <remote>
```

### Pushing

Push the current branch to remote, along with all of the necessary commits and internal object.

```bash
git push
```

Push the specified branch to remote, along with all of the necessary commits and internal object.

```bash
git push <remote> <local-branch>
```

Push to a remote branch with a different name than your local branch, along with all of the necessary commits and internal object.

```bash
git push <remote> <local-branch> <remote-branch>
```

Push a local branch and set the remote as upstream.

```bash
git push -u <remote> <local-branch>
         --set-upstream <remote> <local-branch>
```

Make the head of the branch point at your personal history, ignoring any changes that may have occurred in parallel with yours.

```bash
git push -f <remote> <commit>:<local-branch>
         --force
```

Push all refs under refs/heads/ path.

```bash
git push --all
```

It refuses to update a branch unless it is the state that we expect; i.e. nobody has updated the branch upstream.

```bash
git push --force-with-lease
```

Push all refs under refs/heads/ and refs/tags/ and delete non-existing refs.

```bash
git push --mirror
```

## Branches

### Create Branches

Create new branch.

```bash
git branch <branch>
```

Create new branch and set up a remote branch to track.

```bash
git branch --track <branch> <remote>/<remote-branch>
```

Create new branch from a remote branch and no tracking any remote branch.

```bash
git branch --no-track <branch> <remote>/<remote-branch>
```

Create new branch from commit and no tracking and no tracking any remote branch.

```bash
git branch --no-track <branch> <commit>
```

Create new branch and switch to it from a remote branch.

```bash
git checkout <remote-branch>
```

Create new branch and switch to it.

```bash
git checkout -b <branch>
```

Create new branch and switch to it at given local branch.

```bash
git checkout -b <branch> <local-branch>
```

Create new branch and switch to it at given remote branch.

```bash
git checkout -b <branch> <remote>/<remote-branch>
```

Create new branch and switch to it at given remote branch and without tracking.

```bash
git checkout -b <branch> <remote>/<remote-branch> --no-track
```

### Rename Branches

Rename a branch and the corresponding reflog.

```bash
git branch -m <old-local-branch-name> <new-local-branch-name>
           --move
```

Rename current branch and the corresponding reflog.

```bash
git branch -m <new-local-branch-name>
```

### Delete Branches

Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.

```bash
git branch -d <local-branch>
           --delete
```

Delete the specified branch even if it has unmerged changes.

```bash
git branch -D <local-branch>
```

Delete local branches that have been merged into the current branch.

```bash
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```

Delete remote branch from repository.

```bash
git push <remote> --delete <branch>
```

Push a delete signal to the remote that triggers a delete of the remote branch.

```bash
git push <remote> :<branch>
```

### List Branches

List local branches.

```bash
git branch
```

List only remote branches.

```bash
git branch -r
           --remotes
```

Show SHA-1 and commit subject line for each head.

```bash
git branch -v
           -vv--verbose
```

Show SHA-1 and commit subject line for each head, along with relationship to upstream branch (if any).

```bash
git branch -vv
```

List both remote and local branches.

```bash
git branch -a
           --all
```

Only list branches which are fully contained by HEAD.

```bash
git branch --merged
```

Only list branches which are fully contained by branch.

```bash
git branch --merged <branch>
```

List all branches that are already merged into.

```bash
git branch --merged <local-branch> <local-branch>
```

List all remote branches that have already been merged into current branch.

```bash
git branch -r --merged
           --remotes
```

Do not list branches which are fully contained by HEAD.

```bash
git branch --no-merged
```

List local branches, ordered by most recent commit.

```bash
git for-each-ref --sort=-committerdate refs/heads/
```

List local branches, ordered by least recent commit (since version 2.7.0).

```bash
git branch --sort=committerdate  # ASC
```

List local branches, ordered by most recent commit (since version 2.7.0).

```bash
git branch --sort=-committerdate  # DESC
```

### Merge Branches

Merge remote branch into current branch.

```bash
git merge <remote>/<remote-branch>
```

Merge local branch into current branch.

```bash
git merge <local-branch>
```

Generate a merge commit (3-way merge) even if the merge resolved as a fast-forward.

```bash
git merge --no-ff <local-branch>
```

Restore the original branch and abort the merge operation.

```bash
git merge --abort
```

Merge the last checked out branch.

```bash
git merge -
```

### Track Branches

Branch will start tracking remote branch.

```bash
git branch -u <remote>/<remote-branch>
           --set-upstream-to
```

Branch will start tracking remote branch.

```bash
git branch <local-branch> -u <remote>/<remote-branch>
```

Branch will start tracking remote branch.

```bash
git branch --set-upstream-to=<remote>/<remote-branch> <local-branch>
```

Branch will stop tracking remote branch.

```bash
git branch --unset-upstream
```

### Switch to Branch

Switch to a different branch.

```bash
git checkout <branch>
```

Quickly jump back to previous branch.

```bash
git checkout -
```

Quickly jump back to previous branch.

```bash
git checkout @{-1}
```

## Debugging

## Binary Search

Reset bisection state and start a new bisection.

```bash
git bisect start
```

Mark current or given revision as bad.

```bash
git bisect bad
```

Mark current or given revision as good.

```bash
git bisect good
```

Finish bisection search and return to the given branch (or master).

```bash
git bisect reset
```

Show the log of the current bisection.

```bash
git bisect log
```

Replay a bisection log.

```bash
git bisect replay
```

Print out the log of the current bisection.

```bash
git bisect log > <name>.log
```

## Tagging

Create annotated tag.

```bash
git tag -a <tag-name> -m "<message>"
```

Create lightweight tag.

```bash
git tag <tag-name>
```

Create tag for specific commit.

```bash
git tag <tag-name> <commit>
```

Search for tags with a particular pattern.

```bash
git tag -l "v1.8.5*"
```

By default, the git push command doesn’t transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them.

```bash
git push <remote> <tag>
```

All tags under refs/tags are pushed to the remote repository.

```bash
git push <remote> --tags
```

Push missing annotated tags reachable from the pushed refs.

```bash
git push --follow-tags
```

Delete local tag.

```bash
git tag -d <tag-name>
        --delete
```

Delete remote tag.

```bash
git push <remote> :<tag-name>
```

Show tag data.

```bash
git show <tag-name>
```

Show tag message.

```bash
git tag -n
```

Show the most recent tag on the current branch.

```bash
git describe --tags --abbrev=0
```

List the tags in alphabetical order.

```bash
git tag
```

## Submodules

Add given repository as a submodule.

```bash
git submodule add <url>
```

Add given repository as a submodule to path.

```bash
git submodule add <url> <path>
```

Initialize submodules recorded in the index by setting the submodule name in .git/config.

```bash
git submodule init
```

Initialize submodule at path.

```bash
git submodule init <path>
```

Update the registered submodules to match what the superproject expects by cloning missing submodules and updating the working tree of the submodules.

```bash
git submodule update
```

Initialize and update submodules.

```bash
git submodule update --init
```

Initialize and update submodule at path.

```bash
git submodule update --init <path>
```

Instead of using the superproject’s recorded SHA-1 to update the submodule, use the status of the submodule’s remote-tracking branch.

```bash
git submodule update --remote
```

Deinitialize submodule from repository.

```bash
git submodule deinit <path>
```

Unregister all submodules.

```bash
git submodule deinit --all
```

Unregister all submodules with local changes.

```bash
git submodule deinit -f --all
```

Copy the new configuration from .gitmodules to .git/config

```bash
git submodule sync
```

Show the status of the submodules.

```bash
git submodule status
```

Prints out a summary of the difference between the submodule's HEAD and the one recorded in main repository.

```bash
git submodule summary <path>
```

Evaluate shell command in each checked-out submodule.

```bash
git submodule foreach '<command>'
```

## Refs and the Reflog

### Hashes

Get the hash of object.

```bash
git rev-parse <object>
```

Get the hash of first commit.

```bash
git rev-list --max-parents=0 HEAD
```

Get the hash of the original base.

```bash
git merge-base <local-branch> master
```

Check whether or not the argument object is a valid reference.

```bash
git rev-parse --verify <object>
```

Get symbolic name of object.

```bash
git rev-parse --abbrev-ref <object>
```

Get symbolic name of object.

```bash
git symbolic-ref --short <object>
```

Get symbolic name of object.

```bash
git rev-name <object>
```


### Refs

A ref is an indirect way of referring to a commit. You can think of it as a user-friendly alias for a commit hash.
Refs are stored as normal text files in the .git/refs directory. To explore the refs in one of your repositories, navigate to .git/refs.
The heads directory defines all of the local branches in your repository. Each filename matches the name of the corresponding branch, and inside the file you’ll find a commit hash. This commit hash is the location of the tip of the branch.

Output information on each ref (bisect, heads, remotes or tags).

```bash
git for-each-ref refs/heads/
```

Show the last 10 local branches you recently worked on, sorted by the time that we were last working there.

```bash
git for-each-ref --count=10 --sort=-committerdate refs/heads/ --format="%(refname:short)"
```

### Special Refs

In addition to the refs directory, there are a few special refs that reside in the top-level .git directory. These refs are created and updated by Git when necessary. They are listed below:

* HEAD – The currently checked-out commit/branch.
* FETCH_HEAD – The most recently fetched branch from a remote repo.
* ORIG_HEAD – A backup reference to HEAD before drastic changes to it.
* MERGE_HEAD – The commit(s) that you’re merging into the current branch with git merge.
* CHERRY_PICK_HEAD – The commit that you’re cherry-picking.

### Relative Refs

The ~ character lets you reach parent commits. For example, the following displays the grandparent of HEAD.

```bash
git show HEAD~2
```

When working with merge commits, things get a little more complicated. Since merge commits have more than one parent, there is more than one path that you can follow. For 3-way merges, the first parent is from the branch that you were on when you performed the merge, and the second parent is from the branch that you passed to the git merge command.
If you want to follow a different parent, you need to specify which one with the ^ character. For example, if HEAD is a merge commit, the following returns the second parent of HEAD.

```bash
git show HEAD^2
```

### Reflog

The reflog is Git’s safety net. It records almost every change you make in your repository, regardless of whether you committed a snapshot or not. You can think of it as a chronological history of everything you’ve done in your local repo. Using git reset it is then possible to change back to the commit it was before.

```bash
git reflog
```

Show the reflog with relative date information (e.g. 2 weeks ago).

```bash
git reflog --relative-date
```

## Others

Run as if git was started in given path.

```bash
git -C <path> <command>
```

The Git repository browser.

```bash
git gitk <file>
```

Instantly browse your working repository in gitweb.

```bash
git instaweb --httpd=webrick
```

Create backup with your repository’s files.

```bash
git archive --format=zip > <name>.zip
```

Create backup with your repository’s files.

```bash
git archive --format=zip -o <name>.zip <object>
                         --output=<name>.zip
```

Create backup with your repository’s files.

```bash
git archive | gzip > <name>.tar.gz
```

Export branch with history to a file.

```bash
git bundle create <file> <branch-name>
```

Import from a bundle.

```bash
git clone repo.bundle <repo-dir> -b <branch-name>
```

Count unpacked number of objects and their disk consumption.

```bash
git count-objects --human-readable
```

Remove files that are listed in the .gitignore but still on the repository.

```bash
git ls-files -i --exclude-from=.gitignore | xargs git rm --cached
```

## Getting Help

Display help information about git.

```bash
git help <command>
```

Display help information about git.

```bash
git <command> --help
```

Get git version.

```bash
git --version
```

Print lines matching a pattern.

```bash
git grep <pattern>
```

List ignored files.

```bash
git check-ignore *
```

Determine which pattern is causing a particular file to be ignored.

```bash
git check-ignore -v <path>
```

FINDING COMMITS NOT MERGED UPSTREAM
Find commits yet to be applied to upstream.

```bash
git cherry <branch>
```

Find commits yet to be applied to upstream with additional information.

```bash
git cherry -v <branch>
           --verbose
```

IGNORING CHANGES TO A TRACKED FILE
Temporarily ignore changes.

```bash
git update-index --assume-unchanged <file>
```

Track changes again.

```bash
git update-index --no-assume-unchanged <file>
```

Files that should never be tracked are listed in your .gitignore file.
What about if you want to ignore some local changes to a tracked file?

RESOLVING CONFLICTS
Finish with git add file and git commit.

```bash
git checkout --theirs <file>
```

Finish with git add file and git commit.

```bash
git checkout --ours <file>
```

SHOWING ALL COMMITS TO BE MERGED
Show all commits in the current branch yet to be merged to local-branch

```bash
git cherry -v <local-branch>
```

// TODO

```bash
git cherry -v <local-branch> <branch-to-be-merged>
```

// TODO

```bash
git log <branch-to-be-merged> ^<local-branch>
```
