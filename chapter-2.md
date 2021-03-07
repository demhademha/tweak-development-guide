# Chapter 2 - Learning the terminal
Here's a joke for you: Why do people always miss their planes? Keep reading to find the answer.

## What is a terminal?
A terminal is often a black screen with white text. It allows us to directly interact with our device, so that we don't need to use an app.
Terminal can significantly improve our workflow, let's take a look at an example.
1. Open `filza`
2. Tap on the `root` button, and you will be taken to the default location.
3. Navigate to `/usr/bin`
This is where most of the scripts are kept for the jailbreak, and it is **important** you don't delete anything from here.
In the simplest terms, a script is a file that will run one or ore command at once. (It can be anything from being a calculator or an automatic repo builder, that asks you questions for example, what colour you want the get button to be, and then creates a repo where you just need to put your packages in.)
4. Navigate until you see `sbreload`
5. Tap on it, and press ok
**Note: this will respring your device!**\
Ok so as you can see, that took a long time, and to be honest it's not practical as you're forced to navigate filza.  
well by using a terminal, we can make this significantly easier.
1. Ensure that you've used ssh to login into your device see chapter 1 if you've forgotten how to do that
2. Enter the command `sbreload`
**Note: this will respring your device**\
So, the conclusion from this is that for many things, we can just use terminal, rather than relying on filza. The terminal eliminates the need for us to go to `/usr/bin/sbreload`.\
Ok, now you should have a basic understanding of what we just did, now let's learn navigating around with just the terminal.\
So the word `directory` is just another fancy word for folder. In terminal, when we say things like `go to x directory,` we're just saying `go to x folder`. The `cd` command stands for `change directory` and it is followed by the path (the location of a folder or file on the device) so when we say `cd /var/` we're saying `change the directory to /var/` which is the var directory.\
Here's a question for you: which folder would you expect `cd  /var/mobile/Media` to take you?

If your answer is /var/mobile/Media, then you are correct.\
Now you know how to navigate directories (I hope) and it's time to know what files are in a certain directory.\
Firstly, change directory to /var/mobile (`cd /var/mobile`) and now, type `ls`.
* ls stands for list: so typing it will list everything in that particular folder. In our case, that's everything of /var/mobile. Now, you should see the `Media` folder (again).\
Now, you have two ways you can get to the `Media` folder, you could either type `cd /var/mobile/Media` or, you could use `cd ./Media` (which is a lot easier). The `.` before the `/` tells cd to automatically put in `/var/mobile` (or whatever the prefix is) of that directory, and the `/` just tells cd to put in what comes after it (in our case, `Media`).\
So, if we break it down even more, `.` = the prefix of the directory, and `/` means the rest of the location.\
If we type  `cd ..` means navigate to the previous  directory.
* The `pwd` command stands for print working directory: it will print where you currently are, in our case, /var/mobile.
* The command `touch` means create a new file, so `touch /var/tweaklog.txt` will create a txt file called tweaklog.
* The suffix (end of a file) is extremely important. As different suffixes be interpreted in different ways. For example, a file with a  suffix  of .swift means a swift file, a file with the suffix .m means an objective-c file and a file with .html would be a html file.

## Summary:
You should now be able to comfortably navigate terminal, using cd, you should be able to list what files are in your directory, you should know the definition of the word directory, you should be able to get which directory you are currently in, have an understanding of how to create a new file using touch and the significance of file extensions. Next chapter will be going over setting up SSH keys & changing your root password.  

Why do people always miss their planes?

Because they spend too much time at the terminal\
Get it?...

## When you are ready, you can head over to [Chapter 3](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-3.md)

## Remember, you can join our [Discord server](https://discord.gg/nX7c4VZnBu)
