# 42KL_Born2beroot

42 Born2beroot done in 42 Kuala Lumpur Campus

## Project Details

- System Administration related exercise
- Create your first a virtual machine in VirtualBox
- Create own operating system.
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
- During the defense, you will have to create a new user and assign it to a group.

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
- functional WordPress website with the following services: lighttpd MariaDB, and PHP.
- Set up a service of your choice that you think is useful (NGINX / Apache2 excluded!). During the defense, you will have to justify your choice.
- To complete the bonus part, you have the possibility to set up extra services. In this case, you may open more ports to suit your needs. Of course, the UFW/Firewalld rules has to be adapted accordingly.

## Submission
- turn in a signature.txt file at the root of your Git repository. To get this signature, you first have to open the default installation folder (it is the folder where your VMs are
saved):
 - Windows: %HOMEDRIVE%%HOMEPATH%\VirtualBox VMs\
- Then, retrieve the signature from the ".vdi" file of your virtual machine in sha1 format.

## Defense Questions

- Questions about the operating system you chose.
- Know the differences between aptitude and apt.
- The difference between SELinux or AppArmor is.
- The use of SSH will be tested during the defense by setting up a new account. You must therefore understand how it works.
- During the defense, you will have to create a new user and assign it to a group.
- During the defense, you will be asked to explain how this script works. You will also have to interrupt it without modifying it.
- During the defense, you will have to justify your choice of the service choosen

## Learning & Understanding

### Virtual Machine
- A virtual machine (VM) is a software emulation of a physical computer, which enables one physical computer (the host) to run multiple operating systems or applications simultaneously within isolated virtual environments. These virtual environments are called virtual machines. Each virtual machine behaves as if it were an independent and complete computer system with its own virtual CPU, memory, storage, network interfaces, and other hardware components.
- Hypervisor: The software responsible for creating and managing virtual machines is called a hypervisor or virtual machine monitor (VMM). The hypervisor allows multiple virtual machines to coexist on the same physical hardware, allocating and managing resources efficiently among them.
- Snapshot and Cloning: Virtual machines often offer the capability to take snapshots, which are point-in-time backups of the VM state. Cloning allows for duplicating a VM quickly, which is useful for deploying multiple instances with similar configurations.

#### Type 1 Hypervisors (Bare-Metal Hypervisors)

- Architecture: Type 1 hypervisors are installed directly on the physical hardware of the host machine. They operate directly on the system's hardware resources without the need for an underlying operating system.

- Performance: Since Type 1 hypervisors run directly on the hardware, they generally offer better performance compared to Type 2 hypervisors. They have direct access to hardware resources, which reduces overhead and improves efficiency.

- Resource Allocation: Type 1 hypervisors can allocate hardware resources (CPU, RAM, etc.) directly to virtual machines, providing more control and better performance.

- Examples: Some examples of Type 1 hypervisors include VMware ESXi, Microsoft Hyper-V Server, and Citrix Hypervisor (formerly XenServer).

- Use Case: Type 1 hypervisors are often used in server virtualization scenarios, data centers, and enterprise-level virtualization deployments, where performance, scalability, and resource management are crucial.

#### Type 2 Hypervisors (Hosted Hypervisors)

- Architecture: Type 2 hypervisors are installed on top of an existing operating system (host OS). They rely on the host OS for access to hardware resources.

- Performance: Type 2 hypervisors introduce some performance overhead since they run as applications within the host operating system. This can lead to slightly reduced performance compared to Type 1 hypervisors.

- Resource Allocation: Type 2 hypervisors depend on the host OS for resource allocation. They request resources from the host OS, which then handles distribution to the virtual machines.

- Examples: Popular Type 2 hypervisors include Oracle VirtualBox, VMware Workstation, and Parallels Desktop.

- Use Case: Type 2 hypervisors are commonly used in desktop or workstation environments, where users may need to run multiple operating systems or experiment with software without modifying the host system. They are also useful for software development and testing purposes.

