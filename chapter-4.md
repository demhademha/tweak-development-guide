# Chapter 4 - Aliases and Folders
In this chapter, we'll create the folders and the aliases that this guide will use.

## What is an alias?
In the most simplest terms, an alias is a shortcut for a command. For example, I could have an alias called `c` which stands for `clear` or an alias called `m` which stands for `make`. However, in these lessons, we'll be using aliases to make our lives easier when navigating directories.

### Let's see how this works
First, ssh into your device, refer to [chapter 1](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md) if you've forgotten how to do this. Make sure you log in as the **mobile** user and not the **root** user.\
Next, type the following `alias respring="sbreload"`, you can now type `respring` in your terminal, and your device will respring.

So, as you can see, we created an alias named respring, that executes the command sbreload. If we now type `respring` in terminal the command is not found.

So, we can now see that the aliases are not persistent. So, how do we make this persistent?\
The very first thing we need to find out is whether we are using zsh or bash. (You're wondering what bash and zsh are? They are both shells. A shell is an interface that allows you to input commands to control/access the operating system(ex. iOS, Linux).

The way to figure out what shell you are using is by typing this command in your terminal: `echo $SHELL`.
This will return either `/usr/bin/bash` or `/usr/bin/zsh`, make sure to remember which one is displayed for you.

Now, open Filza and navigate to `/var/mobile`, you should see `.profile` (for bash) or `.zprofile` (for zsh), and open the correct file according to your shell. However, if the file isn't displayed, you'll need to manually create the `.profile` or the `.zprofile` file yourself by running the command:
For bash:`touch /var/mobile/.profile`
For zsh: `touch var/mobile/.zprofile`

Once you've opened the correct file, go ahead, copy and paste the following lines of code:
```
alias github="cd ~/github"
alias tweaks="cd ~/tweaks"
export THEOS=~/theos
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

Next chapter will be setting up Theos & getting an SDK for our device.

## When you are ready, you can head over to [Chapter 5](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-5.md)

## Remember, you can join our [Discord server](https://discord.gg/nX7c4VZnBu)
