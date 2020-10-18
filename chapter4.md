# chapter 4
## Aliases and Folders
In this chapter, we'll create the folders and. The aliases that this guide will comprise of. 
## What is an alias?

In the most   simplest terms, an alias is a short cut for a command. For example, I could have an alias called "c" which stands for clear" or an alias called "m" which stands for make" however, in these lessons, we'll be using aliases to make our lives easier when navigating directories. 
### Let's see how this works 
First, ssh in to your device, refer to chapter 1 if you've forgotten how to do this. Make sure you login as the **mobile** user and not the **root** user.
Next, type the following

alias respring="sbreload"
you can now type in "respring" in your terminal, and your device will respring. 

So, as you can see, we created an alias with the name respring, that carries out the command sbreload. 
if we now type "respring" in terminal the command is not found. 
so, we can now see that the aliases are not persistent. 
So, how do we make this persistent? 
The very first thing is we need to find out if we are using zsh or bash. The way we will do this is by typing "echo $SHELL" 
This will return either "/usr/bin/bash" or "/usr/bin/zsh", make sure to remember which one is displayed for you. 
Now, open filza and navigate to /var/mobile and you should see ".profile" (for bash) or ".zshprofile" (for zsh) and go ahead and open the correct file for your jailbreak. However, if the file isn't displayed, you'll need to manually create the ".profile" or the ".zshprofile" file yourself. 
Once your in the correct folder, go ahead and copy the following lines of code:
alias github="~/github"
alias tweaks="~/tweaks"
export $THEOS=~/Theos
Note: $THEOS is a variable we have set this up now to save time later on.,   
now, save this file, restart ish by reloading it from the app switcher and reconnect over ssh.
now, type in the following:
mkdir=~/github
mkdir ~/tweaks

## summary: 
*  have an understanding of aliases 
* created aliases for github and tweaks 
* made aliases persistent 
* created a tweaks and a github folder