### Operating System
- An operating system (OS) is a fundamental software component that acts as an intermediary between computer hardware and user-level applications. It manages and controls the resources of a computer system, providing a user-friendly interface and enabling various software programs to run efficiently on the hardware. The operating system plays a crucial role in coordinating all the activities of the computer, ensuring that different processes and applications can work together harmoniously.

### Server
- A server is a computer or a specialized hardware device that provides services, resources, or functionalities to other computers, devices, or users within a network. It is designed to respond to requests and handle various tasks on behalf of its clients, which can be other computers, devices, or applications connected to the network. Servers play a crucial role in facilitating communication, data storage, and resource sharing in computer networks.

### System administration
- System administration, often referred to as sysadmin, is the process of managing and maintaining computer systems, networks, servers, and other IT infrastructure to ensure their efficient and secure operation. System administrators, also known as sysadmins, are responsible for handling various tasks related to the setup, configuration, maintenance, and troubleshooting of hardware, software, and network components within an organization

### KDump
- "Kdump" is a Linux kernel crash dumping mechanism that allows the kernel to capture information about a system crash or kernel panic when it occurs. In the event of a severe system crash, the kdump service takes a snapshot of the crashed kernel's memory and saves it to a pre-configured storage location (such as a disk partition or a network location). This memory dump is useful for post-mortem analysis, debugging, and determining the root cause of the crash.

### SELinux 
- SELinux (Security-Enhanced Linux) is a security framework implemented in the Linux kernel that provides Mandatory Access Control (MAC) capabilities. Developed by the National Security Agency (NSA) and released as open-source software, SELinux aims to enforce fine-grained access controls on various system resources to enhance the overall security of the operating system.
- Traditional discretionary access control (DAC) mechanisms, like the standard Unix file permissions (read, write, execute), allow users and processes considerable freedom in accessing files and resources. However, they may not provide sufficient protection against certain security threats, such as privilege escalation and access control bypass.
- SELinux goes beyond DAC by introducing mandatory access controls, which enforce additional security policies that are not subject to user discretion. It uses a security policy language to define rules and constraints on how processes can access system resources, such as files, directories, sockets, and inter-process communication.

### AppArmor
- AppArmor (Application Armor) is a Linux security module designed to provide an additional layer of security to applications running on a system. It is a mandatory access control framework that restricts the capabilities of individual applications, limiting their access to specific resources and actions, thus reducing the potential damage that could be caused by security breaches or malicious activities.
- AppArmor is a Linux kernel security module that provides an additional layer of Mandatory Access Control (MAC) to enforce security policies for individual applications. Like SELinux, AppArmor aims to enhance the security of Linux systems by restricting the actions and access rights of applications, reducing the potential impact of security breaches and vulnerabilities.
- While AppArmor and SELinux share similar goals of providing mandatory access controls, they use different approaches. AppArmor's path-based security and more straightforward profile syntax may make it a more accessible choice for some users, especially those new to mandatory access controls. However, the choice between AppArmor and SELinux often depends on the specific needs and preferences of the Linux distribution and its users.

#### Summary of AppArmor and SELinux
- Both AppArmor and SELinux (Security Enhanced Linux) are Linux Kernel Securities that are used to increase security in Linux distributions by hardening access to files and processes (AppArmor is the most used for this purpose).
These security systems provide tools to isolate applications from each other... and in turn isolate an attacker from the rest of the system when an application is compromised.

- SELinux
 - SELinux is a kernel module that can be enabled or disabled by the system admin. As access to files and network ports is limited following a security policy, a faulty program or a misconfigured daemon can’t make a huge impact on system security.
 - In its default enforcing mode, SELinux will deny and log any unauthorized attempts to access any resource. This approach usually referred to as the principle of least privilege, means that explicit permission must be given to a user or program to access files, directories, sockets, and other services.

- AppArmor
 - AppArmor is a Linux Security Module implementation of name-based Mandatory Access Controls (MAC). it confines individual programs to a set of listed files.
 - AppArmor is installed and loaded by default. It uses profiles of an application to determine what files and permissions the application requires. Some packages will install their own profiles.

