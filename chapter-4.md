# Chapter 4
## Aliases and Folders
In this chapter, we'll create the folders and the aliases that this guide will comprise of.

## What is an alias?
In the most simplest terms, an alias is a shortcut for a command. For example, I could have an alias called `c` which stands for `clear` or an alias called `m` which stands for `make`. However, in these lessons, we'll be using aliases to make our lives easier when navigating directories.

### Let's see how this works
First, ssh into your device, refer to [chapter 1](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md) if you've forgotten how to do this. Make sure you log in as the **mobile** user and not the **root** user.\
Next, type the following `alias respring="sbreload"`, you can now type `respring` in your terminal, and your device will respring.

So, as you can see, we created an alias named respring, that carries out the command sbreload. If we now type `respring` in terminal the command is not found.

So, we can now see that the aliases are not persistent. So, how do we make this persistent?\
The very first thing we need to find out is whether we are using zsh or bash. (You're wondering what bash and zsh are? They are both shells. A shell is a interface to access an operating system, it allows you to input commands.)

The way we will do this is by typing `echo $SHELL`.
This will return either `/usr/bin/bash` or `/usr/bin/zsh`, make sure to remember which one is displayed for you.

Now, open Filza and navigate to `/var/mobile`, you should see `.profile` (for bash) or `.zprofile` (for zsh), and open the correct file according to your shell. However, if the file isn't displayed, you'll need to manually create the `.profile` or the `.zprofile` file yourself.
Once you're in the correct file, go ahead, copy and paste the following lines of code:
```
alias github="~/github"
alias tweaks="~/tweaks"
export $THEOS=~/Theos
```
Note: `$THEOS` is a variable, we have set this up now to save time later when we'll install Theos.

Now, save this file, restart ish by reloading it from the app switcher and reconnect over ssh. Now, type in the following:
```
mkdir ~/github
mkdir ~/tweaks
```

## Summary:
* Have an understanding of aliases
* Created aliases for github and tweaks
* Made aliases persistent
* Created a tweaks and a github folder
