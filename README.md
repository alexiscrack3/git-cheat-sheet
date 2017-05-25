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

## Settings
### Setting Global Configs
Set your username for every repository
```bash
$ git config --global user.name "<name>"
```
Set your email for every repository
```bash
$ git config --global user.email "<email>"
```
Color output of capable git commands. value: true, false, auto
```bash
$ git config --global color.ui <value>
```
A boolean to make git-clean do nothing unless given -f, -i or -n. Defaults to true. Possible values: true, false
```bash
$ git config --global clean.requireForce <value>
```
Make git case sensitive. Possible values: true, false
```bash
$ git config --global core.ignorecase <value>
```
Defines the action git push should take. Possible values: nothing, matching, upstream, current, simple (safest option and is well-suited for beginners)
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
Get all your global configs
```bash
$ git config --global --list
                      -l
```
Get global username
```bash
$ git config --global user.name
```
Get global email
```bash
$ git config --global user.email
```

### Removing Global Configs
Remove global username
```bash
$ git config --global --unset user.name
```
Remove global email
```bash
$ git config --global --unset user.email
```

### Setting Local Configs
Set your username for current repository
```bash
$ git config user.name "<name>"
```
Set your email for current repository
```bash
$ git config user.email "<email>"
```

### Getting Local Configs
Get username
```bash
$ git config --get user.name
```
Get email
```bash
$ git config --get user.email
```

### Removing Local Configs
Remove username
```bash
$ git config --unset user.name
```
Remove email
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






INITIALIZING A REPOSITORY
```bash
git init
```
```bash
git init <directory>
```

INITIALIZING A SHARED REPOSITORY
Creates a repository that doesn’t have a working directory, making it impossible to edit files and commit changes in that repository.
```bash
git init --bare
```


STAGING NEW OR MODIFIED FILE
Add all files
```bash
git add .
```
Add a specific file
```bash
git add <file>
```
Add a specific directory
```bash
git add <directory>
```
Add files with an extension file
```bash
git add *.<extension>
```
Add to index modified and deleted tracked files but it will never stage new files
```bash
git add -u
```
Begin an interactive staging session that lets you choose portions of a file to add to the next commit
```bash
git add -p
        --patch
        #    y - stage this hunk
        #    n - do not stage this hunk
        #    q - quit; do not stage this hunk nor any of the remaining ones
        #    a - stage this hunk and all later hunks in the file
        #    d - do not stage this hunk nor any of the later hunks in the file
        #    g - select a hunk to go to
        #    / - search for a hunk matching the given regex
        #    j - leave this hunk undecided, see next undecided hunk
        #    J - leave this hunk undecided, see next hunk
        #    k - leave this hunk undecided, see previous undecided hunk
        #    K - leave this hunk undecided, see previous hunk
        #    s - split the current hunk into smaller hunks
        #    e - manually edit the current hunk
        #    ? - print help
```
```bash
git add -p <file>
```
Add to index modified files
```bash
git add $(git ls-files --modified)
```

STAGING ONLY UNTRACKED FILES
Type a (for "add untracked")
Then * (for "all")
Then q (to quit)
```bash
git add -i
```



REMOVING A FILE
It removes deleted files from your staging area
```bash
git rm $(git ls-files --deleted)
```
It only removes a file from index but not from disk
```bash
git rm --cached <file>
```
It only removes recursively files from index but not from disk
```bash
git rm --cached -r <directory>
```
It removes recursively from index
```bash
git rm <directory> -r
```
```bash
git rm <file>
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
git commit --all
            -a
```
```bash
git commit -am "<message>"      // Stage all files that have been modified and deleted, but new files you have not told git about are not affected
```
```bash
git commit -m "<message>" \ --author="Name <your_email@youremail.com>"
```
```bash
git commit -m "<message>"
           --mesage
```
```bash
git commit -v                   // Show unified diff of all file changes
           --verbose
```
```bash
git commit --dry-run --short    // If you want to check in which files a commit is going to be incorporated
```

SKIPPING STAGING AREA DURING COMMIT
```bash
git commit --only <file> // This only works with tracked files
```



CLONING AN EXISTING REPOSITORY
```bash
git clone <repository>              // Clone the repository in the current directory
```
```bash
git clone <repository> <directory>  // Clone the repository inside of directory
The question: "how do I clone a repo and set the remote name to something other that origin?"
```
```bash
git clone --origin <new-remote-name> <repository> // Clone a repository and set the remote name
```

