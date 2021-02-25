# A world of ssh passwords and keys 


## Objectives for this lesson
* Change the mobile user password
* Understand the use of a ssh key  and a **basic** understanding of how they work
* Their pros
* How to create a ssh key
* How to add the ssh key to the target device

## Why changing the ssh passwords is vital
So, the majority of you will have a password which prevents prying eyes from just going into your device, and taking a look at all of your sensitive information. Well, as soon as we've installed openssh on our device, it only takes someone (who is on the same wifi network) to find our IP address, and enter the password `alpine` and they've gained full access to the device.
as soon as a person has remote access over ssh, they can do whatever they want, but here's a few examples:
* they could bootloop your device
* they could fill up your device storage (for example, sending lots of IPSWs)
* they could download content from your apps
* they could install spyware
However, the most simplest way we can fix this is by changing both our root and mobile passwords.

## What is the difference between the root and the mobile user?
On iOS devices, the main two users are root and mobile. Mobile has less privileges than root, meaning that you would have to run `sudo` in order to do higher privileged things. For example, if I tried to delete a file which is write protected as a mobile user, I might have to use `sudo` in order to achieve that. However, a root user is free to do what they want. But access  by   a malicious person could be troublesome for us, so let's secure the device.

## Changing the root password
1. Make sure that you've logged in with ssh, see [chapter 1](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md)
2. Type `passwd`
It will say `changing password for root`
`New password`
3. Type in your new password, it can't be longer than 8 characters (this is a limitation of iOS not me)
once that's done, you've successfully changed your root password. When you login after following [chapter 1's](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md) instructions, enter this new password.

## Changing the mobile password
1. Make sure that you've logged in with ssh, see [chapter 1](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md)
2. Type `passwd mobile`\
It will say `changing password for mobile`\
`New password`
3. Type in your new password, it can't be longer than 8 characters (this is a limitation of iOS not me), once that's done, you've successfully changed your mobile password.

## Why use an ssh key?
One of the most convincing reasons for using a ssh key is the fact that you don't have to enter your password! This means that your password can be a lot more complex, without you having to remember it. In addition, ssh keys are much more secure than password based authentication as they can be much longer, and are extremely difficult to break if not impossible.

## How does an ssh key work?
I'll try to explain how ssh keys work as best as I can with my analogy.\
Imagine I have a padlock which I give to you and I keep the key. You have the ability to lock the padlock, but that is it. You cannot unlock it. (This is the public key:) You can keep the contents of a thing safe (in other words, you can encrypt something.) However, I am the one with the key, so only I can access that thing which you kept safe (I am the only one who can decrypt it.) So in practical, this means that the public key (the padlock) can be given to anyone: wether it be my Mum, the next door neighbour or GitHub. However, when they send a message to me which is encrypted with my public key (padlock) only I can read it. So when we transfer our public key to the iOS device, it will create a message which only my private key can decrypt. If the keys validate, then I am logged in. 
**note: You should never give out your private key to anyone**

## How to setup an ssh key
1. First, open your terminal app, (whether it is ish, or the terminal app on macOS or Linux)
**Note: do not ssh into your device**
2. Type in `ssh-keygen -b length_of_the_key` **Note: The minimum is 1024 and the max is 16384,\
the larger the key the longer it will take to generate and the more secure it will be. Example: `ssh-keygen -b 16384`** will generate a 16384 bit long ssh key (the max).\
It will then say: \
`Generating public/private rsa key pair` \
(You will need to be patient for this as it may take a while.)
3. After that, the following message will be displayed: \
`Enter file in which to save the key (/root/.ssh/id_rsa)` \
**Note: Yours might be different, you can press enter to accept the default, or type a custom path if you wish.**
4. It will then say \
`Enter passphrase (empty for no passphrase):`. \
Type a passphrase if you wish (strongly recommended)
5. Confirm the passphrase if you entered it, otherwise just press enter again
You've successfully created an ssh key, now let's transfer our padlock (public key) to our iOS device.

## Transfering the public key
1. Type in `ssh-copy-id` followed by how you would login with ssh, for example, `ssh-copy-id root@localhost -p2222`\
It will say something like
```
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
expr: warning: '^ERROR: ': using '^' as the first character
of a basic regular expression is not portable; it is ignored
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@localhost's password:
```
2. Enter the appropriate password,
It will then say
```
Number of key(s) added: 1
Now try logging into the machine, with: "ssh -p '2222' 'localhost'" and check to make sure that only the key(s) you wanted were added.
```
3. Now, login normally over ssh, **you should not be asked for a password** but rather, for your ssh key pass pharase (if you set one)
4. Finally, do the same again, but this time do this for your mobile user (`ssh mobile@localhost` or `ssh mobile@youripadress`)
## Makeing ssh remember our pass phrase
You may find it cumbersome to continuously enter your pass phrase. To fix this, let's make sure that ssh auto fills it in for us. 
1. From terminal, type:
```
eval "$(ssh-agent -s)"
```
the output should be something like this:
```
Agent pid 37
``` 
This initiates the ssh agent. 
Finally, to add the ssh key to the agent, type the following:
```
ssh-add /path/to/your/ssh/directory/.ssh/id_rsa 
```
for example:
```
ssh-add /root/.ssh/id_rsa
```
If you are unsure where this folder is, it was specified when creating an ssh key with ssh-keygen.
Finally, you should be prompted for your pass phrase. Upon entering it, ssh will manually enter it for you. 
To test this, try to login again with ssh. 
## You've finally changed your root and mobile passwords, understood how public and private keys work, generated a public and a private key, and transferred the public key to the device.
