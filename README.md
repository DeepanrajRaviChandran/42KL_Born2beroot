# 42KL_Born2beroot

42 Born2beroot done in 42 Kuala Lumpur Campus

## Project Details

- System Administration related exercise
- Create your first a virtual machine in VirtualBox
- Create own operating system while implementing.
- The use of VirtualBox is mandatory.
- Turn in a signature.txt file at the root of your repository. You must paste in it the signature of your machine’s virtual disk.

## Mandatory

- Set up your first server
- Operating system to use is the latest stable version of Debian
- Rocky you don’t have to set up KDump. However, SELinux must be running at startup and its configuration has to be adapted for the project’s needs.
- AppArmor for Debian must be running at startup too.
- You must create at least 2 encrypted partitions using LVM
- questions about the operating system you choose.
- differences between aptitude and apt
- what SELinux or AppArmor is.
- SSH service must be running on port 4242 only, it must not be possible to connect using SSH as root.
- The use of SSH will be tested during the defense by setting up a new account. You must therefore understand how it works.
- Configure your operating system with the UFW firewall and leave only port 4242 open.
- Firewall must be active when VM is launched.
- The hostname of your virtual machine must be your login ending with 42 (e.g.,wil42). Must modify this hostname during your evaluation.

- Implement a strong password policy.
 - password has to expire every 30 days
 - minimum number of days allowed before the modification of a password will be set to 2.
 - user has to receive a warning message 7 days before their password expires
 - at least 10 characters long with an uppercase letter, a lowercase letter, and a number and must not contain more than 3 consecutive identical characters.
 - password must not include the name of the user.
 - The following rule does not apply to the root password: The password must have at least 7 characters that are not part of the former password.
 - root password has to comply with this policy.
 - After setting up your configuration files, you will have to change all the passwords of the accounts present on the virtual machine, including the root account.

- install and configure sudo following strict rules
 - Authentication using sudo has to be limited to 3 attempts if incorrect password.
 - A custom message must be displayed if a wrong password error using sudo.
 - actions using sudo has to be archived (input/output) and saved in the /var/log/sudo/ folder (log file).
 - The TTY mode has to be enabled for security reasons.
 - For security reasons too, the paths that can be used by sudo must be restricted.
 Example: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin

- In addition to the root user, a user with your login as username has to be present.
- This user has to belong to the user42 and sudo groups.
- *During the defense, you will have to create a new user and assign it to a group.*
- create a simple script called monitoring.sh, developed in bash.
- every 10 min following info must be displayed (wall)
 - architecture of OS and its kernel version.
 - number of physical processors.
 - number of virtual processors.
 - current available RAM and utilization rate as a percentage.
 - current available memory and utilization rate as a percentage.
 - current utilization rate of your processors as a percentage.
 - date and time of the last reboot.
 - Whether LVM is active or not.
 - number of active connections.
 - number of users using the server.
 - IPv4 address of your server and its MAC (Media Access Control) address.
 - number of commands executed with the sudo program.

- During the defense, you will be asked to explain how this script works. You will also have to interrupt it without modifying it.
Take a look at cron.


## Bonus
- Set up partitions correctly so you get a structure similar
- unctional WordPress website with the following services: lighttpd MariaDB, and PHP.
- Set up a service of your choice that you think is useful (NGINX / Apache2 excluded!). During the defense, you will have to justify your choice.
- To complete the bonus part, you have the possibility to set up extra services. In this case, you may open more ports to suit your needs. Of course, the UFW/Firewalld rules has to be adapted accordingly.

## Submission
- turn in a signature.txt file at the root of your Git repository. To get this signature, you first have to open the default installation folder (it is the folder where your VMs are
saved):
 - Windows: %HOMEDRIVE%%HOMEPATH%\VirtualBox VMs\

- Then, retrieve the signature from the ".vdi" file of your virtual machine in sha1 format.

## Learning & Understanding

- What is a Virtual Machine
- What is a Operating System
- What is a server
- What is system administration
- What is KDump, SELinux, AppArmor
- What is LVM
- signature.txt file in VM's
- differences between aptitude and apt
- what is SSH service, ssh port
- set up new SSH account
- what is UFW Firewall
- VM configuration file
- TTY mode
- wall in terminal
- cron
