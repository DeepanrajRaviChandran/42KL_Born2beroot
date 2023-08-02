### Eval Sheet
#### Check Signature.txt
- `cd \Users\PC\VirtualBox VMs\born2beroot`
- `certUtil -hashfile born2beroot.vdi sha1`

#### Project Overview
- How a Virtual Machine Works

- Their choice of operating system.

- The basic differences between Rocky and Debian.

- The Purpose of virtual machines.

- If the evaluated student chose Rocky, what SELinux and DNF are.

- If the evaluated student has chosen : 
    - the difference between aptitude and apt and 
    - what is APPArmor
    - During the defense, a script must display information all
    every 10 minutes.

#### Simple Setup
- Ensure that the machine does not have a graphical environment at launch.

- Check that the UFW service is started with the help of the evaluator.

- Check that the SSH service is started with the help of the evaluator.

- Check that the chosen operating system is Debian

#### User 
- Check that it has been added and that it belongs to the "sudo" and "user42" groups.

- First, create a new user. Assign it a password of your choice, respecting the subject rules. The evaluated student must now explain to you how he was able to set up the rules requested in the subject on their virtual machine.

- Now that you have a new user, ask the student being evaluated to create a group named "evaluating" in front of you and assign it to this user. Finally, check that this user belongs to the "evaluating" group.

- Finally, ask the student evaluated to explain the advantages of this password policy, as well as the advantages and disadvantages of its implementation. Of course, answering that it is because the subject asks for it does not count.

#### Hostname and Partitions
- Check that the hostname of the machine is correctly formatted as follows: login42 (login of the student evaluated).

- Modify this hostname by replacing the login with yours, then restart the machine. If on restart, the hostname has not been updated, the evaluation stops here.

- You can now restore the machine to the original hostname.

- Ask the student evaluated how to view the partitions for this virtual machine.

- Compare the output with the example given in the subject. Please note: This part is an opportunity to discuss the scores! The student being evaluated should give you a brief explanation of how LVM works and what it is all about.

#### SUDO
- Check that the "sudo" program is properly installed on the virtual machine.

- The evaluated student should now show assigning your new user to the "sudo" group.

- The subject imposes strict rules for sudo. The evaluated student must first explain the value and operation of sudo using examples of their choice.

- In a second step, it must show you the implementation of the rules imposed by the subject.

- Verify that the "/var/log/sudo/" folder exists and has at least one file. Check the contents
of the files in this folder, You should see a history of the commands used with sudo.
Finally, try to run a command via sudo. See if the file (s) in the "/var/log/ sudo/" folder
have been updated.
If something does not work as expected or is not clearly explained, the evaluation stops here.

#### UFW
- Check that the "UFW" program is properly installed on the virtual machine.

- Check that it is working properly.

- The evaluated student being evaluated should explain to you basically what UFW is and the value of using it.

- List the active rules in UFW. A rule must exist for port 4242.

- Add a new rule to open port 8080. Check that this one has been added by listing the active rules.

- Finally, delete this new rule with the help of the student evaluated.

#### SSH
- Check that the SSH service is properly installed on the virtual machine.

- Check that it is working properly.

- The evaluated student must be able to explain to you basically what SSH is and the value of using it.

- Verify that the SSH service only uses port 4242.

- The student evaluated should help you use SSH in order to log in with the newly created user. To do this, you can use a key or a simple password. It will depend on the student being evaluated.
Of course, you have to make sure that you cannot use SSH with the "root" user as stated in the subject.

#### Script Monitoring 
- How the script works by showing you the code.

- What is "cron".

- How the evaluated student set up their script so that it runs every 10 minutes when the server starts up.

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