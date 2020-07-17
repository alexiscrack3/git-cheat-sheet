# Git Cheat Sheet

A collection of some of the most useful Git commands

## Table of Contents

1. [Settings](#settings)
    * [Setting Configs](#setting-configs)
    * [Getting Configs](#getting-configs)
    * [Removing Configs](#removing-configs)
2. [Setting Up Repository](#setting-up-repository)
    * [Initializing Repository](#initializing-repository)
    * [Cloning Repository](#cloning-repository)
3. [Saving Changes](#saving-changes)
    * [Adding Files](#adding-files)
    * [Removing Files](#removing-files)
    * [Renaming Files](#renaming-files)
    * [Committing Files](#committing-files)
    * [Stashing Files](#stashing-files)
4. [Inspecting Changes](#inspecting-changes)
    * [Display State](#display-state)
    * [Display Objects](#display-objects)
    * [Logging](#logging)
    * [Display Differences](#display-differences)
    * [Blaming](#blaming)
5. [Listing Files](#listing-files)
6. [Undoing Changes](#undoing-changes)
    * [Reverting Files](#reverting-files)
    * [Reverting Commit](#reverting-commit)
    * [Unstaging Staged File](#unstaging-staged-file)
    * [Resetting Current Commit](#resetting-current-commit)
    * [Removing Untracked Files](#removing-untracked-files)
7. [Rewriting History](#rewriting-history)
    * [Fix Up Commit](#fix-up-commit)
    * [Rebase Commits](#rebase-commits)
    * [Copy Commits](#copy-commits)
8. [Synchronize](#synchronize)
    * [Remotes](#remotes)
    * [Fetching](#fetching)
    * [Pulling](#pulling)
    * [Pushing](#pushing)
9. [Branches](#branches)
    * [Create Branches](#create-branches)
    * [Rename Branches](#rename-branches)
    * [Delete Branches](#delete-branches)
    * [List Branches](#list-branches)
    * [Merge Branches](#merge-branches)
    * [Track Branches](#track-branches)
    * [Switch to Branch](#switch-to-branch)
10. [Debugging](#debugging)
    * [Binary Search](#binary-search)
11. [Tagging](#tagging)
12. [Submodules](#submodules)
13. [Refs and the Reflog](#refs-and-the-reflog)
    * [Hashes](#hashes)
    * [Refs](#refs)
    * [Special Refs](#special-refs)
    * [Relative Refs](#relative-refs)
    * [Reflog](#reflog)
14. [Others](#others)
15. [Getting Help](#getting-help)

## Settings

There are 3 configuration levels:

* User-specific settings. Options set with the --global flag are stored in ~/.gitconfig
* Repository-specific settings. Options set with or without the --local flag are stored in \<repo\>/.git/config
* System-wide settings. Options set with the --system flag are stored in $(prefix)/etc/gitconfig

### Setting Configs

Set repository option.

```bash
git config [<config-level>] [--add] name value
```

Adds a new line to the option without altering any existing values.

```bash
--add name value
```

Create an alias for git commands.

```bash
alias.* '<command>'
```

A boolean to make git-blame show email in output.

```bash
blame.showEmail value
```

A boolean to make git-clean do nothing unless given -f, -i or -n. Possible values: true, false

```bash
clean.requireForce value
```

Turn on/off all Git’s colored terminal output. Possible values: true, false, auto.

```bash
color.ui value
```

Set up default text editor.

```bash
core.editor value
```

Makes git case sensitive. Possible values: true, false.

```bash
core.ignorecase value
```

Sets a diff algorithm. Possible values: default, histogram, minimal, myers, patience.

```bash
diff.algorithm value
```

Specify the style in which conflicted hunks are written out to working tree files upon merge. The default is "merge", which shows a <<<<<<< conflict marker, changes made by one side, a ======= marker, changes made by the other side, and then a >>>>>>> marker. An alternate style, "diff3", adds a ||||||| marker and the original text before the ======= marker.

```bash
merge.conflictstyle value
```

Set up your custom merge resolution and diff tools.

```bash
merge.tool value
```

Defines the action git push should take. Possible values: nothing, matching, upstream, current, simple (safest option and is well-suited for beginners).

```bash
push.default value
```

When set to true, automatically create a temporary stash entry before the operation begins, and apply it after the operation ends. Possible values: true, false.

```bash
rebase.autostash value
```

Show full by default diff when using git stash show. Possible values: true, false.

```bash
stash.showPatch value
```

Show files which are not currently tracked by Git. Directories which contain only untracked files, are shown with the directory name only. Showing untracked files means that Git needs to lstat() all the files in the whole repository, which might be slow on some systems. So, this variable controls how the commands displays the untracked files.

```bash
status.showUntrackedFiles value
```

Set username.

```bash
user.name value
```

Set email.

```bash
user.email value
```

Open the configuration file in a text editor for manual editing.

```bash
-e
--edit
```

### Getting Configs

Get repository option.

```bash
git config [<config-level>] [--show-origin] [--get] name
```

Augment the output of all queried config options with the origin type (file, standard input, blob, command line) and the actual origin (config file path, ref, or blob id if applicable).

```bash
--show-origin
```

Get repository options.

```bash
git config [<config-level>] [--show-origin] -l --list
```

Augment the output of all queried config options with the origin type (file, standard input, blob, command line) and the actual origin (config file path, ref, or blob id if applicable).

```bash
--show-origin
```

List all variables set in config file, along with their values.

```bash
-l
--list
```

### Removing Configs

Remove repository options.

```bash
git config [<file-option>] --unset name
```

Remove the line matching the key from config file.

```bash
--unset name
```

## Setting Up Repository

### Initializing Repository

Create an empty Git repository or reinitialize an existing one.

```bash
git init [--template=<template_directory>] [--bare] [directory]
```

Specify the directory from which templates will be used.

```bash
--template=<template_directory>
```

Create a bare repository.

```bash
--bare
```

### Cloning Repository

Clone a repository into a current directory if not specified.

```bash
git clone [-o <name>] [-b <name>]
          [--depth <depth>] [--single-branch]
          [--recursive]
          [--template=<template_directory>]
          <repository> [<directory>]
```

Instead if using the remote name **origin** to keep track of the upstream repository, use **<name>**.

```bash
-o <name>
--origin <name>
```

Instead of pointing the newly created HEAD to the branch pointed to by the cloned repository’s HEAD, point to <name> branch instead.

```bash
-b <name>
--branch <name>
```

Clone only history leading up to the main branch or the one specified by -b option.

```bash
--single-branch
```

Clone repository and all its submodules recursively.

```bash
--recursive
```

Clone the repository and apply template.

```bash
--template=<template_directory>
```

Clone the repository and only clone the history of commits specified by the option depth. If depth is equal to one, only the most recent commit is included.

```bash
--depth=<depth>
```

## Saving Changes

### Adding Files

Add file contents to the index.

```bash
git add [-n | --dry-run] [-f | --force] [-u | --update]
        [-i | --interactive] [-p | --patch]
        [<pathspec>…]
```

Do not actually add files; only show which ones would be added.

```bash
-n
--dry-run
```

Allow adding otherwise ignored files.

```bash
-f
--force
```

Add to index modified and deleted tracked files but it will never stage new files.

```bash
-u
--update
```

Begin an interactive staging session that lets you choose portions of a file to add to the next commit.

You can select one of the following options and type return:

* y - stage this hunk
* n - do not stage this hunk
* q - quit; do not stage this hunk nor any of the remaining ones
* a - stage this hunk and all later hunks in the file
* d - do not stage this hunk nor any of the later hunks in the file
* g - select a hunk to go to
* / - search for a hunk matching the given regex
* j - leave this hunk undecided, see next undecided hunk
* J - leave this hunk undecided, see next hunk
* k - leave this hunk undecided, see previous undecided hunk
* K - leave this hunk undecided, see previous hunk
* s - split the current hunk into smaller hunks
* e - manually edit the current hunk
* ? - print help

```bash
-p
--patch
```

Staging only untracked files.

List of available subcommands.

* Type a (for "add untracked")
* Then * (for "all")
* Then q (to quit)

```bash
-i
--interactive
```

Add modified files to index.

```bash
git add $(git ls-files --modified)
```

### Removing Files

Remove file from the working directory.

```bash
git rm [-n | --dry-run] [-r] [--] <pathspec>…
```

Do not actually remove the files, just show if they exist in the index.

```bash
-n
--dry-run
```

Remove recursively directory from the working directory.

```bash
-r
```

This option can be used to separate command-line options from the list of files, (useful when filenames might be mistaken for command-line options).

```bash
--
```

Remove a file from index but not from disk.

```bash
--cached
```

Remove files from the working directory.

```bash
git rm $(git ls-files --deleted)
```

### Renaming Files

Move or rename a file, a directory, or a symlink.

```bash
git mv <source> <destination>
```

Alternate way to move or rename a file, directory or symlink.

```bash
mv <old-name> <new-name>
git rm <old-name>
git add <new-name>
```

### Committing Files

Record changes to the repository.

```bash
git commit [-a | --all] [-m <msg> | --message <msg>]
           [-v | --verbose] [-n | --dry-run] [-o | --only]
           [--allow-empty] [--author=<author>]
```

Stage all modified and deleted paths, but new files you have not told git about are not affected.

```bash
-a
--all
```

Use the given message as the commit message.

```bash
-m <msg>
--message <msg>
```

Use the given message as the commit message and override the author name used in the commit.

```bash
--author=<author>
```

Allow recording an empty commit with no file changes.

```bash
--allow-empty
```

Show unified diff of all file changes.

```bash
-v
--verbose
```

Do not create a commit, but show a list of paths that are to be committed.

```bash
-n
--dry-run
```

Skip staging area and commit files, this only works with tracked files.

```bash
-o
--only
```

### Stashing Files

Stash away changes to dirty working directory.

```bash
git stash [-p | --patch] [-k | --[no-]keep-index] [-u | --include-untracked]
```

Interactively select hunks from diff between HEAD and the working tree to stashed.

```bash
-p
--patch
```

Stash only unstaged changes.

```bash
-k
--keep-index
```

All changes already added to the index are undone.

```bash
--no-keep-index
```

Save local changes including untracked files.

```bash
-u
--include-untracked
```

List the stashes stored in the stack.

```bash
git stash list
```

Show the changes recorded in the stash as a diff. Latest stash is used if stash is not provided.

```bash
git stash show [-p | --patch] [<stash>]
```

Show the changes recorded in the stash as a diff in patch format.

```bash
-p
--patch
```

Save local changes to a new stash with message.

```bash
git stash save [<message>]
```

Apply the changes recorded in the stash.

```bash
git stash apply [<stash>]
```

Remove and apply a single stashed state from the stack.

```bash
git stash pop
```

Creates and checks out a new branch named starting from the commit at which the stash was originally created, applies the changes recorded in stash to the new working tree and index, then drops the stash. Latest stash is used if stash is not provided.

```bash
git stash branch <name> [<stash>]
```

Remove a single stashed state from the stack.

```bash
git stash drop [<stash>]
```

Remove all the stashed states.

```bash
git stash clear
```

## Inspecting Changes

### Display State

Show working directory status.

```bash
git status [-s | --short] [-u [<mode>] | --untracked-files [<mode>]] [--ignored] [--] [<pathspec>…]
```

Give the output in short format.

```bash
-s
--short
```

Show untracked files.

The mode parameter is used to specify the handling of untracked files. It is optional: it defaults to **all**.

The possible options are:

* no - Show no untracked files.
* normal - Shows untracked files and directories.
* all - Also shows individual files in untracked directories.

```bash
-u [<mode>]
--untracked-files
```

Status of ignored files.

```bash
--ignored
```

This option can be used to separate command-line options from the list of files, (useful when filenames might be mistaken for command-line options).

```bash
--
```

### Display Objects

Show details of the object (blobs, trees, tags and commits).

```bash
git show [-w | --ignore-all-space]
         [--name-only] [--name-status]
         [--stat] [--pretty | --format=<format>]
         [<object>…]
```

Ignore white space when comparing lines.

```bash
-w
--ignore-all-space
```

Show only names of changed files without the diffs.

```bash
--name-only
```

Show only names and status of changed files without the diffs.

```bash
--name-status
```

Generate diffstat instead of patch.

```bash
--stat
```

Show details of an object with pretty format.

```bash
--pretty <object>
--format=<format> <object> 
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

### Logging

Show commit logs.

```bash
git log [-p | --patch] [[-n | --max-count] <number>]
        [--follow] [--first-parent]
        [--oneline]
        [--stat] [--shortstat] [--summary]
        [--[no-]merges] [--author=<pattern>] [--grep=<pattern>]
        [<pathspec>…]
```

Generate diff in patch format for a specific file.

```bash
-p
--patch
```

Limit the number of commits to output.

```bash
-n
--max-count
```

Show changes over time for a specific file even if the file was renamed.

```bash
--follow
```

Follow only the first parent commit upon seeing a merge commit. This option can give a better overview when viewing the evolution of a particular topic branch, because merges into a topic branch tend to be only about adjusting to updated upstream from time to time, and this option allows you to ignore the individual commits brought in to your history by such a merge.

```bash
--first-parent
```

Condense each commit to a single line.

```bash
--oneline
```

Show statistics for files modified in each commit.

```bash
--stat
```

Display only the changed/insertions/deletions line from the --stat command.

```bash
--shortstat
```

Generate condensed summary of extended header information.

```bash
--summary
```

Display only merge commits.

```bash
--merges
```

Display commits without merge commits.

```bash
--no-merges
```

Search for commits by a particular author. The argument can be a plain string or a regular expression.

```bash
--author=<pattern>
```

Search for commits with a commit message. The argument can be a plain string or a regular expression.

```bash
--grep=<pattern>
```

Get a list of commits made in the last two weeks.

```bash
git log --since='2 weeks'
```

Show only commits that occur in the range.

```bash
git log <since>..<until>
```

Match regexps ignoring case.

```bash
git log [-i <regex> | --regexp-ignore-case <regex>]
```

Maximum number of commits to display.

```bash
git log [-n <number> | --max-count <number>]
```

Show what every contributor has been getting up to across all branches.

```bash
git log --all --oneline --no-merges
```

Show changes since two weeks.

```bash
git log --no-merges --raw --since='2 weeks ago'
```

Generate a changelog.

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
git shortlog [--all] [--no-merges] [-s] [-n]
```

Summarize commits of all refs.

```bash
--all
```

Summarize commits and supress the ones with more than one parent (merge commits).

```bash
--no-merges
```

Summarize commits and suppress commit message.

```bash
-s
--summary
```

Sort according to number of commits.

```bash
-n
--numbered
```

Number of commits of each contributor and ensures that merge commits aren’t being counted.

```bash
git shortlog --all --no-merges -sn 
```

### Display Differences

Show changes between commits, commit and working tree, etc.

```bash
git diff [<options>] [<object>]
```

Show changes between two arbitrary commits.

```bash
git diff [<options>] <commit> <commit> [--] [<path>…]
```

This is synonymous to the previous form. If <commit> on one side is omitted, it will have the same effect as using HEAD instead.

```bash
git diff [<options>] <commit>..<commit> [--] [<path>…]
```

This form is to view the changes on the branch containing and up to the second <commit>, starting at a common ancestor of both <commit>. You can omit any one of <commit>, which has the same effect as using HEAD instead.

```bash
git diff [<options>] <commit>..<commit> [--] [<path>…]
```

Ignore white space when comparing lines.

```bash
-w
--ignore-all-space
```

Show staged changes against your HEAD.

```bash
--cached
--staged
```

Show inline word diff.

```bash
--word-diff
```

Look for differences whose added or removed line matches the given pattern.

```bash
-G <pattern>
```

### Blaming

Show what revision and author last modified each line of a file.

```bash
git blame [-n | --show-number] [-s]
          [-e | --show-email] [-w]
          [-L <range>] [-M] [-C]
          <file>
```

Show the line number in the original commit (Default: off).

```bash
-n
--show-number
```

Suppress the author name and timestamp from the output.

```bash
-s
```

Show the author email instead of author name (Default: off).

```bash
-e
--show-email
```

Ignore whitespace when comparing the parent’s version and the child’s to find where the lines came from.

```bash
-w
```

Restrict the output to the requested line range.

```bash
-L <starting-line>,<ending-line>
```

Detect moved or copied lines within in the same file. This will report the original author of the lines instead of the last author that moved or copied the lines.

```bash
-M
```

Detect lines that were moved or copied from other files. This will report the original author of the lines instead of the last author that moved or copied the lines.

```bash
-C
```

## Listing Files

Show information about files in the index and the working directory.

```bash
git ls-files [-t] [-v]
             (--[cached | deleted | others | ignored | stage | modified])*
		     (-[c | d | o | i | s | m])*
             [--exclude-standard]
```

Show cached files.

```bash
-c
--cached
```

Show deleted files.

```bash
-d
--deleted
```

Show all untracked or ignored files.

```bash
-o
--others
```

Show only ignored files in the output. When showing files in the index, print only those matched by an exclude pattern. When showing "other" files, show only those matched by an exclude pattern.

```bash
-i
--ignored
```

Show staged contents (mode bits, object name and stage number).

```bash
-s
--stage
```

Show modified files.

```bash
-m
--modified
```

This option identifies the file status with the following tags.

You can select one of the following options and type return:

* H - cached
* S - skip-worktree
* M - unmerged
* R - removed/deleted
* C - modified/changed
* K - to be killed
* ? - other

```bash
-t
```

Similar to -t, but use lowercase letters for files that are marked as assume unchanged.

```bash
-v
```

Add the standard Git exclusions: .git/info/exclude, .gitignore in each directory, and the user’s global exclusion file.

```bash
--exclude-standard
```

Show all untracked files.

```bash
--others --exclude-standard
```

Show all ignored files.

```bash
--others --ignored --exclude-standard
```

## Undoing Changes

### Reverting Files

Return the state of your unstaged files as they were before.

```bash
git checkout (-p | --patch) [--] [<pathspec>…]
```

Interactively select hunks in diff.

```bash
-p
--patch
```

This option can be used to separate command-line options from the list of files, (useful when filenames might be mistaken for command-line options).

```bash
--
```

This turns the file that resides in the working directory into an exact copy of the one from object (commit, branch, etc).

```bash
git checkout [<object>] [<pathspec>…]
```

Update all files in the working directory to match the specified commit. This will put you in a detached HEAD state.

```bash
git checkout <commit> .
```

This turns the file that resides in the working directory into an exact copy of the one from stash@{n} and adds it to the staging area.

```bash
git checkout stash@{n} <file>
```

The contents from a specific side of the merge can be checked out of the index.

```bash
git checkout [--ours | --theirs] [<tree-ish>]
```

Gives the version from the branch that holds your work that is being rebased.

```bash
--theirs
```

Gives the version from the branch the changes are rebased onto.

```bash
--ours
```

### Reverting Commit

Generate a new commit that undoes all of the changes introduced in the commit.

```bash
git revert [-e | --edit] [--no-edit] [-n | --no-commit]  <commit>…
```

This is a default option and doesn't need to be specified. This option will open the configured system editor and prompts you to edit the commit message prior to committing the revert.

```bash
-e
--edit
```

This is the inverse of the -e option. The revert will not open the editor.

```bash
--no-edit
```

Passing this option will prevent git revert from creating a new commit that inverses the target commit. Instead of creating the new commit this option will add the inverse changes to the Staging Index and Working Directory.

```bash
-n
--no-commit
```

Sequencer subcommands.

```bash
git revert (--continue | --skip | --abort | --quit)
```

Continue the operation in progress using the information in .git/sequencer. Can be used to continue after resolving conflicts in a failed cherry-pick or revert.

```bash
--continue
```

Skip the current commit and continue with the rest of the sequence.

```bash
--skip
```

Skip the current commit and continue with the rest of the sequence.

```bash
--abort
```

Skip the current commit and continue with the rest of the sequence.

```bash
--quit
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
git reset [-p | --patch] [<pathspec>]
```

Select diff hunks to remove from the index.

```bash
-p
--patch
```

Unstage all files and leave the working directory unchanged.

```bash
git reset HEAD
```

Restore specified path in the working tree.

```bash
git restore --staged <file>
```

### Resetting Current Commit

Reset current HEAD to the specified state.

```bash
git reset [--soft | --mixed | --hard | --keep] [<commit>]
```

Do not reset the index file nor the working directory.

```bash
--soft
```

Reset the index but not the working directory (default).

```bash
--mixed
```

Reset the index and working directory to the given commit.

```bash
--hard
```

Like --hard, but keep local working directory changes.

```bash
--keep
```

Get back to where things were a period of time ago (e.g. when you screw up a merge).

```bash
git reset --hard master@{"300 minutes ago"}
```

### Removing Untracked Files

Remove untracked files from working tree.

```bash
git clean [-d] [-f | --force] [-i | --interactive] [-n | --dry-run] [-x | -X] <path>…
```

Normally, when no <path> is specified, git clean will not recurse into untracked directories to avoid removing too much. Specify -d to have it recurse into such directories as well. If any paths are specified, -d is irrelevant.

```bash
-d
```

Required when clean.requireForce is true (default).

```bash
-f
--force
```

Only show what would and what would not be removed.

```bash
-n
--dry-run
```

Show what would be done and clean files interactively.

```bash
-i
--interactive
```

Don’t use the standard ignore rules, but still use the ignore rules given with -e options from the command line.

```bash
-x
```

Remove only files ignored by Git. This may be useful to rebuild everything from scratch, but keep manually created files.

```bash
-X
```

## Rewriting History

### Fix Up Commit

Record changes.

```bash
git commit [--amend] [--no-edit]
           [--author=<author>] [--reset-author]
           [--reuse-message=<commit>]
```

Add forgotten files and edit the last commit's message.

```bash
--amend
```

Use the selected commit message without launching an editor.

```bash
--no-edit
```

Override the author name used in the commit.

```bash
--author="Name <your_email@youremail.com>"
```

The author of the resulting commit now belongs to the committer.

```bash
--reset-author
```

Take an existing commit object, and reuse the log message and the authorship information (including the timestamp) when creating the commit.

```bash
--reuse-message=<commit>
```

### Rebase Commits

Reapply commits on top of another base tip.

```bash
git rebase [-i | --interactive] [--autostash] [--root] [<branch>]
```

Rebase the current branch onto branch.

```bash
-i
--interactive
```

Automatically stashes any local changes made to your working copy before rebasing and reapplies them after the rebase is completed.

```bash
--autostash
```

Rebase to the root commit of your current branch.

```bash
--root
```

It is possible that a merge failure will prevent this process from being completely automatic. You will have to resolve any such merge failure and run an option.

```bash
git rebase (--continue | --abort)
```

After resolving the conflict manually and updating the index with the desired resolution, you can continue the rebasing process.

```bash
--continue
```

Abort the rebase operation and reset HEAD to the original branch. If <branch> was provided when the rebase operation was started, then HEAD will be reset to <branch>. Otherwise HEAD will be reset to where it was when the rebase operation was started.

```bash
--abort
```

### Copy Commits

Apply the changes introduced by some existing commits.

```bash
git cherry-pick (--continue | --skip | --quit | --abort)
```

Continue the operation in progress using the information in .git/sequencer. Can be used to continue after resolving conflicts in a failed cherry-pick or revert.

```bash
--continue
```

Skip the current commit and continue with the rest of the sequence.

```bash
--skip
```

End revert or cherry-pick sequence.

```bash
--quit
```

Cancel revert or cherry-pick sequence.

```bash
--abort
```

Commits to cherry-pick.

```bash
git cherry-pick <commit>…
```

Introduce particular commits from one branch onto a different branch.

```bash
git cherry-pick <branch>
```

## Synchronize

### Remotes

List remote names.

```bash
git remote [-v | --verbose]
```

Show remote url after name.

```bash
-v
--verbose
```

Create a new connection to a remote repository. HTTP is an easy way to allow anonymous, read-only access to a repository. For read-write access, you should use SSH instead.

```bash
git remote add <remote> <url>
```

Remove a remote and all associated tracking branches.

```bash
git remote rm <remote>
```

Change URL for a remote.

```bash
git remote set-url <remote> <url>
```

Retrieves the URLs for a remote.

```bash
git remote get-url <remote>
```

Rename a remote and update all associated tracking branches.

```bash
git remote rename <old-remote> <new-remote>
```

Show information about a given remote.

```bash
git remote show <remote>
```

### Fetching

Fetch objects and refs from repository. It has absolutely no affect on local development work because it doesn’t force to merge changes. When no remote is specified, by default the origin remote will be used.

```bash
git fetch [-p | --prune] [<remote> [<refspec>…]]
```

Remove any remote-tracking references that no longer exist on the remote.

```bash
-p
--prune
```

Fetch objects and refs from all remotes.

```bash
git fetch --all
```

Merge remote branch into local branch without having to checkout local branch first.

```bash
git fetch origin <remote-branch>:<local-branch>
```

Merge local branch into local branch master without having to checkout master first. Here `.` means to use the local repository as the remote.

```bash
git fetch . <remote-branch>:<local-branch>
```

Fetch from all remotes, not just one.

```bash
git remote update
```

### Pulling

Fetch from and integrate with another repository or a local branch.

```bash
git pull [-r | --rebase] [<remote> [<refspec>…]]
```

Rebase the current branch on top of the upstream branch after fetching.

```bash
-r
--rebase
```

### Pushing

Update remote refs along with associated objects.

```bash
git push [--all | --mirror | --tags] [-n | --dry-run]
         [-f | --force] [--force-with-lease[=<refname>[:<expect>]]]
         [-u | --set-upstream]
         [<remote> [<refspec>…]]
```

Push all branches (i.e. refs under refs/heads/).

```bash
--all
```

Push all refs under refs/heads/ refs/remotes, and refs/tags/ and delete non-existing refs.

```bash
--mirror
```

All refs under refs/tags are pushed, in addition to refspecs explicitly listed on the command line.

```bash
--tags
```

Do everything except actually send the updates.

```bash
-n
--dry-run
```

Usually, the push command refuses to update a remote ref that is not an ancestor of the local ref used to overwrite it. This flag disables these checks, and can cause the remote repository to lose commits; use it with care.

```bash
-f
--force
```

Usually, the push command refuses to update a remote ref that is not an ancestor of the local ref used to overwrite it. This option overrides this restriction if the current value of the remote ref is the expected value. "git push" fails otherwise.

```bash
--force-with-lease
```

Push a local branch and set the remote as upstream.

```bash
-u
--set-upstream
```

Make the head of the branch point at your personal history, ignoring any changes that may have occurred in parallel with yours.

```bash
git push -f <remote> <commit>:<local-branch>
         --force
```

## Branches

### Create Branches

Create new branch.

```bash
git branch [-t | --track | --no-track] <branch> [<start-point>]
```

When creating a new branch, set up configuration entries to mark the start-point branch as "upstream" from the new the branch.

```bash
--track
```

Do not set up "upstream" configuration.

```bash
--no-track
```

Create new branch.

```bash
git checkout [[-b | -B] <new-branch> [-t | --track | --no-track] <start-point>]
```

Causes a new branch to be created as if git-branch were called and then checked out.

```bash
-b
-B
```

### Rename Branches

Rename a branch and the corresponding reflog.

```bash
git branch (-m | -M | --move) [<oldbranch>] <newbranch>
```

Rename a branch and the corresponding reflog.

```bash
-m
-M
--move
```

### Delete Branches

Delete a branch.

```bash
git branch (-d | -D) [-r] <branch>…​
```

Delete the specified branch if it doesn't have unmerged changes.

```bash
-d
--delete
```

Delete the specified branch even if it has unmerged changes.

```bash
-D
```

Delete remote branch from repository.

```bash
git push <remote> --delete <branch>
```

Delete remote branch from repository.

```bash
git push <remote> :<branch>
```

Delete local branches that have been merged into the current branch.

```bash
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```

### List Branches

List local branches.

```bash
git branch [-v | -vv | --verbose]
           [--sort=<key>]
           [(--merged | --no-merged) [<object>]]
           [--contains [<commit]] [--no-contains [<commit>]]
           [(-r | --remotes) | (-a | --all)]
```

Show SHA-1 and commit subject line for each head.

```bash
-v
-vv
--verbose
```

List local branches, ordered by least recent commit.

```bash
--sort=committerdate
```

List local branches, ordered by most recent commit.

```bash
--sort=-committerdate
```

Only list branches which are fully contained by object.

```bash
--merged
```

Do not list branches which are fully contained by object.

```bash
--no-merged
```

Only list branches which contain the specified commit (HEAD if not specified).

```bash
--contains
```

Only list branches which don’t contain the specified commit (HEAD if not specified).

```bash
--no-contains
```

List only remote branches.

```bash
-r
--remotes
```

List both remote and local branches.

```bash
-a
--all
```

List local branches, ordered by most recent commit.

```bash
git for-each-ref --sort=-committerdate refs/heads/
```

Show branches and their commits.

```bash
git show-branch
```

### Merge Branches

Join two or more development histories together

```bash
git merge [--ff | --no-ff] [--squash] [<commit>…]
```

Specifies how a merge is handled when the merged-in history is already a descendant of the current history.

```bash
--ff
```

Generate a merge commit (3-way merge) even if the merge resolved as a fast-forward.

```bash
--no-ff
```

Takes all the commits from a branch, squash them into 1 commit, and merge it with another branch.

```bash
--squash
```

Merge the last checked out branch.

```bash
git merge -
```

Sequencer subcommands.

```bash
git merge (--continue | --abort | --quit)
```

Continue merge operation after a git merge stops due to conflicts.

```bash
--continue
```

Restore the original branch and abort the merge operation.

```bash
--abort
```

Forget about the current merge in progress.

```bash
--quit
```

### Track Branches

Make local branches to track branches.

```bash
git branch (--set-upstream-to=<upstream> | -u <upstream>) [<branch>]
```

Branch will start tracking remote branch.

```bash
-u
--set-upstream-to
```

Remove the upstream information. If no branch is specified it defaults to the current branch.

```bash
git branch --unset-upstream [<branch>]
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

Use binary search to find the commit that introduced a bug.

```bash
git bisect (start | bad | good | reset | log | replay)
```

Reset bisection state and start a new bisection.

```bash
git bisect start
```

Mark current or given revision as bad.

```bash
bad
```

Mark current or given revision as good.

```bash
good
```

Finish bisection search and return to the given branch (or master).

```bash
reset
```

Show the log of the current bisection.

```bash
log
```

Replay a bisection log.

```bash
replay
```

## Tagging

Create tag object signed with GPG.

```bash
git tag [-a] [(-m | --mesage) <msg>] <tagname> [<commit> | <object>]
```

Create annotated tag.

```bash
-a
```

Use the given tag message.

```bash
-m
--message
```

Create lightweight tag.

```bash
git tag <tagname>
```

List tags in alphabetical order.

```bash
git tag
```

List tags.

```bash
git tag [-n] [-l | --list] [<pattern>…​]
```

Search for tags with a particular pattern.

```bash
-l
--list
```

Show tag message.

```bash
-n
```

Delete local tag.

```bash
git tag (-d | --delete) <tagname>…​
```

Delete remote tag.

```bash
git push <remote> :<tagname>
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

Show the most recent tag on the current branch.

```bash
git describe --tags --abbrev=0
```

## Submodules

Add given repository as a submodule.

```bash
git submodule add <url> [<path>]
```

Initialize submodules recorded in the index by setting the submodule name in .git/config.

```bash
git submodule init [<path>…​]
```

Update the registered submodules to match what the superproject expects by cloning missing submodules and updating the working tree of the submodules.

```bash
git submodule update [--init] [--remote] [<path>…​]
```

Initialize all submodules for which "git submodule init" has not been called so far before updating.

```bash
--init
```

Instead of using the superproject’s recorded SHA-1 to update the submodule, use the status of the submodule’s remote-tracking branch.

```bash
--remote
```

Deinitialize submodule from repository.

```bash
git submodule deinit [-f | --force] (--all | <path>…​)
```

The submodule’s working tree will be removed even if it contains local modifications.

```bash
-f
--force
```

Unregister all submodules.

```bash
--all
```

Show the status of the submodules.

```bash
git submodule status [<path>…​]
```

Prints out a summary of the difference between the submodule's HEAD and the one recorded in main repository.

```bash
git submodule summary [<path>…​]
```

Copy the new configuration from .gitmodules to .git/config

```bash
git submodule sync [<path>…​]
```

Evaluate shell command in each checked-out submodule.

```bash
git submodule foreach <command>
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

List references in a local repository.

```bash
git show-ref
```

List only refs/tags in a local repository.

```bash
git show-ref --tags
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