CLONING A SINGLE BRANCH
```bash
git clone -b <branch> --single-branch <repository>
```


```bash
cat .git/config
```
~/.gitconfig file: Specific to your user. You can make Git read and write to this file specifically by passing the --global option
config file in the git directory (that is, .git/config). Each level overrides values in the previous level



GETTING HELP
```bash
git help <command>
```
```bash
git <command> --help
```



GETTING THE VERSION
```bash
git --version
```






LISTING CHANGED FILES IN YOUR WORKING DIRECTORY
```bash
git status
```
```bash
git status -s           // Output in short format
           --short
```
```bash
git status --ignored    // Status of ignored files
```


SHOWING DIFFERENCES
```bash
git diff                    // What's different from our most recent commit
```
```bash
git diff HEAD               // What's different from our most recent commit (staged and unstaged changes)
```
```bash
git diff HEAD~1             // What's different from our previous commit
         HEAD^1
         HEAD^
         HEAD^2             // What's different from two previous commits
         HEAD^^             // What's different from two previous commits
```
```bash
git diff --cached           // It compares your staged changes against your HEAD (last commit)
         --staged
```
```bash
git diff <commit> <commit>  // Differences between two commits
```
```bash
git diff > <file>           // Prints out diff
```
```bash
git diff --word-diff        // Show inline word diff
```
```bash
git diff <commit> HEAD <file>       // diff the same file between two different commits on the same branch
```
```bash
git diff <commit>..HEAD -- <file>   // diff the same file between two different commits on the same branch
```
```bash
git diff <commit> HEAD -- <file>    // diff the same file between two different commits on the same branch
```


SEEING INFORMATION ABOUT FILES IN INDEX/WORKING DIRECTORY
```bash
git ls-files
```
```bash
git ls-files -t         // Show all tracked files
```
```bash
git ls-files -s         // Show staged files
             --stage
```
```bash
git ls-files -d         // Show deleted files
             --deleted
```
```bash
git ls-files -o         // Show untracked files
             --others
```
```bash
git ls-files -m         // Show modified files
             --modified
```
```bash
git ls-files --others --ignored --exclude-from=.git/info/exclude // Show ignored files
```
```bash
git ls-files --others --ignored --exclude-standard               // Show ignored files
```
```bash
git ls-files --exclude-standard --others                         // Show untracked files
```



SHOWING ALL COMMITS TO BE MERGED
```bash
git cherry -v <local-branch> // Show all commits in the current branch yet to be merged to <local-branch>
```
```bash
git cherry -v <local-branch> <branch-to-be-merged>
```
```bash
git log <branch-to-be-merged> ^<local-branch>
```



BLAMING CHANGES
```bash
git blame <file>            // Tells you who last modified each line of a file and which commit made the change
```
```bash
git blame -L <starting-line>,<ending-line> <file> // Annotate only the given line range
```



BINARY SEARCH
```bash
git bisect start
```
```bash
git bisect bad
```
```bash
git bisect good
```
```bash
git bisect reset
```
```bash
git bisect log
```
```bash
git bisect log > bisect.log
```



SHOWING REPOSITORY CHANGES
```bash
git instaweb --httpd=webrick // run a quick web server, open a browser
```



AVOIDING COMMIT A HALF-DONE WORK
```bash
git stash                   // Create a new stash
```
```bash
git stash save "<message>"  // Create a new stash with message
```
```bash
git stash save -u           // Saving current state including untracked files
               --include-untracked
```
```bash
git stash list              // Listing stashed you have stored in your stack
```
```bash
git stash apply stash@{n}   // Reapply a specific stash
```
```bash
git stash drop stash@{n}    // Remove a single stashed state from the stash list
```
```bash
git stash pop               // Reapply and remove the last stash
```
```bash
git stash clear             // Remove all the stashed states
```
```bash
git stash show              // Show changed files from the latest stash
```
```bash
git stash show stash@{n}    // Show changed files
```
```bash
git stash show -p stash@{n} // Show changed files and diff in patch format
```
```bash
git stash -p                // Staging stashes interactively
```
```bash
git stash -k                // Stashing only unstaged changes
```
```bash
git stash -u                // Stashing untracked files
          --untracked
```
```bash
git stash --keep-index
```
```bash
git stash --no-keep-index
```




