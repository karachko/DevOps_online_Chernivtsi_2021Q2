## TASK 5.2. ##

1. I analyzed the structure of the /etc/passwd   
- /etc/passwd Format
- From the above image:
- Username: It is used when user logs in. It should be between 1 and 32 characters in length.
- Password: An x character indicates that encrypted password is stored in /etc/shadow file. 
- User ID (UID): Each user must be assigned a user ID (UID). UID 0 (zero) is reserved for root and UIDs 1-99 are reserved for other predefined accounts. Further UID 100-999 are reserved by system for administrative and system accounts/groups.
- Group ID (GID): The primary group ID (stored in /etc/group file)
- User ID Info: The comment field.  
- Home directory: The absolute path to the directory the user will be in when they log in.
- Command/shell: The absolute path of a command or shell (/bin/bash). Typically, this is a shell. 

- I analyzed the structure of the /etc/group
- Understanding the /etc/group File
group_name: It is the name of group. If you run ls -l command, you will see this name printed in the group field.
- Password: Generally password is not used, hence it is empty/blank. It can store encrypted password. This is useful to implement privileged groups.
- Group ID (GID): Each user must be assigned a group ID. You can see this number in your /etc/passwd file.
- Group List: It is a list of user names of users who are members of the group. The user names, must be separated by commas.

- The users root, sync, ubuntu exist in the system

- For every version of UNIX, there are password file entries for multiple pseudo-users. These records cannot be edited. These non-logon users have corresponding processes for every aspect of the system ownership. Below is a list of the most common pseudo-users:

- daemon Used by system server processes

- bin Owns the user's executable files

- sys Owns system files

- adm Owns budget files

- uucp Used by UUCP

- lp Used by subsystems 1p or lpd

- nobody Used by NFS
- There are other standard pseudo-users such as audit, cron, mail, new, and Usenet.
- 1.1.JPG
- ![1.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.2/1.1.jpg)
2. I learnt UID
- User ID (UID): Each user must be assigned a user ID (UID). UID 0 (zero) is reserved for root and UIDs 1-99 are reserved for other predefined accounts. Further UID 100-999 are reserved by system for administrative and system accounts/groups.
-Example
- cat /etc/passwd
- root:x:0(the third value 0 is the user ID)
- bin:x:2 (the third value 2 is the user ID)  
3. I learnt GID
- Group ID (GID): The primary group ID (stored in /etc/group file)
- cat /etc/passwd
- root:x:0:0(the fouth value 0 is a group ID)
- bin:x:2:2 (the fouth value 2 is a group ID)  
4. I determined belonging of user to the specific group
- How do I find a specific user’s GID?
- id -g ubuntu
- 1000

5. I learnt the commands for adding a user to the system
- useradd [OPTIONS] USERNAME
- Only root or users with sudo privileges can use the useradd command to create new user accounts.
- [OPTIONS]
    - b, --base-dir BASE_DIR base directory for the home directory of the new account
    - r, --system                  create a system account
    - m, --create-home             create the user's home directory
    - e, --expiredate EXPIRE_DATE  expiration date of the new account

6. I learnt how do I change the name (account name) of an existing user
- usermod -l login-name old-name
- sudo usermod -l user3 user2
7. I learnt the skell_dir
- The /etc/skel directory contains files and directories that are automatically copied over to a new user’s when it is created from useradd command.This will ensure that all the users gets same intial settings and environment.
- 7.1.jpg
-  ![7.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.2/7.1.jpg)
- Default Permission of the /etc/skel directory is drwxr-xr-x.
8. I learnt how to remove a user from the system
- Switch to root mode:
- .
- sudo su -
- To delete an old user, use the userdel command:
userdel username
Not necessarily. You can also delete this user's home directory and spool e-mail folder using the -r option with the command:
- userdel -r username
9.I learnt commands and keys that should be used to lock and unlock a user account
- Run the passwd command with the -l switch, to lock the given user account.
- passwd -l daygeek
- Run the passwd command with the -u switch to unlock the given user account.
- passwd -u daygeek
- Run the usermod command with the -L switch to lock the given user account.
- usermod -L daygeek
- Checking the user account locked status using passwd command.
- passwd -S daygeek
- Run the usermod command with the -U switch to unlock the given user account.
- usermod -U daygeek
- The ‘chage’ command is used to view and modify user password expiration information. It can be used to lock and unlock user accounts.

- Set the expiration date to ‘0’ to lock user account with chage command as shown below.

- # chage -E0 daygeek
- To reverse this change, run the following command.

- # chage -E -1 daygeek

