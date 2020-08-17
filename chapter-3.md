# Creating ssh keys

## Objectives for this lesson
* Change the mobile user password
* Understand the use of a ssh key  and a **basic** understanding of how they work
* Their pros
* How to create a ssh key
* How to add the ssh key to the target device

## Changing the ssh passwords
So, the majority of you will have a password which prevents prying eyes from just going into your device, and taking a look at all of your sensitive information. Well, as soon as we've installed openssh on our device, it only takes someone to find our IP address, and enter the password "alpine" and they've gained full access to the device.
as soon as a person has remote access over ssh, they can do whatever they want, but here's a few examples:
* they could bootloop your device
* they could fill up your device storage (for example, sending lots of IPSWs)
* they could download app content
* they could install spyware
However, the most simplest way we can fix this is by changing both our root and mobile passwords.

## What is the difference between the root and the mobile user?
On iOS devices, there are two users, root and mobile. Mobile has less privileges than root, meaning that you would have to run `sudo` in order to do higher privileged things. For example, if I tried to delete a file which is write protected as a mobile user, I might have to use `sudo` in order to achieve that. However, a root user is free to do what they wanted. But access to either by   a malicious person could be troublesome for us, so let's secure that device.

## Changing the root password
1. Make sure that you've logged in with ssh, see chapter 2
2. Type "passwd"
It will say "changing password for root"
"New password"
3. Type in your new password, it can't be longer than 8 characters (this is a limitation of iOS not me)
once that's done, you've successfully changed your root password. When you login after following chapter 2's instructions, enter this new password.

## Changing the mobile password
1. Make sure that you've logged in with ssh, see chapter 2
2. Type "passwd mobile"\
It will say "changing password for mobile"\
"New password"
3. Type in your new password, it can't be longer than 8 characters (this is a limitation of iOS not me), once that's done, you've successfully changed your mobile password.

## Why use an ssh key?
One of the most convincing reasons for using a ssh key is the fact that you don't have to enter your password! This means that your password can be a lot more complex, without you having to remember it. In addition, ssh keys are much more secure than password based authentication as they can be much longer, and are extremely difficult to break if not impossible.

## How does an ssh key work?
I'll try to explain how ssh keys work as best as I can with my analogy.\
Imagine, that I am a builder, and I build a house with doors. You own the house, and can physically touch and see the doors but you can't do anything with them. (These are the public keys, the doors are visible to everyone.) However, I'm the builder, so I own the key which can open the doors. I can both interact and open the doors (this is the private key, I am the only one who has access to this: you, the person who lives in the house never sees the key), so when we use a ssh key, only my private key and my public key will match. I am free to give the public key to anyone whether it's be my mum, the next-door neighbour or GitHub. However, the private key should **only** be with me, and should **never** be given to anyone. So in our case, we will give the public key to the iOS device and the private key will remain on the terminal we are using (whether it is ish, macOS or linux).  

## How to setup an ssh key
1. First, open your terminal app, (whether it is ish, or the terminal app on macOS or Linux)
**Note: do not ssh into your device**
2. Type in `ssh-keygen -b length_of_the_key` **Note: The minimum is 1024 and the max is 16384,\
the larger the key the longer it will take to generate and the more secure it will be. Example: "ssh-keygen -b 16384"** will generate a 16384 bit long ssh key (the max).\
It will then say: "Generating public/private rsa key pair" (You will need to be patient for this as it may take a while.)
3. After that, the following message will be displayed: "Enter file in which to save the key (/root/.ssh/id_rsa)"
**Note: Yours might be different, you can press enter to accept the default, or type a custom path if you wish.**
4. It will then ask "Enter passphrase (empty for no passphrase):" type a passphrase if you wish (strongly recommended)
5. Confirm the passphrase if you entered it, otherwise just press enter again
You've successfully created an ssh key, no let's transfer our door (public key) to our iOS device.

## Transfering the public key
1. Type in `ssh-copy-id` followed by how you would login with ssh, for example, `ssh-copy-id root@localhost -p2222`
It will say something like "/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
expr: warning: '^ERROR: ': using '^' as the first character
of a basic regular expression is not portable; it is ignored
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@localhost's password: "
2. Enter the appropriate password,
It will then say "Number of key(s) added: 1\
Now try logging into the machine, with: "ssh -p '2222' 'localhost'"
and check to make sure that only the key(s) you wanted were added."
3. Now, login normally over ssh, **you should not be asked for a password**
4. Finally, do the same again, but this time do this for your mobile user **"ssh mobile@localhost" or "ssh mobile@youripadress"**
## You've finally changed your root and mobile passwords, understood how public and private keys work, generated a public and a private key, and transferred the public key to the device.
