### Eval Sheet
#### Check Signature.txt
- `cd \Users\PC\VirtualBox VMs\born2beroot`
- `certUtil -hashfile born2beroot.vdi sha1`

#### Project Overview
- How a Virtual Machine Works
    - Use an application like virtualbox to segregate hardware resources
    - type 2 hypervisor , creates an os on top of an exisying os
    - vm os will have its own isolated environment which wont intefere with existing os

- Their choice of operating system.
    - Debian, because its more user friendly for beginners
    - For rocky you need to set up selinux while for debian apparmor comes preinstalled

- The basic differences between Rocky and Debian.
    - Debian uses APT while Rocky uses YUM/DNF
    - Rocky Linux 8 is designed to be a server system
    - Debian is more desktop use case

- The Purpose of virtual machines.
    - You can have multiple os with the same hardware
    - every user have their own machine even at 42
    - Isolation and security purpose as well
    - Can clone and save state of the machine

- the difference between aptitude and apt and 
    - apt stands for "Advanced Packaging Tool".
    - aptitude stands for "Advanced Packaging Tool Interface".
    - Aptitude is a high-level package manager while APT is lower level.
    - They have different syntax
    - apt is more easier to use than aptitude
    - Aptitude is smarter and will automatically remove unused packages or suggest installation of dependent packages while apt will only do what you ask it to do

- what is APPArmor
    - AppArmor (Application Armor) is security system that provides Mandatory Access Control (MAC) security
    - controls the privalges and actions a process or program ca do
    - mainly used to protect systems against malicious programs and spyware but it can also  limit the actions of of a process or program

- During the defense, a script must display information all every 10 minutes.

#### Simple Setup
- Ensure that the machine does not have a graphical environment at launch.
    - `ls /usr/bin/*session`

- Check that the UFW service is started with the help of the evaluator.
    - `sudo ufw status`

- Check that the SSH service is started with the help of the evaluator.
    - `sudo service ssh status`

- Check that the chosen operating system is Debian
    - `head -n 2 /etc/os-release`

#### User 
- Check that it has been added and that it belongs to the "sudo" and "user42" groups.
    - `groups dravi-ch`

- First, create a new user. Assign it a password of your choice, respecting the subject rules. The evaluated student must now explain to you how he was able to set up the rules requested in the subject on their virtual machine.
    - `sudo adduser eval`
    - `getent passwd eval`

- Now that you have a new user, ask the student being evaluated to create a group named "evaluating" in front of you and assign it to this user. Finally, check that this user belongs to the "evaluating" group.
    - `sudo addgroup evaluating`
    - `sudo adduser eval evaluating` or `sudo usermod -aG evaluating eval`
    - `getent group evaluating`
    - `sudo userdel -r eval`
    - `sudo groupdel evaluating`

- Finally, ask the student evaluated to explain the advantages of this password policy, as well as the advantages and disadvantages of its implementation.
    - `Sudo vim /etc/login.defs`
    - `Sudo vim /etc/pam.d/common-password`
    - Basically improved security its hard to guess the password and hard to crack it if there is an attack, basically hinders brute-force attacks
    - Not convenient, remembering strong password is difficult and frustrating if we forget the password
    - Not having recovery mechanisms for the password will be detremental

#### Hostname and Partitions
- Check that the hostname of the machine is correctly formatted as follows: login42 (login of the student evaluated).
    - `hostname`

- Modify this hostname by replacing the login with yours, then restart the machine. If on restart, the hostname has not been updated, the evaluation stops here.
    - `sudo hostnamectl set-hostname <hostname>`
    - `sudo systemctl restart hostname.service`
    - `sudo systemctl restart networking.service`

- You can now restore the machine to the original hostname.
    - `sudo hostnamectl set-hostname dravi-ch42`
    - `sudo systemctl restart hostname.service`
    - `sudo systemctl restart networking.service`

- Ask the student evaluated how to view the partitions for this virtual machine.
    - `lsblk`

- Compare the output with the example given in the subject. Please note: This part is an opportunity to discuss the scores! The student being evaluated should give you a brief explanation of how LVM works and what it is all about.
    - Logical Volume Manager (LVM) is a system for managing disk storage space on Linux systems
    - LVM works by creating a volume group (VG), which is a collection of physical disks or partitions that can be used to create logical volumes
    - Physical Volume : hardisk
    - Volume Group (VG) : It is like a virtual storage disk
    - Logical volume (LV): these devices will be the ones we will use to create file systems


