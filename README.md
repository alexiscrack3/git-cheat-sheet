# GitHub Cheat Sheet
A collection of some of the most useful Git commands

## Table of Contents
1. [Settings](#settings)
    * [Setting Global Configs](#setting-global-configs)
    * [Getting Global Configs](#getting-global-configs)
    * [Setting Local Configs](#setting-local-configs)
    * [Getting Local Configs](#getting-local-configs)
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
