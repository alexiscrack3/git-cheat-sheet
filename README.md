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
    * [Display Differences](#display-differences)
    * [Display Logs](#display-logs)
6. [Listing Files](#listing-files)
7. [Undoing Changes](#undoing-changes)
    * [Reverting Files](#reverting-files)
    * [Reverting Commit](#reverting-commit)
    * [Unstaging Staged File](#unstaging-staged-file)
    * [Resetting Current Commit](#resetting-current-commit)
    * [Removing Untracked Files](#removing-untracked-files)
8. [Tagging](#tagging)
    * [Creating Tags](#creating-tags)
        * [Annotated Tags](#annotated-tags)
        * [Lightweight Tags](#lightweight-tags)
    * [Searching Tags](#searching-tags)
    * [Tagging Later](#tagging-later)
    * [Sharing Tags](#sharing-tags)
    * [Deleting Tags](#deleting-tags)
        * [Local Tag](#local-tag)
        * [Remote Tag](#remote-tag)
    * [Seeing](#seeing)
    * [Listing Tags](#listing-tags)
9. [Submodules](#submodules)
    * [Starting with Submodules](#starting-with-submodules)
    * [Cloning a Project with Submodules](#cloning-a-project-with-submodules)

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
Add modified files to index
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
Stash only unstaged changes
```bash
$ git stash -k
```
Include untracked files
```bash
$ git stash -u
            --include-untracked
```
All changes already added to the index are left intact
```bash
$ git stash --keep-index
```
All changes already added to the index are undone
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
Show working tree status.
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

### Display Differences
What's different from our most recent commit (staged and unstaged changes).
```bash
$ git diff
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
Show statistics for files modified in each commit.
```bash
$ git log --stat
```
Display only the changed/insertions/deletions line from the --stat command.
```bash
$ git log --shortstat
```
Generate condensed summary of extended header information
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
Show changes since two weeks.
```bash
$ git log --no-merges --raw --since='2 weeks ago'
```

## Listing Files
Show information about files in the index and the working tree.
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
Return the state of your unstaged files as they were in your HEAD (last commit)
```bash
$ git checkout HEAD
```
Return the state of your unstaged files that match the regular expression as they were in your last commit.
```bash
$ git checkout \*.txt
```
Return the state of your file as it was in your last commit
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
Restore a deleted file
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
Revert merge commit. The -m followed by the 1 indicates that we want to keep the parent side of the merge (the branch we are merging into)
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
Remove untracked directories
```bash
$ git clean -d
```
Remove only ignored files
```bash
$ git clean -X
```
Show what would be done and clean files interactively
```bash
$ git clean -i
            --interactive
```

## Blaming Changes
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
$ git bisect log > file.log
```













ADDING FORGOTTEN FILE TO LAST COMMIT
// TODO
```bash
$ git add <file>
```
Add forgotten file and lets you edit the previous commit's message
```bash
$ git commit --amend
```
Add forgotten file without changing its commit message
```bash
$ git commit --amend --no-edit
```

CHANGING YOUR LAST COMMIT
Change your commit message using the terminal
```bash
$ git commit --amend
```
Changes your commit message. NEVER amend commits that have been pushed to a public repository
```bash
$ git commit --amend -m "New commit message"
```
Amend author
```bash
$ git commit --amend --author='<name> <email>'
```
Reword the previous commit
```bash
$ git commit -v --amend
```



MOVING THE LATEST COMMIT TO A NEW BRANCH
// TODO
```bash
$ git checkout -b <new-branch>
```
// TODO
```bash
$ git reset --hard HEAD~
```



REBASING COMMITS
Rebase your current HEAD onto branch. NEVER rebase published commits
```bash
$ git rebase <branch>
```
Abort a rebase
```bash
$ git rebase --abort
```
Continue a rebase after resolving conflicts
```bash
$ git rebase --continue
```

1st. way
git checkout <local-branch>
git rebase <remote-branch>      // Rebase the current branch onto <remote-branch>, which can be any kind of commit reference (an ID, a branch name, a tag, or a relative reference to HEAD). This allow us do a standard fast-forward merge

2nd. way
git rebase <remote-brach> <local-branch>

3rd.way
git rebase -i <remote-branch>   // This opens an editor where you can enter commands for each commit to be rebase. Pick and/or squash commits. Finally, you can do a fast-forward merge to integrate the polished branch into the main code base

4th. way
git rebase -i HEAD~10           // If you have not yet pushed the commit anywhere, you can use git rebase -i to remove that commit. The ~10 means rebase the last 10 commits.



RESOLVING CONFLICTS
Finish with git add <file> and git commit
```bash
$ git checkout --theirs <file>
```
Finish with git add <file> and git commit
```bash
$ git checkout --ours <file>
```



COPYING COMMITS
Jump into the branch that you want to insert the commit into
```bash
$ git cherry-pick <commit>
```
Introduce particular commits from one branch onto a different branch
```bash
$ git cherry-pick <branch>
```
// TODO
```bash
$ git cherry-pick --abort
```
// TODO
```bash
$ git cherry-pick --continue
```
// TODO
```bash
$ git cherry-pick --quit
```




FECTHING FROM YOUR REMOTES
When no remote is specified, by default the origin remote will be used
```bash
$ git fetch
```
Fetch all remotes
```bash
$ git fetch --all
```
Fetch all of the branches from the repository to see what everybody else has been working on. It has absolutely no affect on your local development work because it doesn’t force you to merge changes. When you finish to review changes you have to merge remote branch to a local branch
```bash
$ git fetch <remote>
```
Fetch the specified branch
```bash
$ git fetch <remote> <local-branch>
```
After fetching, remove any remote-tracking references that no longer exist on the remote
```bash
$ git fetch -p
            --prune
```



PULLING FROM YOUR REMOTES
```bash
$ git pull <remote> <local-branch>
```
Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy. This is the same as git fetch <remote> followed by git merge origin/<current-branch>
```bash
$ git pull <remote>
```
Same as pull command, but instead of using git merge to integrate the remote branch with the local one, use git rebase
```bash
$ git pull --rebase <remote>
```



PUSHING TO YOUR REMOTES
To push a local branch (current branch)
```bash
$ git push
```
To push to the branch of the same name on the remote. This creates a local branch (remote branch for us) in the destination repository
```bash
$ git push <remote> <local-branch>
```
To push to the branch of the same name on the remote. This creates a local branch (remote branch for us) in the destination repository
```bash
$ git push <remote> <local-branch> <remote-branch>
```
To push a local branch and set the remote as upstream
```bash
$ git push -u <remote> <local-branch>
           --set-upstream <remote> <local-branch>
```
Makes the head of the branch point at your personal history, ignoring any changes that may have occurred in parallel with yours
```bash
$ git push -f <remote> <commit>:<local-branch>
           --force
```
It refuses to update a branch unless it is the state that we expect; i.e. nobody has updated the branch upstream
```bash
$ git push --force-with-lease
```
Pushes up the repo and its refs for the first time
```bash
$ git push -u <remote> --all
```
Git obtains the current branch name from HEAD
```bash
$ git push <remote> HEAD
```
Push all refs under refs/heads/
```bash
$ git push --all
```
Push all refs under refs/heads/ and refs/tags/ and delete non-existing refs
```bash
$ git push --mirror
```



ADDING REMOTES
Create a new connection to a remote repository. After adding a remote, you’ll be able to use <remote> as a convenient shortcut for <url> in other Git commands. HTTP is an easy way to allow anonymous, read-only access to a repository. For read-write access, you should use SSH instead
```bash
$ git remote add <remote> <url>
```

EDITING REMOTES
// TODO
```bash
$ git remote set-url <remote> <url
```

RENAMING REMOTES
// TODO
```bash
$ git remote rename <old-remote> <new-remote>
```

REMOVING REMOTES
// TODO
```bash
$ git remote rm <remote>
```

LISTING YOUR REMOTES
List remote names
```bash
$ git remote
```
List remote names and url
```bash
$ git remote -v
```
List remote names
```bash
$ git remote show
```

SHOWING INFORMATION ABOUT A REMOTE
Explicitly tells you which local branches are tracking which remote branches
```bash
$ git remote show <remote>
```




LISTING BRANCHES
List the local branches
```bash
$ git branch
```
List the remote-tracking branches
```bash
$ git branch -r
```
Show sha1 and commit subject line for each head, along with relationship to upstream branch (if any)
```bash
$ git branch -v
```
If given twice, print the name of the upstream branch, as well (see also git remote show <remote>)
```bash
$ git branch -vv
```
List both remote-tracking branches and local branches
```bash
$ git branch -a
             --all
```
Which branches are already merged into HEAD (i.e. the branch you're on)
```bash
$ git branch --merged
```
Lists branches merged into <branch>
```bash
$ git branch --merged <branch>
```
All the branches that contain work you haven't yet merged in. By default this applies to only the local branches.
The -a flag will show both local and remote branches, and the -r flag shows only the remote branches.
```bash
$ git branch --no-merged
 ```

CREATING BRANCHES
Creates a new branch
```bash
$ git branch <branch>
```
Creates a new branch and set up a remote branch to track
```bash
$ git branch --track <branch> <remote>/<remote-branch>
```
Creates a new branch from a remote branch and no tracking any remote branch
```bash
$ git branch --no-track <branch> <remote>/<remote-branch>
```
Creates a new branch from commit and no tracking and no tracking any remote branch
```bash
$ git branch --no-track <branch> <commit>
```
Creates a new branch and switching to it
```bash
$ git checkout -b <branch>
```
Creates a new branch from a local branch and switching to it
```bash
$ git checkout -b <branch> <local-branch>
```
Creates a new branch from a remote branch with a specific name and switching to it
```bash
$ git checkout -b <branch> <remote>/<remote-branch>
```
Creates a new branch from a remote branch with a specific name and switching to it without tracking
```bash
$ git checkout -b <branch> <remote>/<remote-branch> --no-track
```
Creates a new branch from a remote branch and switching to it
```bash
$ git checkout <remote-branch>
```



TRACKING BRANCHES
// TODO
```bash
$ git branch -u <remote>/<remote-branch>
             --set-upstream-to
```
// TODO
```bash
$ git branch <local-branch> -u <remote>/<remote-branch>
```
Stop tracking remote branch
```bash
$ git branch --unset-upstream
```



SWITCHING TO ANOTHER BRANCH
// TODO
```bash
$ git checkout <branch>
```
Quickly jump back to previous branch.
```bash
$ git checkout -
```


DELETING BRANCHES
Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes
```bash
$ git branch -d <local-branch>
```
Force delete the specified branch, even if it has unmerged changes
```bash
$ git branch -D <local-branch>
```
Deletes remote branch
```bash
$ git push <remote> --delete <branch>
```
Deletes remote branch
```bash
$ git push <remote> :<branch>
```



RENAMING BRANCHES
// TODO
```bash
$ git branch -m <old-local-branch-name> <new-local-branch-name>
```
If you want to rename the current branch
```bash
$ git branch -m <new-local-branch-name>
```



MERGING BRANCHES
// TODO
```bash
$ git merge <remote>/<remote-branch>
```
You can merge your changes if you are on
```bash
$ git merge <local-branch> <another-local-branch>
```
The --no-ff flag causes the merge to always create a new commit object. This avoids losing information.
```bash
$ git merge --no-ff <local-branch>
```
// TODO
```bash
$ git merge --abort
```



MERGED BRANCHES
// TODO
```bash
$ git branch --merged
```
List all branches that are already merged into
```bash
$ git branch --merged <local-branch> <local-branch>
```
// TODO
```bash
$ git branch -r --merged
```


REMOVING MERGED BRANCHES
To delete any branches that have been merged into the currently checked out branch
```bash
$ git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```



GETTING THE NAME OF CURRENT BRANCH
// TODO
```bash
$ git rev-parse --abbrev-ref HEAD
```






VIEWING DETAIL ABOUT A COMMIT
It shows details of the most recent commit
```bash
$ git show
```
It shows details of the most recent commit
```bash
$ git show HEAD
```
List filenames without the diffs
```bash
$ git show HEAD --name-only
```
It shows details of the last fetch
```bash
$ git show FETCH_HEAD
```
It shows details of a particular commit number
```bash
$ git show <commit>
```
Reference a commit via commit message pattern matching
```bash
$ git show :/<commit>
```
It shows details of a particular stash
```bash
$ git show stash@{n}
```
It shows details of a file on a branch
```bash
$ git show <branch>:<file>
```
It shows details of a file on a branch
```bash
$ git show <commit>:<file>
```
Exporting to file
```bash
$ git show <branch>:<file> > <path>
```
It shows branches and their commits
```bash
$ git show-branch
```



FINDING COMMITS NOT MERGED UPSTREAM
Find commits yet to be applied to upstream
```bash
$ git cherry <branch>
```
Find commits yet to be applied to upstream with additional information
```bash
$ git cherry -v <branch>
             --verbose
```



VIEWING THE STATE HISTORY
Contains information about the old state of branches and allows you to go back to that state if necessary. Using git reset it is then possible to change back to the commit it was before
```bash
$ git reflog
```
Show the reflog with relative date information (e.g. 2 weeks ago).
```bash
$ git reflog --relative-date
```



SEEING CHANGES FOR A FILE
// TODO
```bash
$ git gitk <file>
```





## Tagging
### Creating Tags
Git uses two main types of tags: lightweight and annotated.
#### Annotated Tags
```bash
$ git tag -a <tag-name> -m "<message>"
```
#### Lightweight Tags
```bash
$ git tag <tag-name>
```

### Searching Tags
Search for tags with a particular pattern.
```bash
$ git tag -l "v1.8.5*"
```

### Tagging Later
Tag specific commit.
```bash
$ git tag <tag-name> <commit>
```

### Sharing Tags
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

### Deleting Tags
#### Local Tag
```bash
$ git tag -d <tag-name>
          --delete
```
#### Remote Tag
```bash
$ git push <remote> :<tag-name>
```

### Seeing
Seeing tag data.
```
$ git show <tag-name>
```
Seeing tag message.
```bash
$ git tag -n
```
Showing the most recent tag on the current branch.
```bash
$ git describe --tags --abbrev=0
```

### Listing Tags
This command lists the tags in alphabetical order
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



CREATING BACKUPS
// TODO
```bash
$ git archive HEAD --format=zip > <name>.zip
```
// TODO
```bash
$ git archive HEAD | gzip > <name>.tar.gz
```
// TODO
```bash
$ git archive <local-branch> --format=zip --output=<name>.zip
```



IGNORING CHANGES TO A TRACKED FILE
Temporarily ignore changes
```bash
$ git update-index --assume-unchanged <file>
```
Track changes again
```bash
$ git update-index --no-assume-unchanged <file>
```
Files that should never be tracked are listed in your .gitignore file.
What about if you want to ignore some local changes to a tracked file?


LISTING IGNORED FILES
// TODO
```bash
$ git check-ignore *
```



EXPORTING A BRANCH WITH HISTORY TO A FILE
// TODO
```bash
$ git bundle create <file> <branch-name>
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



SHOWING REPOSITORY CHANGES
Run a quick web server, open a browser
```bash
$ git instaweb --httpd=webrick
```



SEARCHING COMMITED CODE
// TODO
```bash
$ git grep <pattern>
```



IMPORTING FROM A BUNDLE
// TODO
```bash
$ git clone repo.bundle <repo-dir> -b <branch-name>
```



COUNTING UNPACKED NUMBER OF OBJECTS AND THEIR DISK CONSUMPTION
// TODO
```bash
$ git count-objects --human-readable
```


NUMBER OF COMMITS OF EACH CONTRIBUTOR
```bash
$ git shortlog -s -n
```


```bash
cat .git/config
```
~/.gitconfig file: Specific to your user. You can make Git read and write to this file specifically by passing the --global option
config file in the git directory (that is, .git/config). Each level overrides values in the previous level



GETTING HELP
```bash
$ git help <command>
```
// TODO
```bash
$ git <command> --help
```



GETTING THE VERSION
```bash
$ git --version
```
