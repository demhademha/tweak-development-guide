# Chapter 5 - Setting up the compiler
By the end of this lesson, you will have a working c compiler.

## What is a compiler?
A compiler is the piece of software which takes your source code, (the thing humans can read) and converts it into machine code (what the device understands). <br>
The compiler we will be using is the clang compiler. It can be installed from your package manager. Alternatively, it can be installed directly from terminal by running `sudo apt update && sudo apt install clang` (make sure to ssh into your device first).

We next need to download a patched sdk. An sdk is a software development kit. It is what we need in order to communicate with the device, (for example, changing the UI).
1. Ssh into your idevice
2. Type `sudo apt update && sudo apt install wget zip unzip` type in your **password** and `y` if asked
3. Type `cd /var/mobile`
4. Type `wget https://github.com/theos/sdks/archive/master.zip`
5. Wait for it to download
6. Type `unzip master.zip`
7. Wait for this to unzip: there will be a lot of output on your screen
8. Type `cd sdks-master`
9. Type `ls` 
10. You will see multiple files with the ending `.sdk` make a note of the one which corresponds closest to your iOS version. For example, my device is running iOS 14.2, so I will choose the iOS 14.4 sdk.
11. Type `mv your_sdk_version ..` For example, `mv iPhoneOS14.4.sdk ..`
12. Type `cd ..` and you should be back at `/var/mobile`
13. Type rm -r master.zip sdks-master
14. Open your profile file: (refer to chapter 4 if you have forgotten how to do this)
15. At the bottom, add the following line: `export SDKROOT=/var/mobile/your_sdk` for example, `export SDKROOT=/var/mobile/iPhoneOS14.4.sdk` 
16. Restart your terminal session by disconnecting over ssh
17. Once you've reconnected over ssh, type `echo $SDKROOT`, the output should be `/var/mobile/your_sdk`.

## We've now set up our compiler! In the next chapter, we'll actually code :)
## Remember, you can join our [discord server](https://discord.gg/nX7c4VZnBu)