REVERTING FILES
```
```bash
git checkout .                  // Returns the state of your unstaged files as they were in your last commit
```
```bash
git checkout \*.storyboard      // Returns the state of your unstaged files that match the regular expression as they were in your last commit (required to escape with backslash the expression)
```
```bash
git checkout HEAD               // Returns the state of your unstaged files as they were in your HEAD (last commit)
```
```bash
git checkout HEAD^              // Returns the state of your unstaged files as they were in the previous commit of HEAD
```
```bash
git checkout <file>             // Returns the state of your file as it was in your last commit
```
```bash
git checkout -- <file>          // Returns the state of your file as it was in your last commit but if you have a file and a branch named the same, we will need to use this syntax
```
```bash
git checkout <commit> <file>    // This turns the <file> that resides in the working directory into an exact copy of the one from <commit> and adds it to the staging area
```
```bash
git checkout <commit> .         // Update all files in the working directory to match the specified commit. This will put you in a detached HEAD state
```
```bash
git checkout stash@{n} <file>   // This turns the <file> that resides in the working directory into an exact copy of the one from stash@{n} and adds it to the staging area
```
```bash
git checkout -p                 // Interactively select hunks in diff
```
```bash
git checkout -p <file>          // Interactively select hunks in diff for a specific file
```

RESTORING DELETED FILE
```bash
git checkout <deleting-commit>^ -- <file_path>
```



UNSTAGING A STAGED FILE
```bash
git reset           // This unstages all files and leave the working directory unchanged
```
```bash
git reset HEAD      // This unstages all files and leave the working directory unchanged
```
```bash
git reset <file>    // Unstaging a file
```
```bash
git reset -p        // This can be used in reverse when removing changes from the index
```

REMOVING COMMIT TO A KNOWN STATE
```bash
git reset --soft    // Do not touch the index file nor the working tree
```
```bash
git reset --mixed   // Reset the index but not the working tree (default)
```
```bash
git reset --hard    // Match the working tree and index to the given tree
```
```bash
git reset --keep    // Like --hard, but keep local working tree changes
```
```bash
git reset <commit>  // Move the current branch to <commit>. All changes made since <commit> will reside in the working directory, which lets you re-commit the project history. NEVER reset to commits that have been pushed to a public repository
```



REVERTING COMMIT
```bash
git revert <commit> // Generate a new commit that undoes all of the changes introduced in the commit, then apply it to the current branch
```
```bash
git revert --abort  // Cancel the revert operation
```
```bash


REVERTING MERGE COMMIT
```bash
git revert -m 1 <commit>    // We specify the merge using the SHA1 hash of the merge commit. The -m followed by the 1 indicates that we want to keep the parent side of the merge (the branch we are merging into).
```



REVERTING INITIAL COMMIT
```bash
git update-ref -d HEAD
```
```bash



REMOVING UNTRACKED DIRECTORIES/FILES
```bash
git clean
```
```bash
git clean -f           // If the git configuration variable clean.requireForce is not set to false, git clean will refuse to run unless given -f or -n
          --force
```
```bash
git clean -n            // Don’t actually remove anything, just show what would be done
```
```bash
git clean -f -d         // Forcefully remove untracked directory
          -fd
```
```bash
git clean -fd --dry-run // If you are clearing out untracked files, you can double check what files are going to be deleted with the dry run flag
```
```bash
git clean -X -f         // Cleaning the files from .gitignore
```
```bash
git clean -i            // Interactive mode
```





ADDING FORGOTTEN FILE TO LAST COMMIT
```bash
git add <file>
```
```bash
git commit --amend              // Add forgotten file and lets you edit the previous commit's message
```
```bash
git commit --amend --no-edit    // Add forgotten file without changing its commit message
```

CHANGING YOUR LAST COMMIT
```bash
git commit --amend // Change your commit message using the terminal
```
```bash
git commit --amend -m "New commit message" // Changes your commit message. NEVER amend commits that have been pushed to a public repository
```
```bash
git commit --amend --author='<name> <email>' // Amend author
```
```bash
git commit -v --amend   // Reword the previous commit
```



MOVING THE LATEST COMMIT TO A NEW BRANCH
```bash
git checkout -b <new-branch>
```
```bash
git reset --hard HEAD~
```



REBASING COMMITS
```bash
git rebase <branch>     // Rebase your current HEAD onto branch. NEVER rebase published commits
```
```bash
git rebase --abort      // Abort a rebase
```
```bash
git rebase --continue   // Continue a rebase after resolving conflicts
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
```bash
git checkout --theirs <file>    // Finish with git add <file> and git commit
```
```bash
git checkout --ours <file>      // Finish with git add <file> and git commit
```



