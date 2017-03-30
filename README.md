# GitHub Cheat Sheet
A collection of some of the most useful Git commands

## Table of Contents
1. [Settings](#settings)
    * [Setting Global Configs](#setting-global-configs)
    * [Getting Global Configs](#getting-global-configs)
    * Local Configs

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

### Getting Global Settings
Get all your global settings
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
