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
3. [Getting a Git Repository](#getting-a-git-repository)
    * [Initializing a Repository](#initializing-a-repository)
    * [Initializing a Shared Repository](#initializing-a-shared-repository)
4. [Adding Changes](#adding-changes)
    * [Tracking New or Modified Files](#tracking-new-or-modified-files)
    * [Interactive Staging](#interactive-staging)
6. [Removing Files](#removing-files)
5. [Tagging](#tagging)
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
6. [Submodules](#submodules)
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
$ git config --global --list
                      -l
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

## Getting a Git Repository
### Initializing a Repository
Create empty git repository or re-initialize an existing one.
```bash
$ git init
```
Create empty git repository in directory
```bash
$ git init <directory>
```

### Initializing a Shared Repository
Create a repository that doesn’t have a working directory, making it impossible to edit files and commit changes in that repository.
```bash
$ git init --bare
```

## Adding Changes
### Tracking New or Modified Files
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

### Interactive Staging
Staging only untracked files.
```bash
$ git add -i
          --interactive
#   Type a (for "add untracked")
#   Then * (for "all")
#   Then q (to quit)
```

## Removing Files
Remove file from the working tree.
```bash
$ git rm <file>
```
Remove recursively directory the working tree.
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
Remove files from the working tree.
```bash
$ git rm $(git ls-files --deleted)
```



RENAMING FILES
1st. way
mv <old-name> <new-name>
git rm <old-name>
git add <new-name>

2nd. way
git mv <file-from> <file-to>



COMMITTING YOUR CHANGES
Stage all modified and deleted paths
```bash
$ git commit -a
             --all
```
Stage all files that have been modified and deleted, but new files you have not told git about are not affected
```bash
$ git commit -am "<message>"
```
// TODO
```bash
$ git commit -m "<message>" \ --author="Name <your_email@youremail.com>"
```
// TODO
```bash
$ git commit -m "<message>"
             --mesage
```
Show unified diff of all file changes
```bash
$ git commit -v
             --verbose
```
If you want to check in which files a commit is going to be incorporated
```bash
$ git commit --dry-run --short
```

SKIPPING STAGING AREA DURING COMMIT
This only works with tracked files
```bash
$ git commit --only <file>
```



CLONING AN EXISTING REPOSITORY
Clone the repository in the current directory
```bash
$ git clone <repository>
```
Clone the repository inside of directory
The question: "how do I clone a repo and set the remote name to something other that origin?"
```bash
$ git clone <repository> <directory>
```
Clone a repository and set the remote name
```bash
$ git clone --origin <new-remote-name> <repository>
```

CLONING A SINGLE BRANCH
```bash
$ git clone -b <branch> --single-branch <repository>
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






LISTING CHANGED FILES IN YOUR WORKING DIRECTORY
```bash
$ git status
```
Output in short format
```bash
$ git status -s
             --short
```
Status of ignored files
```bash
$ git status --ignored
```


SHOWING DIFFERENCES
What's different from our most recent commit
```bash
$ git diff
```
What's different from our most recent commit (staged and unstaged changes)
```bash
$ git diff HEAD
```
What's different from our previous commit
```bash
$ git diff HEAD~1
         HEAD^1
         HEAD^
```
 What's different from two previous commits
 ```bash
$ git diff HEAD^2
```
What's different from two previous commits
```bash
$ git diff HEAD^^
```
It compares your staged changes against your HEAD (last commit)
```bash
$ git diff --cached
           --staged
```
Differences between two commits
```bash
$ git diff <commit> <commit>
```
Prints out diff
```bash
$ git diff > <file>
```
Show inline word diff
```bash
$ git diff --word-diff
```
diff the same file between two different commits on the same branch
```bash
$ git diff <commit> HEAD <file>
```
diff the same file between two different commits on the same branch
```bash
$ git diff <commit>..HEAD -- <file>
```
diff the same file between two different commits on the same branch
```bash
$ git diff <commit> HEAD -- <file>
```


SEEING INFORMATION ABOUT FILES IN INDEX/WORKING DIRECTORY
// TODO
```bash
$ git ls-files
```
Show all tracked files
```bash
$ git ls-files -t
```
Show staged files
```bash
$ git ls-files -s
               --stage
```
Show deleted files
```bash
$ git ls-files -d
               --deleted
```
Show untracked files
```bash
$ git ls-files -o
               --others
```
Show modified files
```bash
$ git ls-files -m
               --modified
```
Show ignored files
```bash
$ git ls-files --others --ignored --exclude-from=.git/info/exclude
```
Show ignored files
```bash
$ git ls-files --others --ignored --exclude-standard
```
Show untracked files
```bash
$ git ls-files --exclude-standard --others
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



BLAMING CHANGES
Tells you who last modified each line of a file and which commit made the change
```bash
$ git blame <file>
```
Annotate only the given line range
```bash
$ git blame -L <starting-line>,<ending-line> <file>
```



BINARY SEARCH
// TODO
```bash
$ git bisect start
```
// TODO
```bash
$ git bisect bad
```
// TODO
```bash
$ git bisect good
```
// TODO
```bash
$ git bisect reset
```
// TODO
```bash
$ git bisect log
```
// TODO
```bash
$ git bisect log > bisect.log
```



SHOWING REPOSITORY CHANGES
Run a quick web server, open a browser
```bash
$ git instaweb --httpd=webrick
```



AVOIDING COMMIT A HALF-DONE WORK
Create a new stash
```bash
$ git stash
```
Create a new stash with message
```bash
$ git stash save "<message>"
```
Saving current state including untracked files
```bash
$ git stash save -u
                 --include-untracked
```
Listing stashed you have stored in your stack
```bash
$ git stash list
```
Reapply a specific stash
```bash
$ git stash apply stash@{n}
```
Remove a single stashed state from the stash list
```bash
$ git stash drop stash@{n}
```
Reapply and remove the last stash
```bash
$ git stash pop
```
Remove all the stashed states
```bash
$ git stash clear
```
Show changed files from the latest stash
```bash
$ git stash show
```
Show changed files
```bash
$ git stash show stash@{n}
```
Show changed files and diff in patch format
```bash
$ git stash show -p stash@{n}
```
Staging stashes interactively
```bash
$ git stash -p
```
Stashing only unstaged changes
```bash
$ git stash -k
```
Stashing untracked files
```bash
$ git stash -u
            --untracked
```
// TODO
```bash
$ git stash --keep-index
```
// TODO
```bash
$ git stash --no-keep-index
```




REVERTING FILES
Returns the state of your unstaged files as they were in your last commit
```bash
$ git checkout .
```
Returns the state of your unstaged files that match the regular expression as they were in your last commit (required to escape with backslash the expression)
```bash
$ git checkout \*.storyboard
```
Returns the state of your unstaged files as they were in your HEAD (last commit)
```bash
$ git checkout HEAD
```
Returns the state of your unstaged files as they were in the previous commit of HEAD
```bash
$ git checkout HEAD^
```
Returns the state of your file as it was in your last commit
```bash
$ git checkout <file>
```
Returns the state of your file as it was in your last commit but if you have a file and a branch named the same, we will need to use this syntax
```bash
$ git checkout -- <file>
```
This turns the <file> that resides in the working directory into an exact copy of the one from <commit> and adds it to the staging area
```bash
$ git checkout <commit> <file>
```
Update all files in the working directory to match the specified commit. This will put you in a detached HEAD state
```bash
$ git checkout <commit> .
```
This turns the <file> that resides in the working directory into an exact copy of the one from stash@{n} and adds it to the staging area
```bash
$ git checkout stash@{n} <file>
```
Interactively select hunks in diff
```bash
$ git checkout -p
```
Interactively select hunks in diff for a specific file
```bash
$ git checkout -p <file>
```

RESTORING DELETED FILE
```bash
$ git checkout <deleting-commit>^ -- <file_path>
```



UNSTAGING A STAGED FILE
This unstages all files and leave the working directory unchanged
```bash
$ git reset
```
This unstages all files and leave the working directory unchanged
```bash
$ git reset HEAD
```
Unstaging a file
```bash
$ git reset <file>
```
This can be used in reverse when removing changes from the index
```bash
$ git reset -p
```

REMOVING COMMIT TO A KNOWN STATE
Do not touch the index file nor the working tree
```bash
$ git reset --soft
```
Reset the index but not the working tree (default)
```bash
$ git reset --mixed
```
Match the working tree and index to the given tree
```bash
$ git reset --hard
```
Like --hard, but keep local working tree changes
```bash
$ git reset --keep
```
Move the current branch to <commit>. All changes made since <commit> will reside in the working directory, which lets you re-commit the project history. NEVER reset to commits that have been pushed to a public repository
```bash
$ git reset <commit>
```



REVERTING COMMIT
Generate a new commit that undoes all of the changes introduced in the commit, then apply it to the current branch
```bash
$ git revert <commit>
```
Cancel the revert operation
```bash
$ git revert --abort
```


REVERTING MERGE COMMIT
We specify the merge using the SHA1 hash of the merge commit. The -m followed by the 1 indicates that we want to keep the parent side of the merge (the branch we are merging into)
```bash
$ git revert -m 1 <commit>
```



REVERTING INITIAL COMMIT
```bash
$ git update-ref -d HEAD
```



REMOVING UNTRACKED DIRECTORIES/FILES
```bash
$ git clean
```
If the git configuration variable clean.requireForce is not set to false, git clean will refuse to run unless given -f or -n
```bash
$ git clean -f
            --force
```
Don’t actually remove anything, just show what would be done
```bash
$ git clean -n
```
Forcefully remove untracked directory
```bash
$ git clean -f -d
            -fd
```
If you are clearing out untracked files, you can double check what files are going to be deleted with the dry run flag
```bash
$ git clean -fd --dry-run
```
Cleaning the files from .gitignore
```bash
$ git clean -X -f
```
Interactive mode
```bash
$ git clean -i
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
Checkout previous branch
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



VIEWING THE COMMIT HISTORY
Show all commits
```bash
$ git log
```
Show changes over time for a specific file
```bash
$ git log <file>
```
Generate diff in patch format for a specific file
```bash
$ git log -p <file>
```
If want to see the entire history
```bash
$ git log --follow <file>
```
If want to see the entire history of the file (including history beyond renames and with diffs for each change)
```bash
$ git log --follow -p <file>
```
Exports a git log to a text file
```bash
$ git log > <file>
```
Show only commits that occur in the range. Both arguments can be either a commit ID, a branch name, HEAD, or any other kind of revision reference
```bash
$ git log <commit>..<commit>
```
Maximum number of commits to display
```bash
$ git log -n
```
// TODO
```bash
$ git log --max-count
```
Limits the number of commits to show
```bash
$ git log -n -n
```
Condense each commit to a single line. This is useful for getting a high-level overview of the project history
```bash
$ git log --oneline
```
Include which files were altered and the relative number of lines that were added or deleted from each of them
```bash
$ git log --stat
```
// TODO
```bash
$ git log --shortstat
```
// TODO
```bash
$ git log --summary
```
Search for commits by a particular author. The argument can be a plain string or a regular expression
```bash
$ git log --author="<pattern>"
```
Search for commits with a commit message that matches <pattern> , which can be a plain string or a regular expression
```bash
$ git log --grep="<pattern>"
```
// TODO
```bash
$ git log --graph --decorate ﻿--oneline
```
// TODO
```bash
$ git log --graph --pretty=oneline --abbrev-commit
```
// TODO
```bash
$ git log --pretty=oneline
```
What changed since two weeks?
```bash
$ git log --no-merges --raw --since='2 weeks ago'
```
// TODO
```bash
$ git log <origin>/<remote-branch>
```
Last commit a file appeared in. This same command will even work for files that have been deleted if you know the path and name of the file in question
```bash
$ git log -1 <file>
```
Number of commits of each contributor
```bash
$ git shortlog -s -n
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
