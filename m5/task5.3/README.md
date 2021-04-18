# TASK5.3 #
## Part1 ##
1. I learnt the states of a process in Linux.
- In Linux, a process has the following possible states:

- Running – here it’s either running (it is the current process in the system) or it’s ready to run (it’s waiting to be assigned to one of the CPUs).
- Waiting – in this state, a process is waiting for an event to occur or for a system resource. Additionally, the kernel also differentiates between two types of waiting processes; interruptible waiting processes – can be interrupted by signals and uninterruptible waiting processes – are waiting directly on hardware conditions and cannot be interrupted by any event/signal.
- Stopped – in this state, a process has been stopped, usually by receiving a signal. For instance, a process that is being debugged.
- Zombie – here, a process is dead, it has been halted but it’s still has an entry in the process table.
2. I examined the pstree command
- pstree is a Linux command that shows the running processes as a tree.
- pstree username
- pstree pid
- Example - ubuntu@WIN-LVJOCDBKSR3:~$ pstree ubuntu
- bash───pstree
3. I learnt  proc file system.
- The proc filesystem is a pseudo-filesystem which provides an
       interface to kernel data structures.  It is commonly mounted at
       /proc. Typically, it is mounted automatically by the system, but
       it can also be mounted manually using a command such as:           mount -t proc proc /proc
- Mount options.The proc filesystem supports the following mount options:

- hidepid=n (since Linux 3.3)
              This option controls who can access the information in
              /proc/[pid] directories. 
- gid=gid (since Linux 3.3)
              Specifies the ID of a group whose members are authorized
              to learn process information otherwise prohibited by
              hidepid (i.e., users in this group behave as though /proc
              was mounted with hidepid=0). 

4. I printed information about the processor
- ![4.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/4.1.jpg)
-  less /proc/cpuinfo
- ![4.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/4.2.jpg)
5. I used the ps command to get information about the process

- You can choose all the processes belonging to you, enter:
1
$ ps -x
- To select the user processes using the efficient user ID (EUID) or its name,$ ps -fu sedicomm
- If you want to bring all the processes belonging to a specific group
$ ps -fG adm
- ![5.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/5.1.jpg)

6. I defined kernel processes and user processes

- User-space processes have its own virtual address space.

- Kernel processes or threads do not have their own address space, they operate within kernel address space only. And they may be started before the kernel has started any user process (e.g. init).

7. I Printed the list of processes to the terminal
- ![7.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/7.1.jpg)
- When using ps with the “u” flag (ps -u) you will see a column called STAT that displays the process’s status.
- Here is a list of the various process statuses and what they mean:

- D – Uninterruptible sleep (usually a critical system process, a process that cannot be killed without rebooting)
- R – Running or runable (on run queue)
- S – Interruptible sleep (waiting for an event to complete)
- T – Stopped, either by a job control signal or because it is being traced.
- Z – Defunct (“zombie”) process, terminated but not closed by the parent process that created it

8. I Displayed only the processes of a specific user
To see only the processes owned by a specific user on Linux run: ps -u {USERNAME}
- ![8.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/8.1.jpg)


9. I analyzed existing running tasks
- ps aux
- ![9.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/9.jpg)

10. I learnt top command
- top command is used to show the Linux processes. It provides a dynamic real-time view of the running system. Usually, this command shows the summary information of the system and the list of processes or threads which are currently managed by the Linux Kernel.
- As soon as you will run this command it will open an interactive command mode where the top half portion will contain the statistics of processes and resource usage. And Lower half contains a list of the currently running processes. Pressing q will simply exit the command mode.
- Here,

- PID: Shows task’s unique process id.
- PR: Stands for priority of the task.
- SHR: Represents the amount of shared memory used by a task.
- VIRT: Total virtual memory used by the task.
- USER: User name of owner of task.
- %CPU: Represents the CPU usage.
- TIME+: CPU Time, the same as ‘TIME’, but reflecting more granularity through hundredths of a second.
- SHR: Represents the Shared Memory size (kb) used by a task.
- NI: Represents a Nice Value of task. A Negative nice value implies higher priority, and positive Nice value means lower priority.
- %MEM: Shows the Memory usage of task.
 - ![10.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/10.1.jpg)

11. I displayed the processes of the specific user using the top command.
 Option to list processes by name is to run either top -U {userName} or htop -u {userName} commands
-Example top -u ubuntu
- ![11.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/11.1.jpg)
12. I learnt the interactive commands can be used to control the top command
- Useful interactive commands that can be used in the Top command:

- [Space] Immediately update the contents of the screen.
- [k] destroy the process. The program requests the process code and the signal to be sent to him.
- [n] Change the number of processes displayed. You are invited to enter a number.
- [u] Show only user processes.
- [M] Sort by the amount of memory used.
- [P] Sort the processor boot.