COPYING COMMITS
```bash
git cherry-pick <commit>    // Jump into the branch that you want to insert the commit into
```
```bash
git cherry-pick <branch>    // Introduce particular commits from one branch onto a different branch
```
```bash
git cherry-pick --abort
```
```bash
git cherry-pick --continue
```
```bash
git cherry-pick --quit
```




FECTHING FROM YOUR REMOTES
```bash
git fetch                           // When no remote is specified, by default the origin remote will be used
```
```bash
git fetch --all                     // Fetch all remotes
```
```bash
git fetch <remote>                  // Fetch all of the branches from the repository to see what everybody else has been working on. It has absolutely no affect on your local development work because it doesn’t force you to merge changes. When you finish to review changes you have to merge remote branch to a local branch
```
```bash
git fetch <remote> <local-branch>   // Fetch the specified branch
```
```bash
git fetch -p                        // After fetching, remove any remote-tracking references that no longer exist on the remote
          --prune
```



PULLING FROM YOUR REMOTES
```bash
git pull <remote> <local-branch>
```
```bash
git pull <remote>           // Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy. This is the same as git fetch <remote> followed by git merge origin/<current-branch>
```
```bash
git pull --rebase <remote>  // Same as pull command, but instead of using git merge to integrate the remote branch with the local one, use git rebase
```



PUSHING TO YOUR REMOTES
```bash
git push                                            // To push a local branch (current branch).
```
```bash
git push <remote> <local-branch>                    // To push to the branch of the same name on the remote. This creates a local branch (remote branch for us) in the destination repository
```
```bash
git push <remote> <local-branch> <remote-branch>    // To push to the branch of the same name on the remote. This creates a local branch (remote branch for us) in the destination repository
```
```bash
git push -u <remote> <local-branch>                 // To push a local branch and set the remote as upstream
         --set-upstream <remote> <local-branch>
```
```bash
git push -f <remote> <commit>:<local-branch>        // Makes the head of the branch point at your personal history, ignoring any changes that may have occurred in parallel with yours.
         --force
```
```bash
git push --force-with-lease                         // It refuses to update a branch unless it is the state that we expect; i.e. nobody has updated the branch upstream
```
```bash
git push -u <remote> --all                          // Pushes up the repo and its refs for the first time
```
```bash
git push <remote> HEAD                              // Git obtains the current branch name from HEAD
```
```bash
git push --all                                      // Push all refs under refs/heads/
```
```bash
git push --mirror                                   // Push all refs under refs/heads/ and refs/tags/ and delete non-existing refs
```



ADDING REMOTES
```bash
git remote add <remote> <url>    // Create a new connection to a remote repository. After adding a remote, you’ll be able to use <remote> as a convenient shortcut for <url> in other Git commands. HTTP is an easy way to allow anonymous, read-only access to a repository. For read-write access, you should use SSH instead
```

EDITING REMOTES
```bash
git remote set-url <remote> <url
```

RENAMING REMOTES
```bash
git remote rename <old-remote> <new-remote>
```

REMOVING REMOTES
```bash
git remote rm <remote>
```

LISTING YOUR REMOTES
```bash
git remote      // List remote names
```
```bash
git remote -v   // List remote names and url
```
```bash
git remote show // List remote names
```

SHOWING INFORMATION ABOUT A REMOTE
```bash
git remote show <remote> // Explicitly tells you which local branches are tracking which remote branches
```




LISTING BRANCHES
```bash
git branch              // List the local branches
```
```bash
git branch -r           // List the remote-tracking branches
```
```bash
git branch -v           // Show sha1 and commit subject line for each head, along with relationship to upstream branch (if any)
           -vv          // If given twice, print the name of the upstream branch, as well (see also git remote show <remote>)
```
```bash
git branch -a           // List both remote-tracking branches and local branches
           --all
```
```bash
git branch --merged             // Which branches are already merged into HEAD (i.e. the branch you're on)
```
```bash
git branch --merged <branch>    // Lists branches merged into <branch>
```
```bash
git branch --no-merged          // All the branches that contain work you haven't yet merged in
/* By default this applies to only the local branches.
   The -a flag will show both local and remote branches,
   and the -r flag shows only the remote branches.
 */
 ```