10.I learnt how to remove a user's password and provide him with a password-free login for subsequent password change

- First, if your user has sudo privileges, you must enable its NOPASSWD option. Otherwise, sudo will ask for a password even when you don't have one, and won't accept an empty password.

- To do so, open the sudoers configuration file with sudo visudo, and add the following line to the file, replacing david with your username:

- david ALL=(ALL) NOPASSWD:ALL
- Close the editor to apply the changes, and test the effect on sudo in a new terminal.

- Delete the password for your user by running this command:

sudo passwd -d `whoami`


11. I displayed the extended format of information about the directory
11.jpg

-  ![11.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.2/11.jpg)

12. I learnt  theaccess rights exist.

- Permission Groups

- Each file and directory has three user based permission groups:

- owner – The Owner permissions apply only the owner of the file or directory, they will not impact the actions of other users.
- group – The Group permissions apply only to the group that has been assigned to the file or directory, they will not effect the actions of other users.
- all users – The All Users permissions apply to all other users on the system, this is the permission group that you want to watch the most.
- Permission Types
- Each file or directory has three basic permission types:

- read – The Read permission refers to a user’s capability to read the contents of the file.
- write – The Write permissions refer to a user’s capability to write or modify a file or directory.
- execute – The Execute permission affects a user’s capability to execute a file or view the contents of a directory.

- Viewing the Permissions ls -l

- The permission in the command line is displayed as: _rwxrwxrwx 1 owner:group

- User rights/Permissions
- The first character that I marked with an underscore is the special permission flag that can vary.
- The following set of three characters (rwx) is for the owner permissions.
- The second set of three characters (rwx) is for the Group permissions.
- The third set of three characters (rwx) is for the All Users permissions.
- Following that grouping since the integer/number displays the number of hardlinks to the file.
- The last piece is the Owner and Group assignment formatted as Owner:Group.

- Using Binary References To Set Permissions
- Now that you understand the permissions groups and types this one should feel natural. To set the permission using binary references you must first understand that the input is done by entering three integers/numbers.

- A sample permission string would be chmod 640 file1, which means that the owner has read and write permissions, the group has read permissions, and all other user have no rights to the file.
- r = 4
- w = 2
- x = 1
13.I learnt the sequence of defining the relationship between the file and the user
- Viewing the Permissions ls -l

- The permission in the command line is displayed as: _rwxrwxrwx 1 owner:group

- User rights/Permissions
- The first character that I marked with an underscore is the special permission flag that can vary.
- The following set of three characters (rwx) is for the owner permissions.
- The second set of three characters (rwx) is for the Group permissions.
- The third set of three characters (rwx) is for the All Users permissions.
- Following that grouping since the integer/number displays the number of hardlinks to the file.
- The last piece is the Owner and Group assignment formatted as Owner:Group.


- chmod command is used to change the permission bits of the file or folder.
- Syntax:
- chmod [Permission][Path of file or folder]

- The permission bits can be defined by explicitly and binary references, which are explained in the next part of this tutorial.

- Set permissions in symbolic mode:

- ‘u’, ‘g’, and ‘o’ characters are used for user types, and ‘r‘, ‘w‘, and ‘x’ characters are used for permission types in symbolic mode. 

14. I learnt the commands are used to change the owner of a file 

- chown command is used to change the ownership of user and group user for any file. 
- Syntax:
- chown [OPTION] [OWNER] [: [GROUP] ] FILE

- The first ls command shows the current owner and group ownership of the c2.py file. Here, the user and group ownership name of c2.py is fahmida before running the chown command. When the ls command is executed after running the command, then the user ownership is given to yesmin, and the group ownership is given to the owner’s group named yesmin.

14.jpg
- ![14.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.2/14.jpg)

15. I learnt the octal representation of access rights

- The syntax is as follows to get octal file permissions on Linux:
- stat fileName
- stat -c 'Format' file

- %a	access rights in octal (note ‘#’ and ‘0’ printf flags)
- %n	file name
- %A	access rights in human readable form
- 15.jpg
- ![15.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.2/15.jpg)


16. I learnt about a sticky bit 

- A Sticky bit is a permission bit that is set on a file or a directory that lets only the owner of the file/directory or the root user to delete or rename the file. No other user is given privileges to delete the file created by some other user.

- turn ON the sticky bit on the directory by using +t flag of chmod command.
- chmod +t test/

- 16.jpg
- ![16.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.2/16.jpg)
17. I learnt the attributes should be present in the command script
- chmod ugo+x
- execute – The Execute permission affects a user’s capability to execute a file or view the contents of a directory.
17.jpg

- ![17.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.2/17.jpg)




