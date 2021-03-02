# A world of ssh passwords and keys

## Objectives for this lesson
* Change the root and mobile user password
* Understand the use of an ssh key and get a **basic** understanding of how they work
* Their pros
* How to create an ssh key
* How to add the ssh key to the target device

## Why changing the ssh passwords is vital
So, the majority of you will have a password which prevents prying eyes from just going into your device, and taking a look at all of your sensitive information. Well, as soon as we've installed openssh on our device, it only takes someone (who is on the same wifi network) to find our IP address, and enter the password `alpine` and they've gained full access to the device.
As soon as a person has remote access over ssh, they can do whatever they want, but here's a few examples:
* They could bootloop your device
* They could fill up your device storage (for example, sending lots of IPSWs)
* They could download content from your apps
* They could install spyware...

However, the most simplest way we can fix this is by changing both our root and mobile passwords.

## What is the difference between the root and the mobile user?
On iOS devices, the main two users are root and mobile. Mobile has less privileges than root, meaning that you would have to run `sudo` in order to do higher privileged things. For example, if I tried to delete a file which is write protected as a mobile user, I might have to use `sudo` in order to achieve that. However, a root user is free to do what they want. But access by a malicious person could be troublesome for us, so let's secure the device.

## Changing the root password
1. Make sure that you've logged in with ssh, see [chapter 1](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md)
2. Type `passwd`. It will say:
```
changing password for root
New password
```
3. Type in your new password, it can't be longer than 8 characters (this is a limitation of iOS not me). Once that's done, you've successfully changed your root password. When you login after following [chapter 1's](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md) instructions, enter this new password.

## Changing the mobile password
1. Make sure that you've logged in with ssh, see [chapter 1](https://github.com/demhademha/tweak-development-guide/blob/master/chapter-1.md)
2. Type `passwd mobile`. It will say:
```
changing password for mobile
New password
```
3. Type in your new password, it can't be longer than 8 characters (this is a limitation of iOS not me). Once that's done, you've successfully changed your mobile password.

## Why use an ssh key?
One of the most convincing reasons for using a ssh key is that you don't have to enter your password! This means that your password can be a lot more complex, without you having to remember it. In addition, ssh keys are much more secure than password based authentication as they can be much longer, and are extremely difficult to break if not impossible.

## How does an ssh key work?
I'll try to explain how ssh keys work as best as I can with my analogy.
Imagine I have a padlock which I give to you and I keep the key. You have the ability to lock the padlock, but that is it. You cannot unlock it. (This is the public key:) You can keep the contents of a thing safe (in other words, you can encrypt something.) However, I am the one with the key, so only I can access that thing which you kept safe (I am the only one who can decrypt it.) So in practice, this means that the public key (the padlock) can be given to anyone: wether it be my Mum, the next door neighbour or GitHub. However, when they send a message to me which is encrypted with my public key (padlock) only I can read it. So when we transfer our public key to the iOS device, it will create a message which only my private key can decrypt. If the keys validate, then I am logged in.<br>
**Note:** You should never give out your private key to anyone**

## How to setup an ssh key
1. First, open your terminal app, (whether it is ish, or the terminal app on macOS or Linux)<br>
**Note:** do not ssh into your device
2. Type in the following: <br>
`ssh -v localhost` <br>
The output should be something like this: <br>
`OpenSSH_8.4p1, OpenSSL 1.1.1j 16 Feb 2021` <br>
Note your ssh version: Mine is `8.4p1`. 
3. Log into your device over ssh and again, log its ssh version: my output is the following: <br>
`OpenSSH_8.4p1, OpenSSL 1.1.1i 8 Dec 2020` <br>
Again, my ssh version is `8.4p1` and again, I will note this down somewhere.
4. Type in `exit` to disconnect from the iOS device.  
5. Now determine wether you will need to create an RSA key or an ed25519 key. If both of your ssh versions (the one on the host machine and the ios device) are greater than 6.5, type in <br>
`ssh-keygen -t ed25519 -b length_of_the_key -C "your_email_@website.com"`. <br>
Else, type in <br> 
`ssh-keygen -t rsa -b length_of_the_key -C "your_email_@website.com"`. <br>
**Note:** The minimum length of the key is 1024 and the max is 16384, the larger the key the longer it will take to generate and the more secure it will be.<br>
Example: `ssh-keygen -t ed25519 -b 16384 -C "myemail@gmail.com"`<br>
This will generate a 16384 bit long ssh key (the max).
When generating the key, it will say: <br>
`Generating public/private ed25519 key pair` <br>
(You will need to be patient for this as it may take a while.)
6. After that, the following message will be displayed: <br>
`Enter file in which to save the key (/root/.ssh/id_ed25519)` <br>
**Note:** Yours might be different for example, it might say: <br>
 `Enter file in which to save the key (/etc/.ssh/id_ed25519)` <br>
7. It will then say <br>
`Enter passphrase (empty for no passphrase):` <br>
Type a passphrase if you wish (strongly recommended)
8. Confirm the passphrase if you entered it, otherwise just press enter again.

You've successfully created an ssh key, now let's transfer our padlock (public key) to our iOS device.

## Transfering the public key
1. Type in `ssh-copy-id` followed by how you would login with ssh, for example <br>
`ssh-copy-id root@localhost -p2222` <br>
It will say something like <br>
```
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
expr: warning: '^ERROR: ': using '^' as the first character
of a basic regular expression is not portable; it is ignored
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@localhost's password:
```
2. Enter the appropriate password,
It will then say: <br>
```
Number of key(s) added: 1
Now try logging into the machine, with: "ssh -p '2222' 'localhost'" and check to make sure that only the key(s) you wanted were added.
```
3. Now, login normally over ssh, **you should not be asked for a password** but rather, for your ssh key pass phrase (if you set one).
4. Finally, do the same again, but this time do this for your mobile user.

## Making ssh remember our pass phrase
You may find it cumbersome to continuously enter your pass phrase. To fix this, let's make sure that ssh auto fills it in for us. 
1. From terminal, type: <br>
`eval "$(ssh-agent -s)"` <br> 
The output should be something like this: <br>
`Agent pid 37`. <br>
This initiates the ssh agent. 
2. Finally, to add the ssh key to the agent, type the following: <br>
`ssh-add /path/to/your/ssh/directory/.ssh/id_ed25519` <br>
**Note:** If you are using rsa, then this command should be writtten like this: <br>
`ssh-add /path/to/your/ssh/directory/.ssh/id_rsa` <br>
An example of what this may look like is this: <br>
`ssh-add /root/.ssh/id_ed25519` <br>
If you are unsure where this folder is, it was specified when creating an ssh key with ssh-keygen.

Finally, you should be prompted for your pass phrase. Upon entering it, ssh will manually enter it for you. 
To test this, try to login again with ssh.

## Finishing the ssh setup 
It is a good idea to disable password logins completely. This ensures maximum security for the device, but it also means an individual wil not be able to brute force the password. Let's set this up: <br>
1. Open Filza and navigate to `/etc/ssh`
2. Open the file `sshd_config` with the text editor 
3. Look for the following line: <br>
`#PubkeyAuthentication yes` <br>
Change it to: <br>
`PubkeyAuthentication yes`
4. Look for the following line: <br>
`#PasswordAuthentication yes` <br>
Change it to: <br>
`PasswordAuthentication no` <br>

If I try to login to my device without an ssh key, I get the following output: <br>
`mobile@localhost: Permission denied (publickey,keyboard-interactive).` <br>
As you can see, I can only login if I have the key.

## You've finally changed your root and mobile passwords, understood how public and private keys work, generated a public and a private key, and transferred the public key to the device.
