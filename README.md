# Linux-Forensics

# Autospy deleted files recovery

<h1> This is an exercise provided by the TryHackMe DFIR course </h1>

 
 #### All images and copyrights are protected for TryHackMe

<h2>Description</h2>
Project: OS and accounts information
Objective: Use the command line to find user and accounts information

<h2>Tools/ Utilities Used</h2>

- <b>Linux Virtual Machine</b>
- <b>terminal ( command tool)</b>

Tasks:

1- Find the User ID (UID) of the tryhackme user account.

2- Find the user (s) /members in the group audio.

3- Find out how long a session lasted on Sat April 16 at 20:10.
  
 
Launching the Linux VM: 

There is a terminal on the desktop to use for commands.
The command line to know the OS release info is: cat /etc/os-release

![Linux OS](https://github.com/TheRashaSharif/Linux-Forensics/assets/98124961/efa91480-354b-4436-b1f4-c8c91e40ed98)

The other command on the terminal is name -a which is also going to provide the release and logged user info.

1- The command we will be using for the user ID tryhackme is cat/etc/passwd
as shown above.

When scrolling down the user information is 
tryhackme:x:1001:1001:tryhackme,,,:/home/tryhackme:/bin/bash

user ID is tryhackme, the x means the password is saved in the shadow file, and the user UID is 1001 
/home/tryhackme is the home path and the last values are the shell meaning we can log into it.

If the user name has the value false like this one 
gdm:x:129:135:Gnome Display Manager:/var/lib/gdm3:/bin/false
the false value means you can't log in to this account. It is recommended to set the value to false to avoid vulnerability.

2- To find a user(s) in a group we will use the command cat\etc\group
no s in the end, I know it is tempting to type groups, but this will be the result

The group audio has the following two users: 

![Linux group](https://github.com/TheRashaSharif/Linux-Forensics/assets/98124961/cea45225-9aa0-4bc9-b7e4-67f51b07da28)

3- To view a session activity we will have to change the directory to cd /var/log

this will display all the logs of launched activities. 
$ cd /var/log
Then 
/var/log$ ls

The sessions logs are stored in wtmp and we must elevate to sudo before getting the access
/var/log$ sudo last -f wtmp

The session was successfully initiated on  Sat April 16 at 20:10. lasted an hour and 32 minutes

![Linux date and time q3](https://github.com/TheRashaSharif/Linux-Forensics/assets/98124961/45a6a1c7-1692-4bc6-8162-6e5973d3a113)

This concludes this exercise. The last one was a tough one! 
