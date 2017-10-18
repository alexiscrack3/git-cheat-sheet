# GitHub Cheat Sheet
A collection of some of the most useful Git commands

## Table of Contents
1. [Settings](#settings)
    * [Setting Global Configs](#setting-global-configs)
    * [Getting Global Configs](#getting-global-configs)
    * [Removing Global Configs](#removing-global-configs)
    * [Setting Local Configs](#setting-local-configs)
    * [Getting Local Configs](#getting-local-configs)
    * [Removing Local Configs](#removing-local-configs)
2. [Aliases](#aliases)
    * [Creating Shortcuts](#creating-shortcuts)
    * [Setting Useful Shortcuts](#setting-useful-shortcuts)
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
    * [Display Logs](#display-logs)
    * [Display Differences](#display-differences)
    * [Blame Changes](#blame-changes)
    * [Display Reflog Information](#display-reflog-information)
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
9. [Collaborating](#collaborating)
    * [Remotes](#remotes)
    * [Fetch](#fetch)
    * [Pulling](#pulling)
    * [Pushing](#pushing)
10. [Using Branches](#using-branches)
    * [Create Branches](#create-branches)
    * [Rename Branches](#rename-branches)
    * [Delete Branches](#delete-branches)
    * [List Branches](#list-branches)
    * [Merge Branches](#merge-branches)
    * [Track Branches](#track-branches)
    * [Switch to Branch](#switch-to-branch)
11. [Debugging](#debugging)
    * [File Annotation](#file-annotation)
    * [Binary Search](#binary-search)
12. [Tagging](#tagging)
13. [Submodules](#submodules)
    * [Starting with Submodules](#starting-with-submodules)
    * [Cloning a Project with Submodules](#cloning-a-project-with-submodules)
14. [Others](#others)
15. [Getting Help](#getting-help)

## Settings
### Setting Global Configs
Set your username for every repository.
```bash
$ git config --global user.name "<name>"
```
Set your email for every repository.
```bash
$ git config --global user.email "<email>"
```
Color output of capable git commands. value: true, false, auto.
```bash
$ git config --global color.ui <value>
```
A boolean to make git-clean do nothing unless given -f, -i or -n. Defaults to true. Possible values: true, false
```bash
$ git config --global clean.requireForce <value>
```
Make git case sensitive. Possible values: true, false.
```bash
$ git config --global core.ignorecase <value>
```
Defines the action git push should take. Possible values: nothing, matching, upstream, current, simple (safest option and is well-suited for beginners).
```bash
$ git config --global push.default <value>
```
// TODO
```bash
$ git config --global merge.tool <editor>
```
// TODO
```bash
$ git config --global core.editor <editor>
```

### Getting Global Configs
Get all your global configs.
```bash
$ git config --global -l
                      --list
```
Get all your global configs.
```bash
$ cat ~/.gitconfig
```
Get global username.
```bash
$ git config --global user.name
```
Get global email.
```bash
$ git config --global user.email
```

### Removing Global Configs
Remove global username.
```bash
$ git config --global --unset user.name
```
Remove global email.
```bash
$ git config --global --unset user.email
```

### Setting Local Configs
Set your username for current repository.
```bash
$ git config user.name "<name>"
```
Set your email for current repository.
```bash
$ git config user.email "<email>"
```

### Getting Local Configs
Get all your local configs.
```bash
$ git config --global -l
                      --list
```
Get all your local configs.
```bash
$ cat .git/config
```
Get username.
```bash
$ git config --get user.name
```
Get email.
```bash
$ git config --get user.email
```

### Removing Local Configs
Remove username.
```bash
$ git config --unset user.name
```
Remove email.
```bash
$ git config --unset user.email
```

## Aliases
### Creating Shortcuts
// TODO
```bash
$ git config --global alias.<alias-name> "<command>"
```

### Setting Useful Shortcuts
// TODO
```bash
$ git config --global alias.lg "log --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>' --abbrev-commit"
```
// TODO
```bash
git config --global alias.lgf "log --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%ad) %C(bold blue)<%an>' --abbrev-commit"
```
// TODO
```bash
$ git config --global alias.ls "log --pretty=format:'%C(yellow)%h%Cred%d\ %Creset%s%Cblue\ [%cn]' --decorate"
```
// TODO
```bash
$ git config --global alias.ll "log --pretty=format:'%C(yellow)%h%Cred%d\ %Creset%s%Cblue\ [%cn]' --decorate --numstat"
```
// TODO
```bash
$ git config --global alias.lnc "log --pretty=format:'%h\ %s\ [%cn]'"
```
// TODO
```bash
$ git config --global alias.lds "log --pretty=format:'%C(yellow)%h\ %ad%Cred%d\ %Creset%s%Cblue\ [%cn]' --decorate --date=short"
```
// TODO
```bash
$ git config --global alias.ld "log --pretty=format:'%C(yellow)%h\ %ad%Cred%d\ %Creset%s%Cblue\ [%cn]' --decorate --date=relative"
```
// TODO
```bash
$ git config --global alias.le "log --oneline --decorate"
```
git blame implies that the developer we’re looking for did something wrong, and this might not always be the case.
```bash
$ git config --global alias.praise blame
```

## Setting Up Repository
### Initializing Repository
Create empty git repository or re-initialize an existing one.
```bash
$ git init
```
Create empty git repository in directory
```bash
$ git init <directory>
```

### Initializing Shared Repository
Create a repository that doesn’t have a working directory, making it impossible to edit files and commit changes in that repository.
```bash
$ git init --bare
```

### Cloning Repository
Clone repository in the current directory.
```bash
$ git clone <repository>
```
Clone repository into directory.
```bash
$ git clone <repository> <directory>
```
Clone repository and set remote name.
```bash
$ git clone --origin <new-remote-name> <repository>
```
Clone repository and point HEAD to the given branch.
```bash
$ git clone -b <branch> <repository>
            --branch
```
Clone only history leading up to the main branch or the one specified by -b
```bash
$ git clone -b <branch> --single-branch <repository>
```

## Saving Changes
### Adding Files
#### Tracking New or Modified Files
Add all files.
```bash
$ git add .
```
Add a specific file.
```bash
$ git add <file>
```
Add a specific directory.
```bash
$ git add <directory>
```
Add files with an extension file.
```bash
$ git add *.<extension>
```
Do not actually add files; only show which ones would be added.
```bash
$ git add -n
          --dry-run
```
Add to index modified and deleted tracked files but it will never stage new files.
```bash
$ git add -u
          --update
```
Begin an interactive staging session that lets you choose portions of a file to add to the next commit.
```bash
$ git add -p
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
$ git add $(git ls-files --modified)
```

#### Interactive Staging
Staging only untracked files.
```bash
$ git add -i
          --interactive
#   Type a (for "add untracked")
#   Then * (for "all")
#   Then q (to quit)
```

### Removing Files
Remove file from the working directory.
```bash
$ git rm <file>
```
Remove recursively directory from the working directory.
```bash
$ git rm -r <directory>
```
Remove a file from index but not from disk.
```bash
$ git rm --cached <file>
```
Remove recursively a directory from index but not from disk.
```bash
$ git rm --cached -r <directory>
```
Remove files from the working directory.
```bash
$ git rm $(git ls-files --deleted)
```
Do not actually remove the files, just show if they exist in the index.
```bash
$ git rm -n
         --dry-run
```

### Renaming Files
First way.
```bash
$ mv <old-name> <new-name>
$ git rm <old-name>
$ git add <new-name>
```
Second way.
```bash
$ git mv <file-from> <file-to>
```

### Committing Files
Use the given message as the commit message.
```bash
$ git commit -m "<message>"
             --message
```
Use the given message as the commit message and override the author name used in the commit.
```bash
$ git commit -m "<message>" --author="Name <your_email@youremail.com>"
```
Stage all modified and deleted paths, but new files you have not told git about are not affected.
```bash
$ git commit -a
             --all
```
Stage all modified and deleted path using the given message, but new files you have not told git about are not affected.
```bash
$ git commit -am "<message>"
```
Show unified diff of all file changes.
```bash
$ git commit -v
             --verbose
```
Show list of paths that are to be commited or not, and any untracked.
```bash
$ git commit --dry-run --short
```
Skip staging area and commit files, this only works with tracked files.
```bash
$ git commit --only <file>
```

### Stashing Files
Stash away changes to dirty working directory.
```bash
$ git stash
```
Interactively select hunks from diff between HEAD and working directory to stash.
```bash
$ git stash -p
            --patch
```
Stash only unstaged changes.
```bash
$ git stash -k
```
Include untracked files.
```bash
$ git stash -u
            --include-untracked
```
All changes already added to the index are left intact.
```bash
$ git stash --keep-index
```
All changes already added to the index are undone.
```bash
$ git stash --no-keep-index
```
Save local changes to a new stash with message.
```bash
$ git stash save "<message>"
```
Save local changes including untracked files.
```bash
$ git stash save -u
                 --include-untracked
```
List the stashes stored in the stack.
```bash
$ git stash list
```
Apply the changes recorded in the stash.
```bash
$ git stash apply stash@{n}
```
Remove and apply a single stashed state from the stack.
```bash
$ git stash pop
```
Show the changes recorder in the latest stash as a diff.
```bash
$ git stash show
```
Show the changes recorded in the stash as a diff.
```bash
$ git stash show stash@{n}
```
Show the changes recorded in the stash as a diff in patch format.
```bash
$ git stash show -p stash@{n}
                 --patch
```
Remove a single stashed state from the stack.
```bash
$ git stash drop stash@{n}
```
Remove all the stashed states.
```bash
$ git stash clear
```

## Inspecting Changes
### Display State
Show working directory status.
```bash
$ git status
```
Output in short format.
```bash
$ git status -s
             --short
```
Status of ignored files.
```bash
$ git status --ignored
```

### Display Objects
Show details of the most recent commit.
```bash
$ git show
```
Show details of the most recent commit.
```bash
$ git show HEAD
```
Show details of the object (blobs, trees, tags and commits).
```bash
$ git show <object>
```
Ignore white space when comparing lines.
```bash
$ git show <object> -w
                    --ignore-all-space
```
Show only names of changed files without the diffs.
```bash
$ git show --name-only <object>
```
Show only names and status of changed files without the diffs.
```bash
$ git show --name-status <object>
```
Show details of an object with pretty format.
```bash
$ git show --format="<format>" <object>
           --pretty
```
Show details of commit via commit message pattern matching.
```bash
$ git show :/<commit>
```
Show details of a file on a object.
```bash
$ git show <object>:<file>
```
Export file to path.
```bash
$ git show <branch>:<file> > <path>
```
Show branches and their commits.
```bash
$ git show-branch
```

### Display Logs
Show all commits.
```bash
$ git log
```
Show changes over time for a specific file.
```bash
$ git log <file>
```
Generate diff in patch format for a specific file.
```bash
$ git log -p <file>
          --patch
```
Show changes over time for a specific file even if the file was renamed.
```bash
$ git log --follow <file>
```
Exports git log to text file.
```bash
$ git log > <file>
```
Show only commits that occur in the range.
```bash
$ git log <commit>..<commit>
```
Maximum number of commits to display.
```bash
$ git log -n
          --max-count
```
Condense each commit to a single line.
```bash
$ git log --oneline
```
Get a list of commits made in the last two weeks.
```bash
$ git log --since='2 weeks'
```
Show statistics for files modified in each commit.
```bash
$ git log --stat
```
Display only the changed/insertions/deletions line from the --stat command.
```bash
$ git log --shortstat
```
Generate condensed summary of extended header information.
```bash
$ git log --summary
```
Search for commits by a particular author. The argument can be a plain string or a regular expression.
```bash
$ git log --author="<pattern>"
```
Search for commits with a commit message. The argument can be a plain string or a regular expression.
```bash
$ git log --grep="<pattern>"
```
Show what every contributor has been getting up to across all branches.
```bash
$ git log --all --oneline --no-merges
```
Show changes since two weeks.
```bash
$ git log --no-merges --raw --since='2 weeks ago'
```
Generate a Changelog.
```bash
$ git log --oneline --no-merges <last tag>..HEAD
```
Check which changes you’re about to pull.
```bash
$ git log --oneline --no-merges HEAD..<remote>/<branch>
```
Review what you’re about to push.
```bash
$ git log --oneline --no-merges <remote>/<branch>..HEAD
```
View complex logs.
```bash
$ git log --graph --all --decorate --stat --date=iso
```

### Display Differences
What's different from our most recent commit (staged and unstaged changes).
```bash
$ git diff
```
Ignore white space when comparing lines.
```bash
$ git diff -w
           --ignore-all-space
```
What's different from our most recent commit (staged and unstaged changes).
```bash
$ git diff HEAD
```
What's different from our previous commit.
```bash
$ git diff HEAD~1
           HEAD^1
           HEAD^
```
What's different from two previous commits.
 ```bash
$ git diff HEAD~2
           HEAD^2
           HEAD^^
```
Show staged changes against your HEAD.
```bash
$ git diff --cached
           --staged
```
Show changes between commits.
```bash
$ git diff <commit> <commit>
```
Show changes in file between commits.
```bash
$ git diff <commit> <commit> <file>
```
Show inline word diff.
```bash
$ git diff --word-diff
```
Print out changes.
```bash
$ git diff > <file>
```

### Display Reflog Information
Contains information about the old state of branches and allows you to go back to that state if necessary. Using git reset it is then possible to change back to the commit it was before.
```bash
$ git reflog
```
Show the reflog with relative date information (e.g. 2 weeks ago).
```bash
$ git reflog --relative-date
```

## Listing Files
Show information about files in the index and the working directory.
```bash
$ git ls-files
```
Show cached files.
```bash
$ git ls-files -c
               --cached
```
Show modified files.
```bash
$ git ls-files -m
               --modified
```
Show deleted files.
```bash
$ git ls-files -d
               --deleted
```
Show all untracked or ignored files.
```bash
$ git ls-files -o
               --others
```
Show only ignored files in the output. When showing files in the index, print only those matched by an exclude pattern. When showing "other" files, show only those matched by an exclude pattern.
```bash
$ git ls-files -i
               --ignored
```
Show all untracked files.
```bash
$ git ls-files --others --exclude-standard
```
Show all ignored files.
```bash
$ git ls-files --others --ignored --exclude-standard
```
Show staged contents (mode bits, object name and stage number).
```bash
$ git ls-files -s
               --stage
```
This option identifies the file status with the following tags.
```bash
$ git ls-files -t
# H - cached
# S - skip-worktree
# M - unmerged
# R - removed/deleted
# C - modified/changed
# K - to be killed
# ? - other
```

## Undoing Changes
### Reverting Files
Return the state of your unstaged files as they were in your last commit.
```bash
$ git checkout .
```
Return the state of your unstaged files as they were in your HEAD (last commit).
```bash
$ git checkout HEAD
```
Return the state of your unstaged files that match the regular expression as they were in your last commit.
```bash
$ git checkout \*.txt
```
Return the state of your file as it was in your last commit.
```bash
$ git checkout <file>
```
Return the state of your file as it was in your last commit. Use two consecutive hyphens if file and branch have the same name.
```bash
$ git checkout -- <file>
```
This turns the <file> that resides in the working directory into an exact copy of the one from <commit> and adds it to the staging area.
```bash
$ git checkout <commit> <file>
```
This turns the <file> that resides in the working directory into an exact copy of the one from stash@{n} and adds it to the staging area.
```bash
$ git checkout stash@{n} <file>
```
Update all files in the working directory to match the specified commit. This will put you in a detached HEAD state.
```bash
$ git checkout <commit> .
```
Interactively select hunks in diff.
```bash
$ git checkout -p
               --patch
```
Interactively select hunks in diff for a specific file.
```bash
$ git checkout -p <file>
               --patch
```
Restore a deleted file.
```bash
$ git checkout <deleting-commit>^ -- <file>
```

### Reverting Commit
Generate a new commit that undoes all of the changes introduced in the commit.
```bash
$ git revert <commit>
```
Cancel the revert operation.
```bash
$ git revert --abort
```
Revert initial commit.
```bash
$ git update-ref -d HEAD
```
Revert merge commit. The -m followed by the 1 indicates that we want to keep the parent side of the merge (the branch we are merging into).
```bash
$ git revert -m 1 <commit>
             --mainline
```

### Unstaging Staged File
Unstage all files and leave the working directory unchanged.
```bash
$ git reset
```
Unstage all files and leave the working directory unchanged.
```bash
$ git reset HEAD
```
Unstage a file.
```bash
$ git reset <file>
```
Select diff hunks to remove from the index.
```bash
$ git reset -p
            --patch
```

### Resetting Current Commit
Reset the index and working directory to the given commit.
```bash
$ git reset --hard <commit>
```
Reset the index but not the working directory (default).
```bash
$ git reset --mixed <commit>
```
Do not reset the index file nor the working directory.
```bash
$ git reset --soft <commit>
```
Like --hard, but keep local working directory changes.
```bash
$ git reset --keep <commit>
```

### Removing Untracked Files
Remove untracked files from working directory.
```bash
$ git clean
```
Required when clean.requireForce is true (default).
```bash
$ git clean -f
            --force
```
Only show what would and what would not be removed.
```bash
$ git clean -n
            --dry-run
```
Remove untracked directories.
```bash
$ git clean -d
```
Remove only ignored files.
```bash
$ git clean -X
```
Show what would be done and clean files interactively.
```bash
$ git clean -i
            --interactive
```

## Rewriting History
### Fix Up Commit
Add forgotten files and edit the last commit's message.
```bash
$ git commit --amend
```
Add forgotten files without changing commit's message.
```bash
$ git commit --amend --no-edit
```
Change commit's message. NEVER amend commits that have been pushed to a public repository.
```bash
$ git commit --amend -m "<message>"
```
Override the author name used in the commit.
```bash
$ git commit --amend --author="Name <your_email@youremail.com>"
```

### Rebase Commits
Rebase your current HEAD onto branch. NEVER rebase published commits.
```bash
$ git rebase <branch>
```
Abort current rebase.
```bash
$ git rebase --abort
```
Continue after resolving merge conflict.
```bash
$ git rebase --continue
```
Make a list of commits to be rebased and open in $EDITOR.
```bash
$ git rebase -i
             --interactive
```
Rebase the current branch onto <branch>
```bash
$ git rebase -i <branch>
             --interactive
```

### Copy Commits
Jump into the branch that you want to insert the commit into.
```bash
$ git cherry-pick <commit>
```
Introduce particular commits from one branch onto a different branch.
```bash
$ git cherry-pick <branch>
```
Cancel revert or cherry-pick sequence.
```bash
$ git cherry-pick --abort
```
Resume revert or cherry-pick sequence.
```bash
$ git cherry-pick --continue
```
End revert or cherry-pick sequence.
```bash
$ git cherry-pick --quit
```

## Collaborating
### Remotes
Create a new connection to a remote repository. After adding a remote, you’ll be able to use <remote> as a convenient shortcut for <url> in other Git commands. HTTP is an easy way to allow anonymous, read-only access to a repository. For read-write access, you should use SSH instead.
```bash
$ git remote add <remote> <url>
```
Change URL for a remote.
```bash
$ git remote set-url <remote> <url
```
Rename a remote and update all associated tracking branches.
```bash
$ git remote rename <old-remote> <new-remote>
```
Remove a remote and all associated tracking branches.
```bash
$ git remote rm <remote>
```
List remote names.
```bash
$ git remote
```
Show remote url after name.
```bash
$ git remote -v
             --verbose
```
Show information about a given remote.
```bash
$ git remote show <remote>
```

### Fetch
Fetch objects and refs from repository to see what everybody else has been working on. It has absolutely no affect on local development work because it doesn’t force to merge changes. When no remote is specified, by default the origin remote will be used.
```bash
$ git fetch
```
Fetch objects and refs from all remotes.
```bash
$ git fetch --all
```
Fetch objects and refs from the specified remote.
```bash
$ git fetch <remote>
```
Fetch objects and refs from the specified remote and branch.
```bash
$ git fetch <remote> <local-branch>
```
Remove any remote-tracking references that no longer exist on the remote.
```bash
$ git fetch -p
            --prune
```
Fetch from all remotes, not just one.
```bash
$ git remote update
```

### Pulling
Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy.
```bash
$ git pull
```
Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy.
```bash
$ git pull <remote>
```
Fetch the specified remote’s copy of the branch and merge it into the local copy.
```bash
$ git pull <remote> <branch>
```
Instead of using git merge to integrate the remote branch with the local one, use git rebase.
```bash
$ git pull --rebase <remote>
```

### Pushing
Push the current branch to <remote>, along with all of the necessary commits and internal object.
```bash
$ git push
```
Push the specified branch to <remote>, along with all of the necessary commits and internal object.
```bash
$ git push <remote> <local-branch>
```
Push to a remote branch with a different name than your local branch, along with all of the necessary commits and internal object.
```bash
$ git push <remote> <local-branch> <remote-branch>
```
Push a local branch and set the remote as upstream.
```bash
$ git push -u <remote> <local-branch>
           --set-upstream <remote> <local-branch>
```
Make the head of the branch point at your personal history, ignoring any changes that may have occurred in parallel with yours.
```bash
$ git push -f <remote> <commit>:<local-branch>
           --force
```
Push all refs under refs/heads/ path.
```bash
$ git push --all
```
It refuses to update a branch unless it is the state that we expect; i.e. nobody has updated the branch upstream.
```bash
$ git push --force-with-lease
```
Push all refs under refs/heads/ and refs/tags/ and delete non-existing refs.
```bash
$ git push --mirror
```

## Using Branches
### Create Branches
Create new branch.
```bash
$ git branch <branch>
```
Create new branch and set up a remote branch to track.
```bash
$ git branch --track <branch> <remote>/<remote-branch>
```
Create new branch from a remote branch and no tracking any remote branch.
```bash
$ git branch --no-track <branch> <remote>/<remote-branch>
```
Create new branch from commit and no tracking and no tracking any remote branch.
```bash
$ git branch --no-track <branch> <commit>
```
Create new branch and switch to it from a remote branch.
```bash
$ git checkout <remote-branch>
```
Create new branch and switch to it.
```bash
$ git checkout -b <branch>
```
Create new branch and switch to it at given local branch.
```bash
$ git checkout -b <branch> <local-branch>
```
Create new branch and switch to it at given remote branch.
```bash
$ git checkout -b <branch> <remote>/<remote-branch>
```
Create new branch and switch to it at given remote branch and without tracking.
```bash
$ git checkout -b <branch> <remote>/<remote-branch> --no-track
```

### Rename Branches
Rename a branch and the corresponding reflog.
```bash
$ git branch -m <old-local-branch-name> <new-local-branch-name>
             --move
```
Rename current branch and the corresponding reflog.
```bash
$ git branch -m <new-local-branch-name>
```

### Delete Branches
Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.
```bash
$ git branch -d <local-branch>
             --delete
```
Delete the specified branch even if it has unmerged changes.
```bash
$ git branch -D <local-branch>
```
Delete local branches that have been merged into the current branch.
```bash
$ git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```
Delete remote branch from the remote repository.
```bash
$ git push <remote> --delete <branch>
```
Delete remote branch from the remote repository.
```bash
$ git push <remote> :<branch>
```

### List Branches
List local branches.
```bash
$ git branch
```
List only remote branches.
```bash
$ git branch -r
             --remotes
```
Show SHA-1 and commit subject line for each head.
```bash
$ git branch -v
             -vv--verbose
```
Show SHA-1 and commit subject line for each head, along with relationship to upstream branch (if any).
```bash
$ git branch -vv
```
List both remote and local branches.
```bash
$ git branch -a
             --all
```
Only list branches which are fully contained by HEAD.
```bash
$ git branch --merged
```
Only list branches which are fully contained by branch.
```bash
$ git branch --merged <branch>
```
List all branches that are already merged into.
```bash
$ git branch --merged <local-branch> <local-branch>
```
List all remote branches that have already been merged into current branch.
```bash
$ git branch -r --merged
            --remotes
```
Do not list branches which are fully contained by HEAD.
```bash
$ git branch --no-merged
```
List local branches, ordered by most recent commit.
```bash
$ git for-each-ref --sort=-committerdate refs/heads/
```
List local branches, ordered by most recent commit (since version 2.7.0).
```bash
$ git branch --sort=-committerdate  # DESC
```
List local branches, ordered by least recent commit (since version 2.7.0).
```bash
$ git branch --sort=committerdate  # ASC
```

### Merge Branches
Merge remote branch into current branch.
```bash
$ git merge <remote>/<remote-branch>
```
Merge local branch into current branch.
```bash
$ git merge <local-branch>
```
Generate a merge commit even if the merge resolved as a fast-forward.
```bash
$ git merge --no-ff <local-branch>
```
Restore the original branch and abort the merge operation.
```bash
$ git merge --abort
```
Merge the last checked out branch.
```bash
$ git merge -
```

### Track Branches
Branch will start tracking remote branch.
```bash
$ git branch -u <remote>/<remote-branch>
            --set-upstream-to
```
Branch will start tracking remote branch.
```bash
$ git branch <local-branch> -u <remote>/<remote-branch>
```
Branch will start tracking remote branch.
```bash
$ git branch --set-upstream-to=<remote>/<remote-branch> <local-branch>
```
Branch will stop tracking remote branch.
```bash
$ git branch --unset-upstream
```

### Switch to Branch
Switch to a different branch.
```bash
$ git checkout <branch>
```
Quickly jump back to previous branch.
```bash
$ git checkout -
```

## Debugging
### File Annotation
Show what revision and author last modified each line of a file.
```bash
$ git blame <file>
```
Annotate only the given line range.
```bash
$ git blame -L <starting-line>,<ending-line> <file>
```

## Binary Search
Reset bisection state and start a new bisection.
```bash
$ git bisect start
```
Mark current or given revision as bad.
```bash
$ git bisect bad
```
Mark current or given revision as good.
```bash
$ git bisect good
```
Finish bisection search and return to the given branch (or master).
```bash
$ git bisect reset
```
Show the log of the current bisection.
```bash
$ git bisect log
```
Print out the log of the current bisection.
```bash
$ git bisect log > <name>.log
```

## Tagging
Create annotated tag.
```bash
$ git tag -a <tag-name> -m "<message>"
```
Create lightweight tag.
```bash
$ git tag <tag-name>
```
Create tag for specific commit.
```bash
$ git tag <tag-name> <commit>
```
Search for tags with a particular pattern.
```bash
$ git tag -l "v1.8.5*"
```
By default, the git push command doesn’t transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them.
```bash
$ git push <remote> <tag>
```
All tags under refs/tags are pushed to the remote repository.
```bash
$ git push <remote> --tags
```
Push missing annotated tags reachable from the pushed refs.
```bash
$ git push --follow-tags
```
Delete local tag.
```bash
$ git tag -d <tag-name>
          --delete
```
Delete remote tag.
```bash
$ git push <remote> :<tag-name>
```
Show tag data.
```
$ git show <tag-name>
```
Show tag message.
```bash
$ git tag -n
```
Show the most recent tag on the current branch.
```bash
$ git describe --tags --abbrev=0
```
List the tags in alphabetical order.
```bash
$ git tag
```

## Submodules
### Starting with Submodules
Initialize a submodule.
```bash
$ git submodule init
```
Add given repository as a submodule.
```bash
$ git submodule add <url> <directory>
```
Update a submodule.
```bash
$ git submodule update --init --recursive
```

### Cloning a Project with Submodules
Clone an existing repository and all its sub-modules recursively.
```bash
$ git clone --recursive <repository>
```

## Others
Get SHA-1 of object.
```bash
$ git rev-parse <object>
```
Get a non-ambiguous short name of object.
```bash
$ git rev-parse --abbrev-ref <object>
```
Number of commits of each contributor.
```bash
$ git shortlog -s -n
               -sn
```
Number of commits of each contributor and ensures that merge commits aren’t being counted.
```bash
git shortlog -sn --all --no-merges
```
The Git repository browser.
```bash
$ git gitk <file>
```
Instantly browse your working repository in gitweb.
```bash
$ git instaweb --httpd=webrick
```
Create backup with your repository’s files.
```bash
$ git archive --format=zip > <name>.zip
```
Create backup with your repository’s files.
```bash
$ git archive <object> --format=zip --output=<name>.zip
```
Create backup with your repository’s files.
```bash
$ git archive | gzip > <name>.tar.gz
```
Export branch with history to a file.
```bash
$ git bundle create <file> <branch-name>
```
Import from a bundle.
```bash
$ git clone repo.bundle <repo-dir> -b <branch-name>
```
Count unpacked number of objects and their disk consumption.
```bash
$ git count-objects --human-readable
```
Remove files that are listed in the .gitignore but still on the repository.
```bash
$ git ls-files -i --exclude-from=.gitignore | xargs git rm --cached
```
Show the last 10 local branches you recently worked on, sorted by the time that we were last working there.
```bash
$ git for-each-ref --count=10 --sort=-committerdate refs/heads/ --format="%(refname:short)"
```
Output information on each ref (bisect, heads, remotes or tags).
```bash
$ git for-each-ref refs/heads/
```

## Getting Help
Display help information about git.
```bash
$ git help <command>
```
Display help information about git.
```bash
$ git <command> --help
```
Get git version.
```bash
$ git --version
```
Print lines matching a pattern.
```bash
$ git grep <pattern>
```
List ignored files.
```bash
$ git check-ignore *
```


FINDING COMMITS NOT MERGED UPSTREAM
Find commits yet to be applied to upstream.
```bash
$ git cherry <branch>
```
Find commits yet to be applied to upstream with additional information.
```bash
$ git cherry -v <branch>
             --verbose
```


IGNORING CHANGES TO A TRACKED FILE
Temporarily ignore changes.
```bash
$ git update-index --assume-unchanged <file>
```
Track changes again.
```bash
$ git update-index --no-assume-unchanged <file>
```
Files that should never be tracked are listed in your .gitignore file.
What about if you want to ignore some local changes to a tracked file?


RESOLVING CONFLICTS
Finish with git add <file> and git commit.
```bash
$ git checkout --theirs <file>
```
Finish with git add <file> and git commit.
```bash
$ git checkout --ours <file>
```


SHOWING ALL COMMITS TO BE MERGED
Show all commits in the current branch yet to be merged to <local-branch>
```bash
$ git cherry -v <local-branch>
```
// TODO
```bash
$ git cherry -v <local-branch> <branch-to-be-merged>
```
// TODO
```bash
$ git log <branch-to-be-merged> ^<local-branch>
```