#### SUDO
- Check that the "sudo" program is properly installed on the virtual machine.
    - `dpkg -l | grep sudo`

- The evaluated student should now show assigning your new user to the "sudo" group.
    - `sudo usermod -aG sudo eval`

- The subject imposes strict rules for sudo. The evaluated student must first explain the value and operation of sudo using examples of their choice.
    - "TTY" is an acronym for "teletype", which refers to a computer's terminal interface.
    - To use tty, -t option followed by a TTY number, for example `sudo -t 1 command`
    - In this example, the command will be run on terminal 1

- In a second step, it must show you the implementation of the rules imposed by the subject.
    - `sudo visudo -f /etc/sudoers.d/sudo_config`

- Verify that the "/var/log/sudo/" folder exists and has at least one file. Check the contents
of the files in this folder, You should see a history of the commands used with sudo.
Finally, try to run a command via sudo. See if the file (s) in the "/var/log/ sudo/" folder
have been updated.
    - `sudo cat /var/log/sudo/sudo.log`
    - `sudo ls` or `sudo ufw status`
    - `sudo cat /var/log/sudo/sudo.log`

#### UFW
- Check that the "UFW" program is properly installed on the virtual machine.
    - `dpkg -l | grep ufw`
    - `sudo ufw status numbered`

- Check that it is working properly.
    - go into windows cmd `ssh dravi-ch@localhost -p 4242`

- The evaluated student being evaluated should explain to you basically what UFW is and the value of using it.
    - UFW (Uncomplicated Firewall) is a interface for managing iptables
    - iptables is basically the firewall management tool in Linux
    - So what UFW does is it modify the firewall on which ports to allow connections to and which ports to close. 
    - This is useful in with SSH in our application where we must allow port 4242

- List the active rules in UFW. A rule must exist for port 4242.
    - `sudo ufw status numbered`

- Add a new rule to open port 8080. Check that this one has been added by listing the active rules.
     - `sudo ufw allow 8080`

- Finally, delete this new rule with the help of the student evaluated.
    - `sudo ufw delete <rule_number>`

#### SSH
- Check that the SSH service is properly installed on the virtual machine.
    - `dpkg -l | grep ssh`
    - `sudo service ssh status`

- Check that it is working properly.
     - go into windows cmd `ssh dravi-ch@localhost -p 4242`

- The evaluated student must be able to explain to you basically what SSH is and the value of using it.
    - Secure Shell (SSH) is a network protocol that allows you to remotely connect to a computer through an is encrypted network.
    - SSH is widely used to administer remote servers and you can transfer files between computers when using SSH.

- Verify that the SSH service only uses port 4242.
    - show port fowarding rule
    - `sudo nano /etc/ssh/sshd_config`

- The student evaluated should help you use SSH in order to log in with the newly created user. To do this, you can use a key or a simple password. It will depend on the student being evaluated.
Of course, you have to make sure that you cannot use SSH with the "root" user as stated in the subject.
    - `ssh eval@localhost -p 4242`

#### Script Monitoring 
- How the script works by showing you the code.
    - `cd /usr/local/bin`
    - The first line of the script indicates that the script is to be executed by the Bash shell.
    - Next, the script defines a series of variables that will be used to store system information using grep and unix commands
    - Then, the script uses the wall command to display system information on all terminals connected to the system.

- What is "cron".
    - Cron is a daemon (a background process) that runs commands or scripts at predefined intervals of time. It is primarily used on Unix and Linux systems to schedule tasks to be run automatically.

- How the evaluated student set up their script so that it runs every 10 minutes when the server starts up.
    - `sudo crontab -u root -e`

- Once the correct functioning of the script has been verified, the student evaluated should ensure that this script runs every 1min.

- You can run whatever you want to make sure the script runs with dynamic values correctly, 

- Finally the student evaluated should make the script stop running when the server starts up, but without modifying the script itself. 

- To check this point, you will have to restart the server one last time. At startup, it will be necessary to check that the script
still exists in the same place, that its rights have remained unchanged, and that it has not been modified.

#### Bonus
- Setting up partitions is worth 2 points.

- Setting up WordPress, only with the services required by the subject, is worth 2 points.

- The free choice service is worth 1 point. Verify and test the proper functioning and implementation of each extra service.
For the free choice service, the evaluated student has to give you a
simple explanation about how it works and why they think it is useful.