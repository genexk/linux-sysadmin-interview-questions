Linux System Administrator/DevOps Interview Questions
====================================================

A collection of linux sysadmin/devops interview questions. Feel free to contribute via pull requests, issues or email messages.


## <a name='toc'>Table of Contents</a>

  1. [Contributors](#contributors)
  1. [General Questions](#general)
  1. [Simple Linux Questions](#simple)
  1. [Medium Linux Questions](#medium)
  1. [Hard Linux Questions](#hard)
  1. [Expert Linux Questions](#expert)
  1. [Networking Questions](#network)
  1. [MySQL Questions](#mysql)
  1. [DevOps Questions](#devop)
  1. [Fun Questions](#fun)
  1. [Demo Time](#demo)
  1. [Other Great References](#references)


#### [[⬆]](#toc) <a name='contributors'>Contributors:</a>

* [moregeek](https://github.com/moregeek)
* [typhonius](https://github.com/typhonius)
* [schumar](https://github.com/schumar)
* [negesti](https://github.com/negesti)
* peter
* [andreashappe](https://github.com/andreashappe)
* [quatrix](https://github.com/quatrix)
* [biyanisuraj](https://github.com/biyanisuraj)
* [pedroguima](https://github.com/pedroguima)
* Ben
* [bharatnc](https://github.com/bharatnc)


#### [[⬆]](#toc) <a name='general'>General Questions:</a>

* What did you learn yesterday/this week?
* Talk about your preferred development/administration environment. (OS, Editor, Browsers, Tools etc.)
* Tell me about the last major Linux project you finished.
* Tell me about the biggest mistake you've made in [some recent time period] and how you would do it differently today. What did you learn from this experience?
* Why we must choose you?
* What function does DNS play on a network?
* What is HTTP?
* What is an HTTP proxy and how does it work?
* Describe briefly how HTTPS works.
* What is SMTP? Give the basic scenario of how a mail message is delivered via SMTP.
* What is RAID? What is RAID0, RAID1, RAID5, RAID10?
* What is a level 0 backup? What is an incremental backup?
```
Incremental backups can be either level 0 or level 1. A level 0 incremental backup, which is the base for subsequent incremental backups, copies all blocks containing data, backing the datafile up into a backup set just as a full backup would. The only difference between a level 0 incremental backup and a full backup is that a full backup is never included in an incremental strategy.
```
* Describe the general file system hierarchy of a Linux system.
* Which difference have between public and private SSH key?


#### [[⬆]](#toc) <a name='simple'>Simple Linux Questions:</a>

* What is the name and the UID of the administrator user?
0
* How to list all files, including hidden ones, in a directory?
```
ls -la
```
* What is the Unix/Linux command to remove a directory and its contents?
```
rm -rf
```
* Which command will show you free/used memory? Does free memory exist on Linux?
```
free -m #-m for mega -b for bytes, -k -g etc. -h human readable
```
* How to search for the string "my konfu is the best" in files of a directory recursively?
```
grep -r "my konfu is the best"
-i ignore case, -v inverse, -n line number, grep "^start.*" can use regex, -c count # of matching lines
```
* How to connect to a remote server or what is SSH?
```
ssh user@host
```
* How to get all environment variables and how can you use them?
```
env
env -i command #run cmd with no env, unset variable_name
```
* I get "command not found" when I run ```ifconfig -a```. What can be wrong?
```
nettools package not installed?
```
* What happens if I type TAB-TAB?
```
auto-complete
```
* What command will show the available disk space on the Unix/Linux system?
```
df
-a all info, -h human readable, -T print type, -i show inode info
```
* What commands do you know that can be used to check DNS records?
```
dig @ns_server redhat.com NS +noall +answer
dig redhat.com +short #ipaddress only
dig axfr domain #domain transfer
nslookup -type=any/mx/ns... hostname dnsserver
host hostname
```
* What Unix/Linux commands will alter a files ownership, files permissions?
```
chown -R user:group filename # -R for recursive
```
* What does ```chmod +x FILENAME``` do?
```
add all execute 
-R for recursive
+X for directory
+s setuid # execute the file as file owner
+t sticky # file can't be modified by anyone but owner
chmod =rwx,g+s samplescript.sh
```
* What does the permission 0750 on a file mean?
* What does the permission 0750 on a directory mean?
* How to add a new system user without login permissions?
```
adduser -r -s /bin/nologin newuser
-r for system user, but really no difference between this and a normal user, only in a specific range of uid #s
```
* How to add/remove a group from a user?
```
remove user from group in /etc/group
usermod
-g change primary group
-G add secondary groups
```
* What is a bash alias?
```
alias foo="echo bar"
```
* How do you set the mail address of the root/a user?
* What does CTRL-c do?
```
send sigstop
```
* What does CTRL-d do?
```
Control+D is EOF (End-Of-File). It closes the stdin pipe. If read(STDIN) returns 0, it means stdin closed, which means CTRL+D was hit (assuming there is a keyboard at the other end of the pipe).
```
* What does CTRL-z do?
```
send sigint
```
* What is in /etc/services?
```
programs can do a getportbyname() sockets call in their code in order to understand what port they should use
name port/protocol aliases comments
smtp 25/tcp mail
```
* How to redirect STDOUT and STDERR in bash? (> /dev/null 2>&1)
```
> /dev/null 2>&1
```
* What is the difference between UNIX and Linux.
```
different kernel code
```
* What is the difference between Telnet and SSH?
```
ssh is encrypted by a shared secret
```
* Explain the three load averages and what do they indicate. What command can be used to view the load averages?
```
1, 5, 15 minutes average runqueue length
```
* Can you name a lower-case letter that is not a valid option for GNU ```ls```?
* What is a Linux kernel module?
```
pieces of code that can be loaded and unloaded into the kernel upon demand.  They extend the functionality of the kernel without the need to reboot the system. drivers, etc
lsmod
modinfo module_name
To list the options that are set for a loaded module: systool -v -m module_name
modprobe module_name #load module
insmod filename [args] #load module by file
modprobe -r module_name #remove module
```
* Walk me through the steps in booting into single user mode to troubleshoot a problem.
* Walk me through the steps you'd take to troubleshoot a 404 error on a web application you administer.
* What is ICMP protocol? Why do you need to use?

#### [[⬆]](#toc) <a name='medium'>Medium Linux Questions:</a>

* What do the following commands do and how would you use them?
 * ```tee```
 ```
 ls | tee filename
 ```
 * ```awk```
 ```
 awk -F: '{print $1}' /etc/passwd
 ```
 * ```tr```
 ```
 tr [] {}
 tr -d [] #delete char
 tr -s #squeez
 ```
 * ```cut```
 ```
 cut -b #byte -c #char
 cut -f #field -d delimiters
 ```
 * ```tac```
 ```
 inverse cat
 ```
 * ```curl```
 ```
 curl -h #header
 -O #original filename
 -o filename #
 -L follow redirects
 ```
 * ```wget```
 * ```watch```
 * ```head```
 * ```tail```
 * ```less```
 * ```cat```
 * ```touch```
 * ```sar```
 ```
 sar -u 1 3 # -u cpu usage, every 1 sec 3 times
 -P core#/ALL # 0 for first core
 -r memory
 -S swapspace
 -b general i/o
 -d all block devices
 -w context switch/sec
 -q runqueue and load avg
 -n KEYWORD #network stats, DEV devices, SOCK socket usage...ALL for all usage
 ```
 * ```netstat```
 ```
 -a all
 -t tcp
 -u udp
 -p pid
 -n ip numbers
 -l listening port only
 -r routing info
 -i list interfaces
 -s statistics
 ```
 * ```tcpdump```
 ```
 tcpdump -C 512 -W 8 -s 256 -w /data/support/tcpdump/gpdbgang_issue -i bond0 "tcp port 8020"
 -A include ascii, 
 filters: tcp, udp, host x.x.x.x, dst/src x.x.x.x, and or not for combining filters
 -s capture size, -n/nn n not resolve hostname nn not resolve hostname and port
 -W filename, -v/vv verbose
 ```
 * ```lsof```
 ```
 list all open files
 -u user
 -i TCP:22-200 # or -i :port
 -i 4/6 #ipv4/6
 -i all network connection
 -p pid
 fuser filename
 ```
 * ```ncat```
 ```
 ncat -l 8080 #listen to port 8080
 ncat 192.168.1.100 8080 #connect to port 8080 on remote server
 ncat -l 8080 | ncat 192.168.1.200 80 #proxy
 # 2 way traffic
 $ mkfifo 2way
 $ ncat -l 8080 0<2way | ncat 192.168.1.200 80 1>2way
 ncat -l 10000 -e /bin/bash #-e attach shell to port 10000, this gives access to whoever connects to this port (backdoor)
 ```
 * ```dd```
 ```
 dd if = /dev/sda of = /dev/sdb
 dd if=/dev/hda1 of=~/partition.img
 dd if = hdadisk.img of = /dev/hdb
 dd if = /dev/cdrom of = tgsservice.iso bs = 2048
 dd if=/dev/zero of=/dev/sdb
 dd if=/dev/zero of=/swapfile bs=1024 count=200000
 ```
* What does an ```&``` after a command do?
* What does ```& disown``` after a command do?
* What is a packet filter and how does it work?
* What is Virtual Memory?
* What is swap and what is it used for?
* What is an A record, an NS record, a PTR record, a CNAME record, an MX record?
* Are there any other RRs and what are they used for?
* What is a Split-Horizon DNS?
```
provide 2 views of dns records to different set of users (internal vs external)
```
* What is the sticky bit?
* What does the immutable bit do to a file?
```
chatter +i filename #make the file immutable
chatter -i filename #unset
```
* What is the difference between hardlinks and symlinks? What happens when you remove the source to a symlink/hardlink?
```
softlink okay
hardlink file+hardlink is deleted
```
* What is an inode and what fields are stored in an inode?
```
where the file is on the device, dates, number of links
```
* How to force/trigger a file system check on next reboot?
```
touch /forcefsck
```
* What is SNMP and what is it used for?
* What is a runlevel and how to get the current runlevel?
```
init runlevel#
use runlevel command to check current level
```
* What is SSH port forwarding?
* What is the difference between local and remote port forwarding?
* What are the steps to add a user to a system without using useradd/adduser?
* What is MAJOR and MINOR numbers of special files?
* Describe the mknod command and when you'd use it.
* Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.
* Describe a scenario when deleting a file, but 'df' not showing the space being freed.
* Describe how 'ps' works.
* What happens to a child process that dies and has no parent process to wait for it and what’s bad about this?
* Explain briefly each one of the process states.
* How to know which process listens on a specific port?
* What is a zombie process and what could be the cause of it?
* You run a bash script and you want to see its output on your terminal and save it to a file at the same time. How could you do it?
* Explain what echo "1" > /proc/sys/net/ipv4/ip_forward does.
* Describe briefly the steps you need to take in order to create and install a valid certificate for the site https://foo.example.com.
* Can you have several HTTPS virtual hosts sharing the same IP?
* What is a wildcard certificate?
* Which Linux file types do you know?
* What is the difference between a process and a thread? And parent and child processes after a fork system call?
* What is the difference between exec and fork?
* What is "nohup" used for?
```
prevent hangup signal
```
* What is the difference between these two commands?
 * ```myvar=hello``` this will not be inherited by child process
 * ```export myvar=hello``` this will
* How many NTP servers would you configure in your local ntp.conf?
* What does the column 'reach' mean in ```ntpq -p``` output?
* You need to upgrade kernel at 100-1000 servers, how you would do this?
* How can you get Host, Channel, ID, LUN of SCSI disk?
* How can you limit process memory usage?
* What is bash quick substitution/caret replace(^x^y)?
* Do you know of any alternative shells? If so, have you used any?
* What is a tarpipe (or, how would you go about copying everything, including hardlinks and special files, from one server to another)?
* How can you tell if the httpd package was already installed?
* How can you list the contents of a package?
* How can you determine which package is better: openssh-server-5.3p1-118.1.el6_8.x86_64 or openssh-server-6.6p1-1.el6.x86_64 ?
* Can you explain to me the difference between block based, and object based storage?

#### [[⬆]](#toc) <a name='hard'>Hard Linux Questions:</a>

* What is a tunnel and how you can bypass a http proxy?
* What is the difference between IDS and IPS?
* What shortcuts do you use on a regular basis?
* What is the Linux Standard Base?
* What is an atomic operation?
* Your freshly configured http server is not running after a restart, what can you do?
* What kind of keys are in ~/.ssh/authorized_keys and what it is this file used for?
* I've added my public ssh key into authorized_keys but I'm still getting a password prompt, what can be wrong?
* Did you ever create RPM's, DEB's or solaris pkg's?
* What does ```:(){ :|:& };:``` do on your system?
* How do you catch a Linux signal on a script?
* Can you catch a SIGKILL?
* What's happening when the Linux kernel is starting the OOM killer and how does it choose which process to kill first?
* Describe the linux boot process with as much detail as possible, starting from when the system is powered on and ending when you get a prompt.
* What's a chroot jail?
* When trying to umount a directory it says it's busy, how to find out which PID holds the directory?
* What's LD_PRELOAD and when it's used?
* You ran a binary and nothing happened. How would you debug this?
* What are cgroups? Can you specify a scenario where you could use them?
* How can you remove/delete a file with file-name consisting of only non-printable/non-type-able characters?
* How can you increase or decrease the priority of a process in Linux?
* What are run-levels in Linux?


#### [[⬆]](#toc) <a name='expert'>Expert Linux Questions:</a>

* A running process gets ```EAGAIN: Resource temporarily unavailable``` on reading a socket. How can you close this bad socket/file descriptor without killing the process?
* What do you control with swapiness?
```
sudo sysctl vm.swappiness=10
0 for not swapping until memory is full
1 for lowest swapping aggressiveness
100 for highest
swapoff -a #also disable swap partitions
```
* How do you change TCP stack buffers? How do you calculate it?
* What is Huge Tables? Why isn't it enabled by default? Why and when use it?
* What is LUKS? How to use it?


#### [[⬆]](#toc) <a name='network'>Networking Questions:</a>

* What is localhost and why would ```ping localhost``` fail?
* What is the similarity between "ping" & "traceroute" ? How is traceroute able to find the hops.
* What is the command used to show all open ports and/or socket connections on a machine?
* Is 300.168.0.123 a valid IPv4 address?
* Which IP ranges/subnets are "private" or "non-routable" (RFC 1918)?
* What is a VLAN?
* What is ARP and what is it used for?
* What is the difference between TCP and UDP?
* What is the purpose of a default gateway?
* What is command used to show the routing table on a Linux box?
* A TCP connection on a network can be uniquely defined by 4 things. What are those things?
* When a client running a web browser connects to a web server, what is the source port and what is the destination port of the connection?
* How do you add an IPv6 address to a specific interface?
* You have added an IPv4 and IPv6 address to interface eth0. A ping to the v4 address is working but a ping to the v6 address gives you the response ```sendmsg: operation not permitted```. What could be wrong?
* What is SNAT and when should it be used?
* Explain how could you ssh login into a Linux system that DROPs all new incoming packets using a SSH tunnel.
* How do you stop a DDoS attack?
* How can you see content of an ip packet?
* What is IPoAC (RFC 1149)?
* What will happen when you bind port 0?



#### [[⬆]](#toc) <a name='mysql'>MySQL questions:</a>

* How do you create a user?
* How do you provide privileges to a user?
* What is the difference between a "left" and a "right" join?
* Explain briefly the differences between InnoDB and MyISAM.
* Describe briefly the steps you need to follow in order to create a simple master/slave cluster.
* Why should you run "mysql_secure_installation" after installing MySQL?
* How do you check which jobs are running?
* How would you take a backup of a MySQL database?

#### [[⬆]](#toc) <a name='devop'>DevOps Questions:</a>

* Can you describe your workflow when you create a script?
* What is GIT?
* What is a dynamically/statically linked file?
* What does "./configure && make && make install" do?
* What is puppet/chef/ansible used for?
* What is Nagios/Zenoss/NewRelic used for?
* What is Jenkins/TeamCity/GoCI used for?
* What is the difference between Containers and VMs?
* How do you create a new postgres user?
* What is a virtual IP address? What is a cluster?
* How do you print all strings of printable characters present in a file?
* How do you find shared library dependencies?
* What is Automake and Autoconf?
* ./configure shows an error that libfoobar is missing on your system, how could you fix this, what could be wrong?
* What are the advantages/disadvantages of script vs compiled program?
* What's the relationship between continuous delivery and DevOps?
* What are the important aspects of a system of continuous integration and deployment?
* How would you enable network file sharing within AWS that would allow EC2 instances in multiple availability zones to share data?

#### [[⬆]](#toc) <a name='fun'>Fun Questions:</a>

* A careless sysadmin executes the following command: ```chmod 444 /bin/chmod ``` - what do you do to fix this?
* I've lost my root password, what can I do?
* I've rebooted a remote server but after 10 minutes I'm still not able to ssh into it, what can be wrong?
* If you were stuck on a desert island with only 5 command-line utilities, which would you choose?
* You come across a random computer and it appears to be a command console for the universe. What is the first thing you type?
* Tell me about a creative way that you've used SSH?
* You have deleted by error a running script, what could you do to restore it?
* What will happen on 19 January 2038?
* How to reboot server when reboot command is not responding?


#### [[⬆]](#toc) <a name='demo'>Demo Time:</a>

* Unpack test.tar.gz without man pages or google.
* Remove all "*.pyc" files from testdir recursively?
* Search for "my konfu is the best" in all *.py files.
* Replace the occurrence of "my konfu is the best" with "I'm a linux jedi master" in all *.txt files.
* Test if port 443 on a machine with IP address X.X.X.X is reachable.
* Get http://myinternal.webserver.local/test.html via telnet.
* How to send an email without a mail client, just on the command line?
* Write a ```get_prim``` method in python/perl/bash/pseudo.
* Find all files which have been accessed within the last 30 days.
* Explain the following command ```(date ; ps -ef | awk '{print $1}' | sort | uniq | wc -l ) >> Activity.log```
* Write a script to list all the differences between two directories.
* In a log file with contents as ```<TIME> : [MESSAGE] : [ERROR_NO] - Human readable text``` display summary/count of specific error numbers that occurred every hour or a specific hour.


#### [[⬆]](#toc) <a name='references'>Other Great References:</a>

Some questions are 'borrowed' from other great references like:

* https://github.com/darcyclarke/Front-end-Developer-Interview-Questions
* https://github.com/kylejohnson/linux-sysadmin-interview-questions/blob/master/test.md
* http://slideshare.net/kavyasri790693/linux-admin-interview-questions