- The Difference between AppArmor and SELinux
 1. SELinux is the Default for Rocky Linux, AlmaLinux, CentOS, and Red Hat.
 2. SELinux is Designed to protect the entire operating system.
 3. AppArmor is the Default for OpenSUSE, Debian and Ubuntu.
 4. AppArmor works with file paths.
 5. AppArmor is less complex and easier for the average user to learn than SELinux.

### LVM
- LVM stands for Logical Volume Manager, and it is a storage management technology used in Linux systems (and some other Unix-like operating systems) to manage disk space efficiently. LVM allows users and system administrators to create, resize, move, and manage logical volumes independently from the physical storage devices, providing flexibility and ease of storage management.
- Physical Volumes (PV): These are the physical storage devices, such as hard drives or solid-state drives, that LVM uses as building blocks. When you initialize a disk for use with LVM, it becomes a physical volume.
- Volume Groups (VG): Volume groups are created by combining one or more physical volumes. The volume group acts as a pool of storage from which logical volumes can be allocated. By grouping multiple physical volumes together, you can create larger and more flexible storage spaces.
- Logical Volumes (LV): Logical volumes are the virtual partitions that are created within a volume group. They serve as the equivalent of traditional partitions, and you can format them with file systems (such as ext4, XFS, etc.) and mount them as if they were regular disks.
- Extents: LVM divides the physical volumes and logical volumes into small chunks called extents. Extents are of a fixed size (e.g., 4 MB), and they are the basic units of storage allocation.
- Allocation Policies: LVM allows you to choose different allocation policies for logical volumes, such as linear, striped, and mirrored. These policies determine how data is distributed across physical volumes for performance and redundancy purposes.
- Resizing: LVM provides the ability to resize logical volumes dynamically. You can extend or shrink logical volumes, even while the system is running, without the need to unmount the file systems or reboot the system.

#### Summary LVM
- LVM stands for Logical Volume Management/Manager, it is a system of managing storage Logical Volumes (Explained below). LVM helps you create flexible disks as well as gives you the ability to manage them dynamically.
- LVM does not deal with physical disks, so in order to create your Logical Volume LVM converts the physical disks to Physical Volumes then collects them in groups called Volume Groups, then Gives them to the Logical Volume.
- Physical Volume (PV): physical storage device. It can be a hard disk, an SD card, a floppy disk, etc. This device provides us with storage available to use.
- Volume Group (VG): to use the space provided by a PV, it must be allocated in a volume group. It is like a virtual storage disk that will be used by logical volumes. VGs can grow over time by adding new VPs.
- Logical volume (LV): these devices will be the ones we will use to create file systems, swaps, virtual machines, etc. If the VG is the storage disk, the LV are the partitions that are made on this disk.
- Conclusion of LVM
 1. LVM does not deal with physical disks.
 2. each Physical Volume has a number of Physical Extents.
 3. each extent has a specific size (default PE size is 4 MO).
 4. A single Physical Extent is the smallest unit of disk space that can be individually managed by LVM

### Aptitude and Apt
- APT (Advanced Package Tool) and Aptitude are package management tools used in Debian-based Linux distributions, such as Debian itself and its derivatives like Ubuntu and Linux Mint. These tools facilitate the installation, removal, and management of software packages on the system, making it easier for users and administrators to handle software installations and updates.

1. APT (Advanced Package Tool):
- APT is a command-line tool used to manage software packages in Debian-based distributions.
- It provides a simple and efficient way to install, upgrade, and remove software packages from the system.
- APT uses a system of repositories to obtain packages and their dependencies. Repositories are servers or online sources where the packages are stored and can be downloaded.
- The main commands in APT include:
 1. apt-get: A command-line utility for handling package management tasks, such as installing, upgrading, and removing packages. For example, apt-get install <package-name> installs a package, and apt-get update updates the local package index from the repositories.
 2. apt-cache: A utility for querying package information from the package cache, such as package details, dependencies, and versions.