CREATING BRANCHES
```bash
git branch <branch>                                             // Creates a new branch
```
```bash
git branch --track <branch> <remote>/<remote-branch>            // Creates a new branch and set up a remote branch to track
```
```bash
git branch --no-track <branch> <remote>/<remote-branch>         // Creates a new branch from a remote branch and no tracking any remote branch
```
```bash
git branch --no-track <branch> <commit>                         // Creates a new branch from commit and no tracking and no tracking any remote branch
```
```bash
git checkout -b <branch>                                        // Creates a new branch and switching to it
```
```bash
git checkout -b <branch> <local-branch>                         // Creates a new branch from a local branch and switching to it
```
```bash
git checkout -b <branch> <remote>/<remote-branch>               // Creates a new branch from a remote branch with a specific name and switching to it
```
```bash
git checkout -b <branch> <remote>/<remote-branch> --no-track    // Creates a new branch from a remote branch with a specific name and switching to it without tracking
```
```bash
git checkout <remote-branch>                                    // Creates a new branch from a remote branch and switching to it
```



TRACKING BRANCHES
```bash
git branch -u <remote>/<remote-branch>
           --set-upstream-to
```
```bash
git branch <local-branch> -u <remote>/<remote-branch>
```
```bash
git branch --unset-upstream // Stop tracking remote branch
```



SWITCHING TO ANOTHER BRANCH
```bash
git checkout <branch>
```
```bash
git checkout - // Checkout previous branch
```


DELETING BRANCHES
```bash
git branch -d <local-branch>        // Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes
```
```bash
git branch -D <local-branch>        // Force delete the specified branch, even if it has unmerged changes
```
```bash
git push <remote> --delete <branch> // Deletes remote branch
```
```bash
git push <remote> :<branch>         // Deletes remote branch
```



RENAMING BRANCHES
```bash
git branch -m <old-local-branch-name> <new-local-branch-name>
```
```bash
git branch -m <new-local-branch-name> // If you want to rename the current branch
```



MERGING BRANCHES
```bash
git merge <remote>/<remote-branch>
git merge <local-branch>            // You can merge your changes if you are on <another-local-branch>
```
```bash
git merge --no-ff <local-branch>    // The --no-ff flag causes the merge to always create a new commit object. This avoids losing information.
```
```bash
git merge --abort
```



MERGED BRANCHES
```bash
git branch --merged
```
```bash
git branch --merged <local-branch> // List all branches that are already merged into <local-branch>
```
```bash
git branch -r --merged
```


REMOVING MERGED BRANCHES
```bash
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d   // To delete any branches that have been merged into the currently checked out branch
```



GETTING THE NAME OF CURRENT BRANCH
```bash
git rev-parse --abbrev-ref HEAD
```



VIEWING THE COMMIT HISTORY
```bash
git log                         // Show all commits
```
```bash
git log <file>                  // Show changes over time for a specific file
```
```bash
git log -p <file>               // Generate diff in patch format for a specific file
```
```bash
git log --follow <file>         // If want to see the entire history
```
```bash
git log --follow -p <file>      // If want to see the entire history of the file (including history beyond renames and with diffs for each change).
```
```bash
git log > <file>                // Exports a git log to a text file
```
```bash
git log <commit>..<commit>      // Show only commits that occur in the range. Both arguments can be either a commit ID, a branch name, HEAD, or any other kind of revision reference.
```
```bash
git log -n                      // Maximum number of commits to display
```
```bash
git log --max-count
```
```bash
git log -n -n                   // Limits the number of commits to show
```
```bash
git log --oneline               // Condense each commit to a single line. This is useful for getting a high-level overview of the project history
```
```bash
git log --stat                  // Include which files were altered and the relative number of lines that were added or deleted from each of them
```
```bash
git log --shortstat
```
```bash
git log --summary
```
```bash
git log --author="<pattern>"    // Search for commits by a particular author. The argument can be a plain string or a regular expression
```
```bash
git log --grep="<pattern>"      // Search for commits with a commit message that matches <pattern> , which can be a plain string or a regular expression
```
```bash
git log --graph --decorate ﻿--oneline
```
```bash
git log --graph --pretty=oneline --abbrev-commit
```
```bash
git log --pretty=oneline
```
```bash
git log --no-merges --raw --since='2 weeks ago' // What changed since two weeks?
```
```bash
git log <origin>/<remote-branch>
```
```bash
git log -1 <file> // Last commit a file appeared in. This same command will even work for files that have been deleted if you know the path and name of the file in question.
```
```bash
git shortlog -s -n              // Number of commits of each contributor
```



