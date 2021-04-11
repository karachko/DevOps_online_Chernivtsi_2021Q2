# TASK 5.1 #
 
1. I loged in to the system as root (su root)
2. I changed the password  by using the command (passwd username)
- The file /etc/passwd contained the information about users
- The parameters of command passwd:
- -d, --delete (to delete an user)
- -h, --help (to display help)
- -l, --lock(to lock an user)
- -S, --status(to display a status of user)
3. I determined the users registered in the system by using the command (cat /etc/passwd)
4. I changed the personal information by using the command (usermod -c "YOUR NAME" username)
5. I familiared with the Linux help system and the man and info commands 
5.1. ** help **
` help — Показывает информацию о встроенных командах в Linux
d выводит краткое предназначение по запрашиваемой команде.
м выводит информации в формате псевдо-Man-страницы.
s выводит информацию только для использования синтаксиса по запрашиваемой команде.`

5.1.1. passwd --help
![5.1.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/edit/main/m5/task5.1/5.1.1.jpg)
 
5.1.2. ![5.1.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/edit/main/m5/task5.1/5.1.2.jpg)

5.2.  ** man ** command in Linux is used to display the user manual of any command that we can run on the terminal.
-  -w option: This option returns the location in which the manual page of a given command is present.
-  man -w passwd
- /usr/share/man/man1/passwd.1.gz
- -k option: This option searches the given command as a regular expression in all the manuals and it returns the manual pages with the - section number in which it is found.
- root@WIN-LVJOCDBKSR3:/etc# man -k passwd
- chgpasswd (8)        - update group passwords in batch mode
- chpasswd (8)         - update passwords in batch mode
- gpasswd (1)          - administer /etc/group and /etc/gshadow
- grub-mkpasswd-pbkdf2 (1) - generate hashed password for GRUB
- openssl-passwd (1ssl) - compute password hashes
- pam_localuser (8)    - require users to be listed in /etc/passwd
- passwd (1)           - change user password
 
5.3.
The info format is similar to that of man, the traditional Unix manual format. 
-d, --directory=DIR	Add DIR to INFOPATH.
--version	Display version information and exit.

5.3.1   info passwd
PASSWD(1)                                           User Commands                                           PASSWD(1)

NAME
       passwd - change user password

SYNOPSIS
       passwd [options] [LOGIN]

DESCRIPTION
       The passwd command changes passwords for user accounts. A normal user may only change the password for their
       own account, while the superuser may change the password for any account.  passwd also changes the account or
       associated password validity period.

 5.3.2 info --version
info (GNU texinfo) 6.7

Copyright (C) 2019 Free Software Foundation, Inc.

6. 6.1 less --help
  SUMMARY OF LESS COMMANDS

      Commands marked with * may be preceded by a number, N.
      Notes in parentheses indicate the behavior if N is given.
      A key preceded by a caret indicates the Ctrl key; thus ^K is ctrl-K.
6.2  more --help

Usage:
 more [options] <file>...

A file perusal filter for CRT viewing.

Options:
 -d          display help instead of ringing bell
 -f          count logical rather than screen lines
 -l          suppress pause after form feed
 -c          do not scroll, display text and clean line ends

6.3
ubuntu@WIN-LVJOCDBKSR3:~$ nano passw.sh
ubuntu@WIN-LVJOCDBKSR3:~$ chmod +x passw.sh
ubuntu@WIN-LVJOCDBKSR3:~$ less passw.sh

passwd

passw.sh (END)                                                             
7. 7.jpg
8.8.jpg


part2
1) 2.1.2.jpg
2) 2.2.jpg
3)  An absolute path always contains the root element and the complete directory list required to locate the file. For example, /home/sally/statusReport is an absolute path.
The relative path begins with a dot (period), representing the current directory (also called the "working directory"). The relative path ./public_html/cgi-bin is valid only if the current directory contains a path named public_html which contains a directory named cgi-bin. 
2.3.jpg

To refer to something two levels up in the directory tree one would use the prefix ../../, and so forth.
2.3.1.jpg
To navigate into the root directory, use "cd /"

To navigate to your home directory, use "cd" or "cd ~"

To navigate up one directory level, use "cd .."

To navigate to the previous directory (or back), use "cd -"

To navigate through multiple levels of directory at once, specify the full directory path that you want to go to. For example, use, "cd /var/www" to go directly to the /www subdirectory of /var/. As another example, "cd ~/Desktop" will move you to the Desktop subdirectory inside your home directory.
Example
ubuntu@WIN-LVJOCDBKSR3:~/reldir$ cd /home
ubuntu@WIN-LVJOCDBKSR3:/home$ cd ~/reldir
ubuntu@WIN-LVJOCDBKSR3:~/reldir$

4)2.4.jpg
5)
-  mkdir newdir
cd newdir
-  ls -a >> infofile


- ubuntu@WIN-LVJOCDBKSR3:~/newdir$ cat infofile
.
..
infofile
-     -   ubuntu@WIN-LVJOCDBKSR3:~/newdir$ cp infofile ../
ubuntu@WIN-LVJOCDBKSR3:~/newdir$ cd ../
ubuntu@WIN-LVJOCDBKSR3:~$ ls
1.txt  2  2.txt  infofile  newdir  passw.sh  reldir  user.conf
ubuntu@WIN-LVJOCDBKSR3:~$
      -     cp /home/ubuntu/newdir/infofile /home/ubuntu
- rm -R newdir
-  rm infofle

6. 
-  mkdir test
Это файл в котором хранится история вводимых команд
Находится в домашней папке пользователя
- cp .bash_history ./test
  ls -la
total 4
drwxrwxrwx 1 ubuntu ubuntu  512 Apr  9 13:20 .
drwxr-xr-x 1 ubuntu ubuntu  512 Apr  9 13:08 ..
-rw------- 1 ubuntu ubuntu 3390 Apr  9 13:20 .bash_history

 mv .bash_history labwork2
-create hard link
ln labwork2 lnlab2
ubuntu@WIN-LVJOCDBKSR3:~/test$ ls -l
total 8
-rw------- 2 ubuntu ubuntu 3390 Apr  9 13:20 labwork2
-rw------- 2 ubuntu ubuntu 3390 Apr  9 13:20 lnlab2
- create soft link
   ubuntu@WIN-LVJOCDBKSR3:~/test$ ln -s labwork2 lnlabsoft2
ubuntu@WIN-LVJOCDBKSR3:~/test$ ls -l
total 8
-rw------- 2 ubuntu ubuntu 3390 Apr  9 13:20 labwork2
-rw------- 2 ubuntu ubuntu 3390 Apr  9 13:20 lnlab2
lrwxrwxrwx 1 ubuntu ubuntu    8 Apr  9 13:30 lnlabsoft2 -> labwork2

-A soft link is similar to the file shortcut feature which is used in Windows Operating systems.
Each hard linked file is assigned the same Inode value as the original, therefore they reference the same physical file location.


-  nano lnlabsoft2
  write help

- mv labwork2 hard_lnk_labwork2
  mv lnlabsoft2 symb_lnk_labwork2
 rm labwork2
rm: cannot remove 'labwork2': No such file or directory

7.
2.7.jpg
8.
2.8.jpg
9.????
10.
find /etc -name "host"
2.10.jpg
11.

2.11.jpg
2.11.1.jpg
12.
find /etc >> 1.txt | more
13.
13.jpg
14.
file file.txt
file.txt: ASCII text
2.14.jpg
15.
/etc/security/access.conf
/etc/passwd
/etc/ssh/sshd_config
/etc/ufw/applications.d/openssh-server
/etc/ssl/openssl.cnf


                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
 