2. Aptitude:
- Aptitude is a text-based, interactive front-end to APT, providing a more user-friendly interface for package management.
- It allows users to browse packages, search for software, and select packages for installation or removal using menus and a visual interface.
- Aptitude provides features like package dependency resolution, suggesting solutions to conflicts, and handling package upgrades intelligently.
- Unlike apt-get, Aptitude keeps track of package states and automatically resolves dependencies when installing or removing packages.
- Some common commands in Aptitude include:
 1. aptitude: Running aptitude without arguments opens the interactive interface.
 2. aptitude search <package-name>: Searches for packages matching the given name or keyword.
 3. aptitude install <package-name>: Installs the specified package and its dependencies.
 4. aptitude remove <package-name>: Removes the specified package.

#### Summary of Apt and Aptitude
- apt-get and aptitude  are both package managers that are responsible for any kind of activities related to packages (removing, installing, searchin, updating, upgrading ...). but the most obvious difference between them is that aptitude has a terminal menu interface to interact with, whereas apt-get  doesn't. Rather than the difference in the command line interface, we can say that both aptitude and apt-get are too similar to each other. but we cannot deny that they have some minor differences as instances:
 1. apt-get requires a specific command to remove the eligible files of a particular package whereas aptitude removes them automatically.
 2. aptitude actually performs the functions of not just apt-get, but also some of its companion tools, such as apt-cache and apt-mark
 3. If the actions (installing, removing, updating packages) that you want to take cause conflicts, aptitude  can suggest several potential resolutions. apt-get will just say "I'm sorry Man, I can't allow you to do that.".
 4. aptitude has the why and why-not commands to tell you which manually installed packages are preventing an action that you might want to take.
 5. Aptitude can find you the reason to install a certain package by looking in the list of installed packages and checking if any of their suggested packages have dependencies or any of their dependencies suggests that package or so on.
- So, for most cases, the syntax of Aptitude is kept almost the same as that of apt-get, to make users of apt-get have less pain in migrating to Aptitude, but in addition to this, many powerful features are integrated into Aptitude that makes it the one to be chosen.

- When talking about uninstalling packages using apt package manager, we have the following two options :
 1. remove
 2. purge
- The primary difference being remove and ‘purge‘ is that remove only gets rid of the package leaving any configuration files untouched. Whereas purge not only removes the package but also removes all configuration files OUTSIDE THE HOME DIRECTORY.

- apt-get
apt-get remove <PackageName> # removes only the package and leaves its configuration files
apt-get purge <PackageName> # remove the package including its configuration files

- aptitude
aptitude remove <PackageName> # remove the package including its configuration files

### SSH Service
- SSH (Secure Shell) is a cryptographic network protocol that provides a secure way to access and manage remote computers or devices over a potentially unsecured network, such as the internet. The SSH service, also known as the SSH server, runs on the remote computer and allows users to establish encrypted connections and perform various administrative tasks remotely.