13. I learnt sortting the contents of the processes the ps command output is unsorted. The -sort parameter forces ps to sort the output. The ascending or descending order can be specified by adding the + (ascending) or - (descending) prefix to the parameter:
$ ps [OPTIONS] --sort -paramter1,+parameter2,parameter3..

- ![13.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/13.1.jpg)
14. I learnt the concept of priority

- we will look at how to prioritize the CPU usage of a program or command. If you have a very CPU-intensive program or task, but you also understand that it might take a long time to complete, you can set it a high or favorable priority using the nice command.

- The syntax is as follows:
- $ nice -n niceness-value [command args] 
- sudo nice -n 5 tar -czf backup.tar.gz ./Documents/*
if a program is already running, you can change its priority with the renice command in this form:
- renice -n  -12  -p 1055
15. I changed the priority of a process using the top command
- While the top command is runnin, press r. Give PID value of the process you want to change the process value. Give renice value (from -20 to +19)
16. I examined the kill command
- The basic syntax is as follows:

- kill PID
- kill -s signalName PID
- Where,

- signalNumber : A non-negative decimal integer, specifying the signal to be sent instead of the default TERM.
- signalName : A symbolic signal name specifying the signal to be sent instead of the default TERM.
- PID : Specify the list of processes that kill should signal. Each PID can be any one of the following:
n : If PID is a positive value, the kill command sends the process whose process ID is equal to the PID.
0 : All processes in the current process group are signaled.
-1 : All processes with pid larger than 1 will be signaled i.e. the kill command sends the signal to all processes owned by the effective user of the sender.
- Use the following command to kill pid 257 and exit gracefully:

- kill 257

- How do I specify the signal to send to PID # 4242?
- Pass the -s option to given the signal as a signal number or a signal name. The syntax is:
- $ kill -s signal pid
- $ kill -s stop 4242

17. I learnt commands jobs, fg, bg, nohup
- Displays status of jobs in the current shell session.
- The basic syntax is as follows:jobs
- Option	Description
    -l	Show process id’s in addition to the normal information.
    -p	Show process id’s only.
    -n	Show only processes that have changed status since the last notification are printed.
    -r	Restrict output to running jobs only.
    -s	Restrict output to stopped jobs only.
    -x	COMMAND is run after all job specifications that appear in ARGS have been replaced with the process ID of that job’s process group leader./td>
- The fg command is like bg command except that instead of sending a command in the background, it runs them in the foreground and occupies the current terminal and waits for the process to exit. Without any argument, fg will run the current job in the foreground (vi in this case)
- bg command in linux is used to place foreground jobs in background
- Nohup, short for no hang up is a command in Linux systems that keep processes running even after exiting the shell or terminal.
- I demonstrated how to use command sleep with fg and bg
- ![17.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/17.1.jpg)
- I demonstrated how to use command yes with fg and bg
- ![17.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/17.2.jpg)

# PART2 #

1. I checked the implementability of the most frequently used OPENSSH commands
- ![2.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.1.jpg)
- ![2.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.2.jpg)
2. I implemented basic SSH settings to increase the security
    2.1. Strong Usernames and Passwords
    2.2. Disable Empty Passwords-You need to prevent remote logins from accounts with empty passwords for added security. Open your /etc/ssh/sshd_config file and update the following line:PermitEmptyPasswords no
    2.3.Disable Root Logins. To disable your Root Logins, you’ll need to edit the SSHD configuration file. All your SSH server settings are stored in the /etc/ssh/sshd_config file. Open that file while logging on as root and find the section in the file containing #PermitRootLogin in it.
    2.4. Use Another Port.To change your port, open your /etc/ssh/sshd_config file and add the following lines:

#Run SSH on a non standard port
Port 2025 #Change me
    2.5. Enable Two-Factor Authentication
    2.6.  Use Public/Private Keys for Authentication
 
3. I demonstrated the list the options for choosing keys for encryption in SSH
-l "Fingerprint" Print the fingerprint of the specified public key.
-f "File" Specifies name of the file in which to store the created key.
-t “Type” This option specifies the type of key to be created.
- ![2.3.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.3.jpg)

4. I implemented port forwarding for the SSH client from the host machine to the guest Linux
- I opened in Virtual box -  "Settings" of VM "Centos", chose "Network". attached to "NAT", chose "Port forwarding"
- ![2.4.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.4.1.jpg)
- I clicked -Port Forwarding and asigned port 2222 to 22
- In the "Mobaxterm" i did the settings
- ![2.4.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.4.2.jpg)
- and connected to the VM "Centos"
- ![2.4.3.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.4.3.jpg)
5.  I captured traffic with tcpdump
- ![2.5.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.5.1.jpg)
- and connected to the VM "Centos"
- ![2.5.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m5/task5.3/2.5.2.jpg)