VIEWING DETAIL ABOUT A COMMIT
```bash
git show                    // It shows details of the most recent commit
```
```bash
git show HEAD               // It shows details of the most recent commit
```
```bash
git show HEAD --name-only   // List filenames without the diffs
```
```bash
git show FETCH_HEAD         // It shows details of the last fetch
```
```bash
git show <commit>           // It shows details of a particular commit number
```
```bash
git show :/<commit>         // Reference a commit via commit message pattern matching
```
```bash
git show stash@{n}          // It shows details of a particular stash
```
```bash
git show <branch>:<file>    // It shows details of a file on a branch
```
```bash
git show <commit>:<file>    // It shows details of a file on a branch
```
```bash
git show <branch>:<file> > <path> // Exporting to file
```
```bash
git show-branch             // It shows branches and their commits
```



FINDING COMMITS NOT MERGED UPSTREAM
```bash
git cherry <branch> // Find commits yet to be applied to upstream
```
```bash
git cherry -v <branch> // Find commits yet to be applied to upstream with additional information
           --verbose
```



VIEWING THE STATE HISTORY
```bash
git reflog                  // Contains information about the old state of branches and allows you to go back to that state if necessary. Using git reset it is then possible to change back to the commit it was before
```
```bash
git reflog --relative-date  // Show the reflog with relative date information (e.g. 2 weeks ago).
```



SEEING CHANGES FOR A FILE
```bash
gitk <file>
```






ANNOTATING TAGS
```bash
git tag <tag-name>
```
```bash
git tag <tag-name> <commit> // Tag specific commit
```
```bash
git tag -a <tag-name> -m "<message>"
```

PUSHING TAGS
```bash
git push <remote> <tag>
```
```bash
git push <remote> --tags // Tags are not automatically pushed when you push a branch or use the --all option. The --tags flag sends all of your local tags to the remote repository
```
```bash
git push --follow-tags
```

DELETING LOCAL TAG
```bash
git tag --delete <tag-name>
        -d
```

DELETING REMOTE TAG
```bash
git push <remote> :<tag-name>
```

LISTING YOUR TAGS
```bash
git tag
```

SEEING TAG DATA
```
git show <tag-name>
```

SEEING TAG MESSAGE
```bash
git tag -n
```


SHOWING THE MOST RECENT TAG ON THE CURRENT BRANCH
```bash
git describe --tags --abbrev=0
```





ADDING A SUBMODULE TO PROJECT
```bash
git submodule init
```
```bash
git submodule add <url> <directory>
```
```bash
git submodule update --init --recursive
```

CLONING A PROJECT WITH SUBMODULES
1st. way
```bash
git clone --recursive <repository>  // Clone an existing repository and all its sub-modules recursively
```

2nd. way
```bash
git clone <repository>  // Our folder module will be empty
```
```bash
git submodule init      // Initialize the local config file
```
```bash
git submodule update    // Retrieves data
```




CREATING BACKUPS
```bash
git archive HEAD --format=zip > <name>.zip
```
```bash
git archive HEAD | gzip > <name>.tar.gz
```
```bash
git archive <local-branch> --format=zip --output=<name>.zip
```



IGNORING CHANGES TO A TRACKED FILE
```bash
git update-index --assume-unchanged <file> // Temporarily ignore changes
```
```bash
git update-index --no-assume-unchanged <file> // Track changes again
```
Files that should never be tracked are listed in your .gitignore file.
What about if you want to ignore some local changes to a tracked file?


LISTING IGNORED FILES
```bash
git check-ignore *
```



EXPORTING A BRANCH WITH HISTORY TO A FILE
```bash
git bundle create <file> <branch-name>
```



SEARCHING COMMITED CODE
```bash
git grep <pattern>
```



IMPORTING FROM A BUNDLE
```bash
git clone repo.bundle <repo-dir> -b <branch-name>
```



COUNTING UNPACKED NUMBER OF OBJECTS AND THEIR DISK CONSUMPTION
```bash
git count-objects --human-readable
```