- The primary purposes of the SSH service are as follows:
 1. Secure Remote Access: SSH enables users to log in to a remote system securely. Once connected, users can access the command-line interface or execute specific commands on the remote machine as if they were physically present at the system's console.
 2. Data Encryption: All data transmitted between the SSH client (the user's local computer) and the SSH server (the remote computer) is encrypted, providing protection against eavesdropping and data tampering during transmission.
 3. Authentication: SSH supports various methods of authentication, including password-based authentication, public key authentication, and multi-factor authentication, depending on the server's configuration.
 4. Port Forwarding: SSH allows users to set up secure tunnels for port forwarding, which can be used to securely transfer data between the local and remote systems or to access services running on the remote system as if they were running on the local machine.
 5. File Transfer: SSH can be used for secure file transfer between systems using utilities like SCP (Secure Copy) or SFTP (SSH File Transfer Protocol).

- There are three different techniques that SSH uses to encrypt:
 1. Symmetric encryption: a method that uses the same secret key for both encryption and decryption of a message, for both the client and the host. Anyone who knows the password can access the message that has been transmitted.
 2. Asymmetric encryption: uses two separate keys for encryption and decryption. These are known as the public key and the private key. Together, they form the public-private key pair.
 3. Hashing: another form of cryptography used by SSH. Hash functions are made in a way that they don't need to be decrypted. If a client has the correct input, they can create a cryptographic hash and SSH will check if both hashes are the same.

- The SSH service typically runs on port 22 by default, but this can be configured to use a different port for added security (security through obscurity). SSH can be used to manage remote servers, configure networking devices, perform system administration tasks, and securely access resources on remote networks.

- As SSH encrypts all data during transmission and provides secure authentication mechanisms, it has become the de facto standard for remote access and administration of Linux, Unix, and many other types of systems and devices. It is an essential tool for system administrators, developers, and anyone needing secure remote access to computers and network resources.

#### Summary of SSH Service
- SSH (Secure Shell or Secure Socket Shell) is a network protocol that provides a secure way to connect two machines remotely so they can transmit and receive data securely. It is widely used by administrators to manage systems and applications remotely, deliver software patches as well as exeute commands and move files. By default, an SSH Server listens on TCP (Tranmission Control Protocol) port 22.
- The connection is established by an SSH Client that intends to connect to an SSH Server, the SSH Client starts the connection setup process and uses a pubic key to verify the identity of the SSH Server, after the setup step, the SSH Protcol uses strong symmetric encryption and hashing algorithms to ensure the privacy and integrity of the exchanged data between the Client and the Server.
- Syntax of establishing an SSH Connection
 - ssh <username>@<server ip or hostname> -p <port>

### SSH Port
- The SSH port is the network port number used by the SSH (Secure Shell) protocol to establish encrypted connections between an SSH client and an SSH server. It acts as a communication channel through which secure data transmission and remote access take place.

- By default, SSH uses port number 22 for its communication. When an SSH client initiates a connection to an SSH server, it connects to the server's port 22 by default, assuming no specific port has been configured.

### UFW Firewall
- UFW (Uncomplicated Firewall) is a user-friendly command-line interface for managing iptables, the default firewall management tool in Linux. UFW simplifies the process of configuring firewall rules and provides an easy way for users and administrators to control incoming and outgoing network traffic on a Linux system.
- UFW (Uncomplicated Firewall) is a software application responsible for ensuring that the system administrator can manage iptables in a simple way. Since it is very difficult to work with iptables, UFW provides us with an interface to modify the firewall of our device (netfilter) without compromising security. Once we have UFW installed, we can choose which ports we want to allow connections, and which ports we want to close. This will also be very useful with SSH, greatly improving all security related to communications between devices.

- Key features and functionalities of UFW include:
 1. Simplified Syntax: UFW provides a straightforward and simplified syntax for creating and managing firewall rules. It uses simple commands that are easy to understand, making it accessible to users who are not familiar with the complexities of iptables.
 2. Default Deny: By default, UFW follows a "default deny" policy, meaning that all incoming connections are blocked, and only explicitly allowed connections are permitted. This enhances the system's security posture by requiring explicit rules for access.
 3. Rule Management: UFW allows users to create, enable, disable, and delete firewall rules. Rules can be defined based on various criteria, such as port number, protocol, source or destination IP addresses, and network interfaces.
 4. Application Profiles: UFW includes predefined application profiles that allow users to enable firewall rules for common services and applications, such as SSH, HTTP, HTTPS, etc. This makes it easier to enable firewall access for specific services without manually defining rules.
 5. Logging: UFW can log firewall activity, providing valuable information for monitoring and troubleshooting network traffic.
 6. Integration with Systemd: UFW integrates with systemd, a system and service manager used in modern Linux distributions. This integration allows UFW to automatically start at boot and maintain firewall rules consistently.

- Some common UFW commands include:
    1. sudo ufw enable: Enables the firewall and starts applying the rules.
    2. sudo ufw disable: Disables the firewall, allowing all traffic by default.
    3. sudo ufw allow <port>/<protocol>: Allows incoming traffic on a specific port and protocol.
    4. sudo ufw deny <port>/<protocol>: Blocks incoming traffic on a specific port and protocol.
    5. sudo ufw status: Shows the current status of the firewall and the applied rules.
    6. sudo ufw reset: Resets UFW to its default settings, removing all custom rules.
    7. sudo ufw delete <rule>: Delete UFW's rule
    8. sudo ufw app list: List currently available profiles
    9. sudo ufw allow <profile name>: Enable a profile application
    10. sudo ufw delete allow <profile name>: Disable an application profile

- UFW is particularly useful for desktop users and small to medium-sized server environments, providing an easy-to-use firewall management tool without the need to delve into the complexities of iptables directly.

### iptable
- iptables is a powerful and flexible firewall management tool in Linux that allows users and administrators to set up, maintain, and modify firewall rules. It is a part of the netfilter framework, which is integrated into the Linux kernel and provides packet filtering and network address translation (NAT) functionalities.
- The primary purpose of iptables is to filter and manipulate network traffic, allowing users to control incoming and outgoing packets based on various criteria, such as source and destination IP addresses, port numbers, protocols, and packet states. With iptables, you can enforce security policies, restrict access to services, and protect your system from unauthorized access and network-based attacks.
- UFW provides a more straightforward syntax and a more intuitive approach to configuring firewall rules, making it easier for users and administrators to control network traffic without having to deal directly with the complexity of iptables commands.
- UFW acts as a front-end for iptables, allowing users to manage firewall rules using simple commands that are easy to understand and remember. Behind the scenes, UFW translates these commands into iptables rules and applies them to the Linux kernel's netfilter framework.
- While UFW provides a simplified interface for managing iptables, it is worth noting that using iptables directly allows for more granular control and flexibility, especially for advanced firewall configurations. However, for typical desktop users and small to medium-sized server environments, UFW offers an easy-to-use and effective firewall management tool without the need to delve into the complexities of iptables.

### User and Group Management
- A user in Linux is an entity that has a unique ID, that can manipulate files and performs several operations within the Linux OS. 
- Some USER managing commands
    1. id <username>: Get the user's id
    2. useradd -m -d </home/"name of the directory"> -c <description> <username> : Add a user to the system
        - m -> creates a user with creating its home directory
        - d -> the name of the home directory
        - c -> the description of the creation of the user
        - Here is the absolute path of the default user creation by user add /etc/default/useradd
    3. userdel -r <username>: Delete a user from the system
        - r -> deletes the home directory of the deleted user
    4. passwd <username>: Assign a password to a user

- There are two categories of groups, Primary Group is created automatically when we create a user with the same id as the created user as well as it gets added to the Primary Group to be the first and the only member of that group.
- The second category is the Secondary Group which is created manually by the user using specific commands and we can add a user to it.
- Some GROUP managing commands
    1. groupadd <groupname>: Add a group
    2. groupdel <groupname>: Delete Group
    3. usermod -a -G <groupsname> <username>: Add a user to a particular group
        - a -> appends the user to the supplemental GROUPS
        - G -> new list of supplementary GROUPS
    4. gpasswd -d <username> <groupname>: Delete a user from a particular group

### Password Policy & Commands
#### Password Policies
- Not only in Linux but in every OS, the password policies are so important to generate and build strong passwords in order to avoid a few attacks (most of them are Brute-Force), that's why Linux comes with a library called libpam-cracklib that helps you create a strong password by setting up some options.

- to install the library: apt-get <install libpam-cracklib>
- The config path of the Library is /etc/pam.d/ get in the path then the file called common-password and here is the following options to generate a strong password:
- option=number
    1. lcredit: number of lowercase letters
    2. ucredit: number of uppercase letters
    3. dcredit: number of digits
    4. maxrepeat: number of consecutive identical characters
    5. usercheck: checks if the password has somehow the username
    6. difok: how many characters must not be included in the new password
    7. check_username: checks whether the password has the name of the name straight or reversed
    8. enfore_for_root: enforce the root user with these policies

#### Login Configuration
- The file /etc/login.defs helps when it comes to setting up some conditions related to resetting password (security related)

- There is 3 option you might work with which are:
    1. PASS_MAX_DAYS -> Maximum number of days a password may be used
    2. PASS_MIN_DAYS -> Minimum number of days allowed between password changes
    3. PASS_WARN_AGE -> Number of days warning given before a password expires

- set these options using CLI: 
    - sudo chage --mindays <number> --maxdays <number> --warndays <number> <username>
    - Example :sudo chage --mindays 2 --maxdays 30 --warndays 7 amait-ou

### SUDO
- sudo (short for "SuperUser Do") is a command-line utility in Unix-based operating systems that allows authorized users to execute commands with elevated privileges. These privileges typically belong to the system's superuser, often known as "root." By using sudo, regular users can perform administrative tasks and access sensitive system files and commands without needing to log in as the root user directly.
- The purpose of sudo is to enhance system security by restricting access to critical system functions. It provides a controlled and audited method for users to execute specific commands with administrative permissions while keeping the rest of the system secure from accidental or malicious misuse.
- To use sudo, a user must be listed in the /etc/sudoers configuration file, which determines who is allowed to use sudo and which commands they are permitted to run with elevated privileges. By default, the first user created during the system installation is often added to the sudoers list, allowing them to execute administrative tasks using sudo.
- It is essential to use sudo with caution, as executing certain commands with elevated privileges can have significant consequences on the system. Misuse of sudo can lead to accidental damage or security vulnerabilities. Only use sudo when necessary, and verify that the command you are executing is safe and appropriate.

- Whenever you try to run a command that requires root privileges you will be asked to have root permission, simply here where the role of sudo comes to give you privileges, not only with root but whenever you try to execute a command related to other users or root, you must type sudo so you can get privileged.
- Not all users could use sudo only sudo's group members or those users that were given permission to use sudo within the configuration file suduoers.

- usermod -aG sudo <username>:Add a user to sudo group

- Give the user full sudo access using sudoers file, first of all, run the command visudoand then give it access. Here is the how:
    - syntax: <username> ALL=(ALL) ALL
    - example: dravi-ch ALL=(ALL) ALL

- Note: create a group and give it full sudo access give its members full sudo access as well

#### Configure SUDO
- Going on with the same file sudoers that can be opened using the command visudo (best practice), there are some options that you can add to configure the sudoers file
- Limite the password authentication : Defaults passwd_tries=<number>
- Custome message to be shown when the password is written wrongly : Defaults badpass_message=" your message here"
- Enable the tty by default for security reasons : Defaults requiretty
- Archive sudo commands within a folder :   1. Defaults log_output
                                            2. Defaults log_input
                                            3. Defaults iolog_dir = "path"

### TTY Mode
-  TTY Mode, also known as TTY or TeleTYpewriter mode, refers to the capability of interacting with the system through a terminal or console. TTY represents the physical or virtual terminal used for input and output.
- A TTY is a text-based interface that allows users to interact with the operating system by typing commands and receiving text-based responses. Historically, TTY was associated with physical teleprinter machines, but in modern systems, it represents virtual terminals, such as those accessed through terminal emulators or the Linux virtual consoles.

- In the context of sudo, TTY mode refers to the behavior of sudo when it comes to handling terminal sessions (TTY stands for TeleTYpewriter or Terminal). It determines whether sudo requires the user to enter their password or authenticate using a TTY session.
- By default, when a user runs sudo, sudo requires them to enter their password to authenticate themselves before executing the command with elevated privileges. This password prompt is typically displayed in the same terminal or TTY session where the sudo command was invoked.
- TTY Mode Enabled:
    - In a regular interactive terminal session, sudo prompts the user for their password when they run a command with elevated privileges using sudo.
    - This is the default behavior and is often referred to as "TTY mode enabled" or "askpass mode."

- TTY Mode Disabled:
    - In some cases, when sudo is used in scripts or automated processes, it may not be possible to interactively provide a password.
    - To address this, sudo can be configured to allow password authentication without requiring a TTY session.
    - This mode is called "TTY mode disabled" or "non-interactive mode."
    - In non-interactive mode, sudo will read the password from standard input (stdin) instead of prompting the user for it. This allows the use of sudo in scripts without requiring human interaction.


- Overall, TTY mode is crucial for text-based interaction with the operating system. It is the foundation of the command-line interface (CLI) and plays a significant role in system administration, software development, and various other tasks in Unix-like environments.


### VM configuration file
- A virtual machine (VM) configuration file is a text-based file that contains settings and specifications for a virtual machine. It is a crucial component of virtualization software and is used by virtualization platforms like VMware, VirtualBox, Hyper-V, and others.
- The VM configuration file stores various parameters that define the virtual machine's hardware, operating system settings, and other virtualization-specific options.
- The specific format and location of the VM configuration file vary depending on the virtualization software being used. For Virtual Box it located:
    - VirtualBox: VBOX file (e.g., my_vm.vbox) usually stored in a separate directory named "VirtualBox VMs."

### Wall Command
- The wall command in Unix-like operating systems is used to broadcast a message to all logged-in users on the system. The name "wall" stands for "write all." When you use the wall command, the message you provide as input is sent to every user who is currently logged in, regardless of whether they are using a terminal or logged in remotely.
- The syntax for the wall command : wall [message]
- Keep in mind that the wall command requires administrative privileges, typically provided by the root user or users listed in the sudoers file with appropriate permissions. If you attempt to use wall without sufficient privileges, you may receive a "permission denied" error.

### cron
- cron is a time-based job scheduling program in Unix-like operating systems. It allows users to schedule and automate the execution of commands, scripts, or programs at specific intervals or times. These scheduled tasks are known as "cron jobs."
- The name "cron" comes from the Greek word "chronos," meaning time, which reflects the primary purpose of the tool—to execute tasks at specified times or intervals.
- How cron works:
    1. Cron Daemon: cron runs as a background process called the "cron daemon" or "cron service." The cron daemon continuously checks the system's crontab files for scheduled tasks to execute.
    2. Crontab: The term "crontab" refers to the configuration file used to define cron jobs. Each user can have their own crontab file, which lists the commands or scripts they want to run at specified times.
    3. Scheduled Jobs: When the cron daemon identifies that a scheduled time has arrived based on the crontab entries, it executes the corresponding command or script.
    4. Cron Syntax: Cron jobs are defined using a specific syntax in the crontab file. The syntax consists of five fields (plus a command field) that specify the schedule for the task. The fields represent minutes, hours, days of the month, months, and days of the week when the task should run.

- Common use cases for cron include:
    - Running daily, weekly, or monthly maintenance tasks.
    - Automating backups and data syncing.
    - Generating reports at specific intervals.
    - Running scripts to monitor system health or perform administrative tasks.

#### Crontab Configuration
- The crontab is a file that helps you schedule your programs to be run at a specific time.
- Within the project, you will be asked to create a (monitoring.sh) that runs by the crontab every 10 minutes. the script will display some information related to the system.
- Note -> The bash script monitoring.sh is included under the same name within this repository

- How to use crontab
    - add a crontab job to a specific user : sudo crontab -u <username> -e
        - -u -> specify the username
        - -e -> stands for edit the crontab job
    - With this command a config file will open for adding the crontab job, and here is the syntax to have it properly set : * * * * * command
        - first  * (m)       -> minutes
        - second * ()        -> hours
        - third  *  (dom)    -> day of the month
        - fourth *  (mon)    -> month
        - fifth  *  (dow)    -> day of the week
    - List user's crontab jobs : sudo crontab -l
        - -l -> stands for list crontab jobs

### Step by step

#### Installing Sudo
- Login as root 'su -' or 'su root'


