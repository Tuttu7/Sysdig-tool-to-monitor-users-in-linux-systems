> If your system has bash, the most commonly used shell out there then all commands executed by normal system users will be stored in the   .bash_history hidden file which is kept in each user’s home directory. The content of this file can be viewed by users, using the history command.

```
cat /home/tuttu/.bash_history
```

The date and time when a command was executed is not shown. This is the default setting on most if not all Linux distributions.

To have a real-time view of the shell commands being run by another user logged in via a terminal or SSH, you can use the Sysdig tool in Linux.

Sydig is an open-source, cross-platform, powerful and flexible system monitoring, analysis and troubleshooting tool for Linux. It can be used for system exploration and debugging.

To install sysdig tool in ubuntu based systems 

```
apt install sysdig
```

Once you have installed sysdig, use the spy_users chisel to spy on users by running the command below.

```
sysdig -c spy_users
```

> Sample output

```
# sysdig -c spy_users
14231 18:53:34 tuttu) ls --color=auto -al
14231 18:53:42 tuttu) cd /home/tuttu/Downloads
14231 18:53:49 tuttu) ls --color=auto
14231 18:53:55 tuttu) cat test.txt
14231 18:54:10 tuttu) cd /home/tuttu/Downloads/rsync_directory
14231 18:54:15 tuttu) ls --color=auto
14231 18:54:22 tuttu) touch test
14231 18:54:28 tuttu) mkdir test
14231 18:54:31 tuttu) mkdir test1
14432 18:55:01 root) /bin/sh /usr/lib/sysstat/debian-sa1 1 1
14432 18:55:01 root) /bin/sh /usr/lib/sysstat/sa1 1 1
14432 18:55:01 root) /usr/lib/sysstat/sadc -F -L -S DISK 1 1 /var/log/sysstat
14231 18:55:37 tuttu) cd /home/tuttu
14231 18:55:49 tuttu) cat .bash_history
14231 18:56:05 tuttu) cat /home/tuttu
14231 18:56:15 tuttu) cat /home/tuttu/.bash_history
```
