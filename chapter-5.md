# Chapter 5 - Setting up the compiler
By the end of this lesson, you will have a working c compiler.
## Before begining, unc0ver users and checkra1n users (not odysseyra1n users) follow the following steps:
1. SSH into your idevice as root
2. Type `apt update`
3. Type `apt install -y sudo nano`
4. Type `chmod 0440 /etc/sudoers`
5. Type `nano /etc/sudoers`
6. At the end of the opened text file you will see the following:
```
## Uncomment to allow any user to run sudo if they know the password
## of the user they are running the command as (root by default).
# Defaults targetpw  # Ask for the password of the target user
# ALL ALL=(ALL) ALL  # WARNING: only use this together with 'Defaults targetpw'

## Read drop-in files from /etc/sudoers.d
## (the '#' here does not indicate a comment)
#includedir /etc/sudoers.d
```
7. Un-comment `# Defaults targetpw` and `# ALL ALL=(ALL) ALL` by simply removing the `#`. (do **not** remove the full line)
8. Press `Ctrl+X`, type `Y` and hit enter to save the modified file.

## What is a compiler?
A compiler is software which takes your source code, (the code that humans can read) and converts it into machine code (what the machines understands). <br>
The compiler we will be using is the clang compiler (clang is the compiler for the C, C++, Objective C programming languages). It can be installed from your package manager. Alternatively, it can be installed directly from your terminal by running `sudo apt update` and then running `sudo apt install clang` (make sure to ssh into your device first).

Next, we need to download a patched iOS SDK. An SDK is short for a software development kit. We need it to develop software for our iOS device (for example, changing the UI, or making an app).

1. SSH into your idevice
2. Type `sudo apt update` type in your **password** and `y` if asked
3. Type `sudo apt install wget zip unzip` type in your **password** and `y` if asked
4. Type `cd /var/mobile`
5. Type `wget https://github.com/theos/sdks/archive/master.zip`
6. Wait for it to download
7. Type `unzip master.zip`
8. Wait for this to unzip: there will be a lot of output on your screen. This should take about roughly 4-5 minutes to extract everything
9. Type `cd sdks-master`
10. Type `ls` 
11. You will see multiple files with the ending `.sdk` make a note of the one which corresponds closest to your iOS version. For example, my device is running iOS 14.2, so I will choose the iOS 14.4 sdk.
12. Type `mv your_sdk_version ..` For example, `mv iPhoneOS14.4.sdk ..`
13. Type `cd ..` and you should be back at `/var/mobile`
14. Type `rm -r master.zip sdks-master`
15. Open your profile file: (refer to chapter 4 if you have forgotten how to do this)
16. At the bottom, add the following line: `export SDKROOT=/var/mobile/your_sdk` for example, `export SDKROOT=/var/mobile/iPhoneOS14.4.sdk` 
17. Restart your terminal session by disconnecting over ssh
18. Once you've reconnected over ssh, type `echo $SDKROOT`, the output should be `/var/mobile/your_sdk`.

## We've now set up our compiler! In the next [Chapter](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-6.md), we'll actually code :)
## Remember, you can join our [Discord server](https://discord.gg/nX7c4VZnBu)
