# Basics
## What is Linux
Linux is a kernel which is core of an operating system and is open source.

However, on its own, Linux lacks a lot of things that make a complete operating system, for example GUI tools, text editors and browsers to use.

Ubuntu and Redhat are operating systems built on top of linux kernel.

## What is open source
Open source means the source code is available publicly and anyone can see, modify and distribute as they need. 

## what is kernel
`Ref: https://www.redhat.com/en/topics/linux/what-is-the-linux-kernel`

The Linux® kernel is the main component of a Linux operating system (OS) and is the core interface between a computer’s hardware and its processes.

### What the kernel does
The kernel has 4 jobs:

1.  **Memory management:** Keep track of how much memory is used to store what, and where
2.  **Process management:** Determine which processes can use the central processing unit (CPU), when, and for how long
3.  **Device drivers:** Act as mediator/interpreter between the hardware and processes
4.  **System calls and security:** Receive requests for service from the processes

### Where the kernel fits within the OS
Think of a [Linux](https://www.redhat.com/en/topics/linux) machine as having 3 layers:

1.  **The hardware:** The physical machine—the bottom or base of the system, made up of memory (RAM) and the processor or central processing unit (CPU), as well as input/output (I/O) devices such as [storage](https://www.redhat.com/en/topics/data-storage), [networking](https://www.redhat.com/en/topics/hyperconverged-infrastructure/what-is-software-defined-networking), and graphics. The CPU performs computations and reads from, and writes to, memory.
2.  **The Linux kernel:** The core of the OS. (See? It’s right in the middle.) It’s software residing in memory that tells the CPU what to do.
3.  **User processes:** These are the running programs that the kernel [manages](https://www.redhat.com/en/topics/management). User processes are what collectively make up user space.


## What is Operating System
OS includes kernel and user interface tools, manages the systems hardware and resources like CPU, RAM and Storage devices.

## Ubuntu Vs Redhat
Ubuntu | Redhat
:----- | :----
Developed by canonical | Developed by Red Hat
Initially released on 20 October 2004 | Initially released on 13 may 1995
Is widely used on desktops and server version is also available | RHEL widely used on servers and can be used on desktops
Uses Deb package manager | Uses RPM (Redhat package manager)

## RHEL, Fedora and CentOS
**RedHat enterprise Linux** is a commercial Linux Distribution from Redhat, free to use and charged for support.
**Fedora** is the testing laboratory of **RedHat** which is well known for its bleeding edge technology implementation, which is released every six month.
**CentOS** is another distribution which is **RedHat** minus Non-Free packages. **CentOs** is a stable distribution hence latest version of all packages is pushed into its [RPM](https://www.tecmint.com/20-practical-examples-of-rpm-commands-in-linux/ "RPM Commands") after testing, the focus remains on stability of distribution.

## What is hypervisor
`Ref: https://www.vmware.com/topics/glossary/content/hypervisor.html`

A **hypervisor**, also known as a virtual machine monitor or VMM, is software that creates and runs virtual machines (VMs). A hypervisor allows one host computer to support multiple guest VMs by virtually sharing its resources, such as memory and processing.

### Types of hypervisors
- **Type 1 hypervisor** - ex: XEN,ESXI or KVM
   acts like a lightweight operating system and runs directly on the host’s hardware.
- **Type 2 hypervisor** - ex: VMware workstation, Oracle Virtualbox
   runs as a software layer on an operating system, like other computer programs.

### Container vs hypervisor
**Hypervisors:**
-   Allow an operating system to run independently from the underlying hardware through the use of virtual machines.
-   Share virtual computing, storage and memory resources.
-   Can run multiple operating systems on top of one server (bare-metal hypervisor) or installed on top of one standard operating system and isolated from it (hosted hypervisor).

**Containers:** 
-   Allow applications to run independently of an operating system. 
-   Can run on any operating system—all they need is a container engine to run. 
-   Are extremely portable since in a container, an application has everything it needs to run.

## What is shell
Shell is the user interface for a Linux OS.  
`echo $SHELL` to know your current shell.  
ex: Bash, Cshell, ksh

## Physical, Virtual and Cloud servers
### Physical servers
OS is installed on directly on hardware, hardware includes RAM, hard disk and NIC-NetworkInterfaceCard etc..
The resources are not shared.
Servers either accessed directly or remotely if they are deployed on a Data Center.
### Virtual servers
OS is installed on hypervisor, resources (RAM,DISK and NIC) are shared.
The underlying hardware/server will be mostly deployed on remote Data Centers owned by individual companies.
### Cloud servers
The servers are deployed on cloud providers(ex Amazon, Microsoft, or Google) data centers.

## Linux Login methods
- ssh
    - Password authentication
    - Public key authentication
- Console login
- LDAP
- SSO
- Multifactor Authentication
- 2FA 

### SSH login
More widely used authentication/login method.
Use SSH client (putty) to log into the server remotely over port 22.

Setup SSH
Enable root login
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/v2v_guide/preparation_before_the_p2v_migration-enable_root_login_over_ssh
Enable remote login
Configure password less authentication/ Public key authentication

## File System Structure
`Ref: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/ch-filesystem`

Red Hat Enterprise Linux uses the _Filesystem Hierarchy Standard_ (_FHS_) file system structure, which defines the names, locations, and permissions for many file types and directories.

The Linux File Hierarchy Structure or the Filesystem Hierarchy Standard (FHS)   
defines the directory structure and directory contents in Unix-like operating systems.   
In the FHS, all files and directories appear under the root directory / , even if they are stored on different physical or virtual devices.   
Most of these directories exist in all UNIX operating systems and are generally used in much the same way.

**Common Directories**   
/                     - "Root," the top of the file system hierarchy  
|__  /bin         - Binaries and other executable programs  
|__ /sbin        - similar to the /bin dir, intended to be run by root user.
|__  /boot       - contains static files required to boot the system  
|__  /dev        - contains device nodes that represent the devices attached to the system  
|__  /etc         - System configuration files  
|__  /home     - Users' home directories   
|__  /lib          - contains libraries needed by the essential binaries in the /bin and /sbin
                        Libraries needed by the /usr/bin are located under /usr/lib
|__  /media   - Automatically detected removable media is mounted in the `/media` directory.  
|__  /mnt       - reserved for temporarily mounted file systems, such as NFS file system mounts. 
|__  /opt        - reserved for software and add-on packages that are not part of the default installation.
|__  /srv        - contains site specific data served by RHEL system  
|__  /tmp       - Temporary files. Often not preserved between system reboots     
|__  /usr        - (multi-)user utilities and applications  
|__  /proc     - contains special files that either extract information from the kernel or send information to it
|__  /var        - log files  

/  - "Root," the top of the file system hierarchy.   
   - Every single file and directory starts from the root directory 
   - Only root user has the right to write under this directory.   
   - /root is root user's home directory, which is not same as /

/bin  - Binaries and other executable programs.
   - Common linux commands are located here e.g. ps, Is, ping, grep, cp

/boot - contains static files required to boot the system, for example, the Linux kernel. 
            These files are essential for the system to boot properly.
> Note: Do not remove the `/boot/` directory. Doing so renders the system unbootable.

           
/etc  - System configuration files.   
   - Contains configuration files required by all programs.   
   - This also contains startup and shutdown shell scripts used to start/stop individual 
       programs.   
      Example: /etc/resolv.conf, /etc/logrotate.conf.

/home - Users' home directories  
   • Home directories for all users to store their personal files, and settings.  
   • Example: /home/userl, /home/user2

/opt   - Optional application software packages.   
   - Contains add-on applications from individual vendors.   
   - Add-on applications installed through rpms should be installed under either /opt/ 
      or /opt/sub-directory.

/tmp - Temporary files. Often not preserved between system reboots    
   • Directory that contains temporary files created by system and users.   
   • Files under this directory are deleted when system is rebooted.

/usr - Secondary hierarchy for read-only user data
   - contains the majority of (multi-)user utilities and applications.

/var  - Variable data, most notably log files.

/proc - contains special files that either extract information from the kernel or send information to it. Examples of such information include system memory, CPU information, and hardware configuration

# Users
`Ref: https://www.redhat.com/sysadmin/linux-user-group-management`

## Managing Users
### /etc/passwd file
User account information is stored in the `/etc/passwd` file.
This information includes the account name, home directory location, and default shell, among other values.

Example of /etc/passwd file
`username:password:UID:GID:comment:home:shell`
`user1:x:1001:1001::/home/user1:/bin/bash`

> /etc/passwd file should not be edited directly by tools such as Vi.
### /etc/shadow file
Long ago, password hashes were stored in the `/etc/passwd` file. This file was world-readable, allowing inquisitive users to pull password hashes for other accounts from the file and run them through password-cracking utilities. Eventually, the password hashes were moved to a file readable only by root: `/etc/shadow`.

Example
`username:password:last password change:min:max:warning:inactive:expired`

The password information is manipulated with the `chage` command.

### Create, modify, and delete user accounts
- Create - `usedadd`  - `sudo useradd user1`
  > After creating the user set the password using `passwd`
- Modify - `usermod` - `sudo usermod user1 --login userone --comment "User One"`
    - -   `--comment` (`-c`): Modifies the comment field
    -   `--home` (`-d`): Modifies home directory information
    -   `--expiredate` (`-d`): Changes account-expiration settings
    -   `--login` (`-l`): Modifies the username
    -   `--lock` (`-L`): Locks a user account
    -   `--unlock` (`-U`): Unlocks a user account
- Delete - `userdel` - `sudo userdel user1`
    -   `--force` (`-f`): Deletes the account (including mail and home directory), even if the user is still logged in
    -   `--remove` (`-r`): Deletes the account (including mail and home directory), but the user must be logged out
### Managing group membership
-   `usermod`: Update group membership
-   `id`: Display a list of groups the user is a member of
-   `cat /etc/group`: Show a list of existing groups, with membership displayed in the last field

# Package management
Package management is a method of installing, updating, removing, and keeping track of software updates from specific repositories (repos) in the Linux system.

## How to add a YUM repository
It is always recommended you use a _known_ repository, such as Extra Packages for Enterprise Linux (EPEL), which is hosted at [fedoraproject.org](http://fedoraproject.org/).
Once you determine which repository you need, there are several different ways to install and enable it.

### Install a repository `.rpm`
The first is to install an `.rpm` with the repository information.
`yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm`

### Manually set up a repository
1. create a `.repo` file within `/etc/yum.repo.d` using a text editor.
```sh
$ vi /etc/yum.repo.d/mysql57-community.repo
[mysql57-community]  # Section, and can have more than one
name=MySQL 5.7 Community Server # Repo name
baseurl=http://repo.mysql.com/yum/mysql-5.7-community/el/7/$basearch/ 

# optional
enabled=1 
gpgcheck=1 
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```
2. Verify its configured properly
`yum-config-manager mysql57-community`
3. List all the repos
`yum repolist`    

## Dependency
If a certain package requires a certain resource such as a shared library, or another package, it is said to have a dependency. All modern package management systems provide some method of dependency resolution to ensure that when a package is installed, all of its dependencies are installed as well.

## Packaging system
Almost all the software that is installed on a modern Linux system will be found on the Internet. It can either be provided by the distribution vendor through central repositories (which can contain several thousands of packages, each of which has been specifically built, tested, and maintained for the distribution) or be available in source code that can be downloaded and installed manually.

Because different distribution families use different packaging systems (Debian: ***.deb** / CentOS: ***.rpm** / openSUSE: ***.rpm** built specially for openSUSE), a package intended for one distribution will not be compatible with another distribution. However, most distributions are likely to fall into one of the three distribution families.

## Package tools - Low level/ High level
- **low-level** tools
   which handle in the backend the actual installation, upgrade, and removal of package files)
- **high-level** tools
   which ensures the dependency resolution and metadata searching -”data about the data”.

**DISTRIBUTION** | **LOW-LEVEL TOOL** | **HIGH-LEVEL TOOL**
:-- | :-- | :--
Debian (Ubuntu) | dpkg | apt-get / aptitude
CentOS / Redhat | rpm |yum
openSUSE | rpm | zypper

`Do not attempt to install on CentOS a *.rpm file that was built for openSUSE, or vice-versa!`

### Common Usage of Low-Level Tools
`Install/Upgrade a package manually when it is not available in the central repositories, by using low level tools.`

1. Installing a package from a compiled (*.deb or *.rpm) file
    ```sh
dpkg -i file.deb 		#Debian and derivative
rpm -i file.rpm 		#CentOS / openSUSE
    ```
2. Upgrading a package from a compiled file
```sh
dpkg -i file.deb 		#Debian and derivative
rpm -U file.rpm 		#CentOS / openSUSE
```
3. Listing installed packages
```sh
dpkg -l 		#Debian and derivative
rpm -qa 		#CentOS / openSUSE

```
4. Find, if a package is installed
```sh
dpkg --status package_name 		#Debian and derivative
rpm -q package_name 			#CentOS / openSUSE

```
5. Find out, which package installed a file
```sh
dpkg --search file_name      #Debian and derivative
rpm -qf file_name            #CentOS / openSUSE
```

### Common Usage of High-Level Tools
1. Searching for a package
```sh
aptitude search package_name     # Debian/Ubuntu
apt-get search package_name      # Debian/Ubuntu

yum search package_name               # Redhat /Centos
yum search all package_name           # Search for pkg_name in package names and description.
yum whatprovides “*/package_name”     # To know that package we will have to install

zypper search package_name		 #On openSUSE
```
2. Install a package
```sh
apt-get install package_name 		      # Debian and derivatives
yum install package_name 			      # CentOS
zypper install package_name 		      # OpenSUSE
```
3. Remove/Unistall a package
```sh
apt-get remove/purge package_name         # Debian
yum erase package_name                    # Centos
zypper remove -package_name               # openSUSE
```
`**Remove** will uninstall the package but leaving configuration files intact, whereas purge will erase every trace of the program from your system.`

4. Update installed packages
```sh
apt-get update
yum update 
```
5. history
`yum history`

gives you an overview of what happened in past transactions. This provides some useful information, like the date when the transaction happened and what command was run.

You can undo or redo certain transactions using the `history` command
`yum history undo <id>`

# Soft and Hard links
links in UNIX are pointers pointing to a file or a directory. Creating links is a kind of shortcuts to access a file. Links allow more than one file name to refer to the same file, elsewhere. 

There are two types of links :
1.  Soft Link or Symbolic links
2.  Hard Links

##  Soft Links
`ln  -s <original filename> <link name>`
`stat <filename>`
- A soft link is similar to the file shortcut feature which is used in Windows Operating systems.
- Soft Link contains the path for original file and not the contents
- Removing soft link doesn’t affect anything but removing original file, the link becomes “dangling” link which points to nonexistent file.
- A soft link can link to a directory.
- If we change the name of the original file then all the soft links for that file become dangling
- Link across file systems: If you want to link files across the file systems, you can only use symlinks/soft links.

## Hard Links
`ln  <original filename> <link name>`
-   Each hard linked file is assigned the same Inode value as the original, therefore they reference the same physical file location. Hard links more flexible and remain linked even if the original or linked files are moved throughout the file system, although hard links are unable to cross different file systems.
-   ls -l command shows all the links with the link column shows number of links.
-   Links have actual file contents
-   Removing any link, just reduces the link count, but doesn’t affect other links.
-   Even if we change the filename of the original file then also the hard links properly work.
-   We cannot create a hard link for a directory to avoid recursive loops.
-   If original file is removed then the link will still show the content of the file.
-   The size of any of the hard link file is same as the original file and if we change the content in any of the hard links then size of all hard link files are updated.
-   The disadvantage of hard links is that it cannot be created for files on different file systems and it cannot be created for special files or directories.

# File/Dir permissions
For effective security, Linux divides authorization into 2 levels.
1. Ownership
2. Permission


In the above o/p first column,
"-" indicates a file
"d" indicates a directory
"i" indicates a link

Column 2-4 indicates permission for the owner
Column 5-7 indicates permission for group
Column 8-10 indicates permission for other users

Permissions “r” is for read, “w” is for write, and “x” is for execute.

In Lunux permissions can be set using two methods
1. Symbolic method
2. Absolute method (Numeric method)
 
## To change directory  permissions
-   **chmod +rwx filename** to add permissions.
-   **chmod -rwx directoryname** to remove permissions.

## To change permission for Group Owners and Others
-   **chmod g+w filename**
-   **chmod o+w filename**

To change permissions for everyone, use “u” for users, “g” for group, “o” for others, and “ugo” or “a” (for all).

**chmod ugo+rwx foldername**
**chmod a=r foldername**

## Change Groups for Files and Directories
-   **chgrp groupname filename**
-   **chgrp groupname foldername**

`Note that the group must exist before you can assign groups to files and directories.`

## To Change Ownership for files and folders
-   **chown name filename**
-  **chown name foldername**

`These commands will give ownership to someone, but all sub files and directories still belong to the original owner.`

To change ownership for all sub files and folders
-   **chown -R name directoryname**

## Absolute method (Change Permissions in Numeric Code)
-   **0 = No Permission**
-   **1 = Execute**
-   **2 = Write**
-   **4 = Read**

Basically, you add up the numbers depending on the level of permission you want to give.

Permission in numbers are:

-   **0 = ---**
-   **1 = --x**
-   **2 = -w-**
-   **3 = -wx**
-   **4 = r-**
-   **5 = r-x**
-   **6 = rw-**
-   **7 = rwx**

For example:

-   **chmod 777 foldername** will give read, write, and execute permissions for everyone.
-   **chmod 700 foldername** will give read, write, and execute permissions for the user only.

## Umask
The **umask** command returns, or sets, the value of the system's file mode creation mask.

New files and directories permissions can be defined using umask.

`System default permissions for files: 666 and Directories:777`

### Specifying the file creation mask using numeric representation
#### The other permission digit
In octal representations of file permissions, there are actually four digits. The three important digits we've discussed are the last three digits. The first digit is a special file permission indicator, and for this discussion can be considered always to be zero. So from here on out, when we discuss file permission **777**, it may also be referred to as **0777**.

### So how does the umask actually work?

The **umask** _masks_ permissions by restricting them by a certain value.

Essentially, each digit of the umask is "subtracted" from the OS's default value to arrive at the default value you define. It's not really subtraction; technically, the mask is negated (its [bitwise](https://www.computerhope.com/jargon/b/bitwoper.htm) compliment is taken) and this value is then applied to the default permissions using a [logical AND](https://www.computerhope.com/jargon/b/boolean.htm) operation. The result is that the umask tells the operating system which permission bits to "turn off" when it creates a file.

In Linux, the default permissions value is **666** for a regular file, and **777** for a directory. When creating a new file or directory, the [kernel](https://www.computerhope.com/jargon/k/kernel.htm) takes this default value, "subtracts" the umask value, and gives the new files the resulting permissions.

So if our **umask** value is **022**, then any new files will, by default, have the permissions **644** (666 - 022). Likewise, any new directories will, by default, be created with the permissions **755** (777 - 022).

To see current system umask
`umask`
`umask -S` for symbolic notation

### Specifying the file creation mask using symbols
_user class symbol_ may be one or more of the following:

**u**

User (the owner of the file).

**g**

Group (any member of the file's defined group).

**o**

Other (anyone else).

**a**

All (equivalent to **ugo**).

_permissions operator_ may be one of the following:

**+**

allow the specified file permissions to be enabled for the specified user classes (permissions that are not specified are unchanged in the mask).

**-**

prohibit the specified file permissions from being enabled for the specified user classes (permissions that are not specified are unchanged in the mask).

**=**

allow the specified file permissions to be enabled for the specified user classes (permissions not specified will be prohibited by the mask during file creation).

for example,
`umask u+w`

sets the mask so that when files are created, they have permissions which allow write permission for the user (file owner). The rest of the file's permissions would be unchanged from the operating system default.

Multiple changes can be specified by separating multiple sets of symbolic notation with commas
`umask u-x,g=r,o+w`

> Note that if you use the equals operator ("**=**"), any permissions not specified will be specifically prohibited. For example, the command
> `umask a=`
   Sets the file creation mask so that new files are inaccessible to everyone.

### Specifying the file creation mask using numeric representation
   `umask 022`
   > This is the same as running **umask 0022**; if you specify only three digits, the first digit will be assumed to be zero.

## Sticky Bit
The sticky bit was initially introduced to ‘stick’ an executable program’s text segment in the swap space even after the program has completed execution, to speed up the subsequent runs of the same program. However, these days with faster storage and RAM the sticky bit means something entirely different.

Think of a scenario where you create a Linux directory that can be used by all the users of the Linux system for creating files. Users can create, delete or rename files according to their convenience in this directory. For all those who think that why would such a directory be created? There exists, for example, /tmp directory in the Linux system that can be used by different Linux users to create temporary files.
Now, what if an user accidentally or deliberately deletes (or rename) a file created by some other user in this directory?

Well, to avoid these kind of issues, the concept of sticky bit is used.

A Sticky bit is a permission bit that is set on a file or a directory that lets only the owner of the file/directory or the root user to delete or rename the file. No other user is given privileges to delete the file created by some other user.

Usage | command
:-- | :--
Set the sticky bit | `chmod +t <dir/file>`
Remove sticky bit | `chmod -t <dir/file>`
Check the sticky bit | `ls -al `

## The setuid bit
This bit is present for files which have executable permissions. The setuid bit simply indicates that when running the executable, it will set its permissions to that of the user who created it (owner), instead of setting it to the user who launched it. Similarly, there is a setgid bit which does the same for the gid.

Set the setuid bit
`chmod u+s <file>`

## The setgid bit
The setgid affects both files as well as directories. When used on a file, it executes with the privileges of the group of the user who owns it instead of executing with those of the group of the user who executed it.
When the bit is set for a directory, the set of files in that directory will have the same group as the group of the parent directory, and not that of the user who created those files. This is used for file sharing since they can be now modified by all the users who are part of the group of the parent directory.

Set the setgid bit
`chmod g+s <dir>`

# VI Editor
   You can use the **vi** editor to edit an existing file or to create a new file from scratch in Linux.
   An improved version of the vi editor which is called the **VIM**.

   Create or Open an existing file
   `vi testfile`
   The above command will generate the following output −
   ```
   |
   ~
   ~
   ~
   "testfile" [New File]
   ```
   You will notice a **tilde** (~) on each line following the cursor. A tilde represents an unused line. If a line does not begin with a tilde and appears to be blank, there is a space, tab, newline, or some other non-viewable character present.

## Operating modes
While working with the vi editor, we usually come across the following two modes −

-   **Command mode** − This mode enables you to perform administrative tasks such as saving the files, executing the commands, moving the cursor, cutting (yanking) and pasting the lines or words, as well as finding and replacing. In this mode, whatever you type is interpreted as a command.
    
-   **Insert mode** − This mode enables you to insert text into the file. Everything that's typed in this mode is interpreted as input and placed in the file.

## Commands
Command | Usage
:--- | :---
Exit without saving | `:q!`
Save and exit | `:wq`
Save and exit | `:zz`
Save file as file2 | `:w <file2>`
searches forwards (downwards) | `:/ `
searches backwards (upwards) | `:?`
Displays lines with line numbers on the left side | `:set nu`

# Process management
A Program loaded into memory and executing is called a process.
## Process types and states
**Foreground process** - Initiated and controlled through a terminal session.
**Background process** - Process not connected to a terminal

**Process states**
Running
Waiting
Stopped
Zombie/Defunct
Orphaned

**List of all processes**
`ps -aux`

**List system mem and CPU usage**
`top`
`htop`

Usage | Command
:--- | :---
List all running processes | `ps -A`
List processes owned by you | `ps -X`
`ps -e`
`ps -r`
List processes by a user | `ps -fU test1`
List processes by a group | `ps -fG group1`
List custom fields | `ps -eo pid,ppid,user,cmd`
Real time monitoring | `watch -n 1 'ps -eo pid,%mem,%cpu, --sort=-%mem | head'` 

# Service Management
The fundamental purpose of an init system is to initialize the components that must be started after the Linux kernel is booted (traditionally known as “userland” components). The init system is also used to manage services and daemons for the server at any point while the system is running.

## Starting and Stopping Services
To start a `systemd` service, executing instructions in the service’s unit file, use the `start` command.  
`sudo systemctl start <service name>`  
`sudo systemctl stop <service/application name>

## Restarting and Reloading
To restart a running service, you can use the `restart` command:

```bash
sudo systemctl restart <application>
```

If the application in question is able to reload its configuration files (without restarting), you can issue the `reload` command to initiate that process:

```bash
sudo systemctl reload <application>
```

If you are unsure whether the service has the functionality to reload its configuration, you can issue the `reload-or-restart` command. This will reload the configuration in-place if available. Otherwise, it will restart the service so the new configuration is picked up:

```bash
sudo systemctl reload-or-restart <application>
```
## Enabling and Disabling Services
To tell `systemd` to start services automatically at boot, you must enable them.

To start a service at boot, use the `enable` command:
```bash
sudo systemctl enable <application>
```

This will create a symbolic link from the system’s copy of the service file (usually in `/lib/systemd/system` or `/etc/systemd/system`) into the location on disk where `systemd` looks for autostart files (usually `/etc/systemd/system/some_target.target.wants`. We will go over what a target is later in this guide).

To disable the service from starting automatically, you can type:
```bash
sudo systemctl disable application.service
```

This will remove the symbolic link that indicated that the service should be started automatically.

> enabling a service does not start it in the current session. If you wish to start the service and also enable it at boot, you will have to issue both the `start` and `enable` commands.

## Checking the Status of Services

To check the status of a service on your system, you can use the `status` command:

```bash
systemctl status <application.service>
```
This will provide you with the service state, the cgroup hierarchy, and the first few log lines.

```sh
systemctl is-active application.s
systemctl is-enabled application.service
systemctl is-failed application.service
```

## Listing all services/Units
Usage | Command
:-- | :--
List active units | `systemctl list-units`
List all units | `systemctl list-units --all`
List only inactive | `systemctl list-units --all --state=inactive`
List unit files | `systemctl list-unit-files`

# Networking
https://www.redhat.com/sysadmin/sysadmin-essentials-networking-basics
https://medium.com/@IBMDeveloper/learn-linux-101-networking-fundamentals-e8d9ece93b1f
https://www.networkworld.com/article/2693416/unix-networking-basics-for-the-beginner.html

https://www.redhat.com/sysadmin/beginners-guide-network-troubleshooting-linux

## What is a network?
In computing, a network is a collection of two or more computers that can communicate.
In order for networking to facilitate communication between devices, the machines on the network must be able to find each other.

The systems responsible for making this possible are TCP and IP.

## Transmission Control Protocol (TCP)
Communication requires a means of transport for messages between them, and computers communicate using digital signals carried over Ethernet cables or radio waves or microwaves.

The specifications for this are formally defined as the [TCP protocol](https://tools.ietf.org/html/rfc793).

## Internet protocol (IP)
Computers on a network identify themselves and each other with IP addresses, such as 10.0.0.1 or 192.168.0.8.
These are also generally mapped to hostnames, such as `laptop` and `desktop` or `darkstar` or `penguin` or whatever name you give each machine.

The specifications for this are formally defined as the [IP protocol](https://tools.ietf.org/html/rfc791).

## Minimal networking
The most simple network possible is a single-node network.
This might seem like it's cheating, but in fact, it's a valid network in the sense that a computer needs to know how to address itself.

Each computer considers itself as the `localhost` node, with an internal-only IP address of 127.0.0.1.

You can verify this with the `ping` command:
```sh
ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data. 64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.031 ms
```

The `localhost` designation is defined in the `/etc/hosts` file:

## View your network interfaces on Linux
`ip address show`

## Assign a static IP address on Linux
`sudo ip address add 169.254.0.1 dev eth0`

Normally, an IP address is assigned dynamically from a dedicated DHCP server or a router running an embedded DHCP server.

It's the job of the DHCP server to broadcast offers for addresses over its network.

When a computer gets connected to a network, it requests an address.

The DHCP server assigns it one and registers which device on the network, identified by its media access control (MAC) address, has been assigned which address.

That's how computers know how to find one another across a network.

Usage | Command
:--- | :---
View network interfaces | `ip address show`
Assign a static ip address | `sudo ip address add 169.254.0.1 eth0`
Add another IP address to an interface | `sudo ip a change 192.168.0.5 eth0`
link status on all network devices | `ip link show`
Show network statistics | `ip -s -h l show dev eth0`
Show the IP address of a single interface | `ip a show dev eth0`
Display route table | `ip route`
add a route | `sudo ip route add default via 192.168.254.1 dev enp1s0`
restart the connection | `sudo nmcli con down enp1s0` <br> `sudo nmcli con up enp1s0`
Edit a connection | `sudo nmcli connection edit enp7s0`
nslookup command | `nslookup redhat.com`
displays the network connectivity path | `tracepath -n sat65server`
List of ports and listening status | `netstat -a`
List all ports status | ` netstat -tlupn`

## Firewall
A firewall is defined as **a solution or service that regulates, protects, and blocks network traffic as it passes to and from a server.**

The Linux kernel includes the _Netfilter_ subsystem, which is used to manipulate or block network traffic headed into or through your server. All modern Linux firewall solutions use this system for packet filtering.

### IPTABLES
The kernel’s packet filtering system would be of little use to administrators without a userspace interface to manage it. This is the purpose of iptables: When a packet reaches your server, it will be handed off to the Netfilter subsystem for acceptance, manipulation, or rejection based on the rules supplied to it from userspace via iptables.

### ufw - Uncomplicated Firewall
The default firewall configuration tool for Ubuntu is ufw. Developed to ease iptables firewall configuration, ufw provides a user-friendly way to create an IPv4 or IPv6 host-based firewall.

ufw by default is initially disabled.

“ufw is not intended to provide complete firewall functionality via its command interface, but instead provides an easy way to add or remove simple rules. It is currently mainly used for host-based firewalls.”

Usage | command
:-- | :--
Enable ufw | `sudo ufw enable`
Check the status | `sudo ufw status`
Open a ssh port | `sudo ufw allow 22`
Rules can be added using numbered format | `sudo ufw insert 1 allow 80`
View the numbered format | `sudo ufw status numbered`
close an opened port | `sudo ufw deny 22`
Delete a rule | `sudo ufw delete deny 22`

# Disk management
## Creating standard partition
Partition is nothing but creating logical regions on the hard disk/storage device.

Primary partition ?
extended partition ?

### Steps for creating partition
Attach new disk to the server
Scan for new hardware changes or reboot
fdisk /dev/newdiskname
n, part type, Specify size and save & exit
udevadm settle
mark file system
Mount and add fstab entry for permanent mount

### Steps for deleting a partition
Run final archive backup
Bring down applications hosted on partition
un-mount mount point
delete partition using fdisk/gdisk utilities
Destroy the HDD

List the connected Hard disks
`lsblk`
`fdisk -l`

Scan for new disks
`udevadm trigger`
`fdisk -l` or `lsblk`

If the new disk doesnt list
`ls /sys/class/scsi_host/ |while read host; do echo "---" > /sys/class/scsi_host/$host/scan; done`

then list
`fdisk -l` or `lsblk`

Format and create fs on new disk
`fdisk /dev/sdb`
- n - new partition
- P - Primary partition
- size can be mention as +2G
- wq - save and exit

run `udevadm settle`
list them `lsblk` or `fdisk -l`

create Logical partition on the newly created physical partition
`fdisk /dev/sdb`
- n 
- l - logical partition
- mention size +1G
- wq
`udevadm settle`

create a file system
`mkfs.ext4 /dev/sdb5`
`mkfs.xfs /dev/sdb1`

Create mount point `mkdir /data1`
mount the new fs  `mount /dev/sdb1 /data1`
list them `df -h` or `df -Th`

## Delete a partition
Unmount  `umount /data1`
                 `df -h`
`fdisk /dev/sdb`
- d - delete a partition
- mention the number
- P - list the partitions
- wq - save and exit

`udevadm settle`
`lsblk`


# LVM
https://www.redhat.com/sysadmin/lvm-vs-partitioning

# Job scheduling
## Cron
The Cron daemon is a built-in Linux utility that runs processes/scripts on your system at a scheduled time. Cron reads the **crontab** (cron tables) for predefined commands and scripts.

###  Crontab Syntax
_**Cron**_ reads the configuration files for a list of commands to execute. The daemon uses a specific syntax to interpret the lines in the _**crontab**_ configuration tables.

`a b c d e /directory/command output`

- The first five fields **`a b c d e`** specify the time/date and recurrence of the job.
- In the second section, the **`/directory/command`** specifies the location and script you want to run.
- The final segment **`output`** is optional. It defines how the system notifies the user of the job completion.

#### Cron Job Time Format
The first five fields in the command represent numbers that define when and how often the command runs. A space separates each position, which represents a specific value.

The table below summarizes possible values for the fields and the example syntax:

Field | Possible values | Syntax | Notes 
:-- | :-- | :-- | :--
[a] minute | 0-59 | 7 * * * * | Every 7 minutes
[b] Hour | 0-23 | 0 7 * * * | 7 am every day
[c] day | 0-31 | 0 0 7 * * | every month 7th
[d] month | 0-12 | 0 0 0 7 * | July 1st
[e] day of the week | 0-7 | 0 0 * * 7 | every sunday (0,7 means sunday)

> Cron uses local time
> We can easily determine our schedule on [https://crontab.guru/](https://crontab.guru/)

#### Use special string to save time
Instead of the first five fields, you can use any one of eight special strings. It will not just save your time but it will improve readability.

Special string | Meaning
:-- | :--
@reboot | Run once, at startup.
@yearly | Run once a year, `0 0 1 1 *`
@annually | (same as @yearly)
@monthly | Run once a month, `0 0 1 * *`
@weekly | Run once a week, `0 0 * * 0`
@daily | Run once a day, `0 0 * * *`
@midnight |(same as @daily)
@hourly | Run once an hour, `0 * * * *`

#### Script to execute
mention the absolute path of the script
`/root/backup.sh`

#### Output (Optional)
By default, **`cron`** sends an email to the owner of the crontab file when it runs. 

As this is an optional feature, you can prevent that scenario by disabling the output email. To turn off email output, add the following string, **`>/dev/null 2>&1`,** after the timing and command fields.

```
* * * * * directory/command >/dev/null 2>&1
```

### Using Operators
For efficiency, cron syntax also uses operators. Operators are special characters that perform operations on the provided values in the cron field.

-   **An asterisk (*)** stands for all values. Use this operator to keep tasks running during all months, or all days of the week.
-   **A comma (,)** specifies separate individual values.
-   **A dash (–)** indicates a range of values.
-   **A forward-slash (/)** is used to divide a value into steps. (*/2 would be every other value, */3 would be every third, */10 would be every tenth, etc.)

### Setting Up a Cron Job
Check cron service status  
`sudo systemctl status cron`

-   `crontab -a <filename>`: create a new `<filename>` as crontab file for the current user
-   `crontab -e`: edit crontab file or create one if it doesn’t already exist for the current user
-   `crontab –u other_username –e` : Edit crontab for a Different User
-   `crontab -l`: show up our crontab file
-   `crontab -r`: delete our crontab file
-   `crontab -v`: show up the last time we have edited our crontab file

### Default /etc/crontab file and /etc/cron.d/* directories
**/etc/crontab** is system crontabs file. Usually only used by root user or daemons to configure system wide jobs. 
**/var/spool/cron/crontabs or /var/cron/tabs/** is directory for personal user crontab files.

Additionally, cron reads the files in /etc/cron.d/ directory. 
Usually system daemon such as sa-update or sysstat places their cronjob here

Directory | Description
:-- | :--
/etc/cron.d/ | Put all scripts here and call them from /etc/crontab file.
/etc/cron.daily/ | Run all scripts once a day
/etc/cron.hourly/ | Run all scripts once an hour
/etc/cron.monthly/ | Run all scripts once a month
/etc/cron.weekly/ | Run all scripts once a week

### How do I backup installed cron jobs entries?
Simply type the following command to backup your cronjobs to a nas server mounted at /nas01/backup/cron/users.root.bakup directory:  
`crontab -l > /nas01/backup/cron/users.root.bakup  
`crontab -u userName -l > /nas01/backup/cron/users.userName.bakup`

## At
The **at** command is used for jobs that only need to be run once. These jobs are run from either the command line or from scripts. The **at** entries do not go in the **crontab** files.

The **at** command reads from standard input the names of commands to be run at a later time and allows you to specify when the commands should be run

## Submitting an at job
`echo <_command to execute_> |at -t 950603220000`
`echo <_command to execute_> |at now + 200 minutes`

The Date variable to the **-t** flag is specified using the following format:

[[CC]YY]MMDDhhmm[.SS]

The digits in the Date variable are defined as follows:

-   CC specifies the first two digits of the year (the century).
-   YY specifies the second two digits of the year.5
-   MM specifies the month of the year (01 through 12).
-   DD specifies the day of the month (01 through 31).
-   hh specifies the hour of the day (00 through 23).
-   mm specifies the minute of the hour (00 through 59).
-   SS specifies the second of the minute (00 through 59).
-   Both the CC and YY digits are optional. If neither is given, the current year is assumed.

# Nice and Renice
**Nice** command in Linux helps in execution of a program/process with modified scheduling priority. It launches a process with a user-defined scheduling priority. In this, if we give a process a higher priority, then Kernel will allocate more CPU time to that process. 
**Renice** command allows you to change and modify the scheduling priority of an already running process.

Niceness values  range from -20 (most favorable to the process) to 19 (least favorable  to the process).

Check NICE value
`ps -el`
```
$ ps -el |more
F S   UID     PID    PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0       1       0  0  80   0 - 25470 -      ?        00:00:01 systemd
1 S     0       2       0  0  80   0 -     0 -      ?        00:00:00 kthreadd
1 I     0       3       2  0  60 -20 -     0 -      ?        00:00:00 rcu_gp
1 I     0       4       2  0  60 -20 -     0 -      ?        00:00:00 rcu_par_gp
1 I     0       6       2  0  60 -20 -     0 -      ?        00:00:00 kworker/0:0H-kblockd
```

Set the priority of a new process
`nice -10 <process/script> # This sets a nice value of 10`
`nice --10 <process> # This sets a nice value of -10`

Change the priority of a running process
`Sudo renice -n 15 -p <PID> #sets a nice of 15`
`sudo renice -15 <PID> # sets a nice of -15`
`sudo renice 15 <PID> # sets a nice of 15`
`sudo renice -n 10 -g <Groupname> #Set the priority of all programs of a group`
`sudo renice -n 10 -u <username> #set the priority of all programs of a user`

`nice #shows the current default nice value`

# SFTP setup
Data security and credentials encryption are the thumb rules for a system administrator. FTP (File Transfer Protocol) is great for transferring files, but it is not as secure to use over the network. By using this protocol, your data and credentials are transferred without any encryption method. SFTP, abbreviated as Secure File Transfer Protocol, is used for providing better security. SFTP works over the SSH protocol by providing the encryption required to establish a secure connection. Therefore, you can transfer data to or from your local computer system in a secure way. Hence, the secure file transfer protocol (SFTP) is more secure than the simple file transfer protocol (FTP). Sometimes, you may need to provide remote access to the SFTP/FTP server to the development teams or other clients. In this case, SFTP allows you to provide secure limited access to specific directories and files.

## Prereqs
You need root privileges or sudo access for creating a new SFTP user and for executing the administrative commands.

## Setting up SFTP Server on Ubuntu 20.04
1. Install SSH
2. Change SSHD configuration for SFTP group
3. Restart/Reload SSH services
4. Create SFTP users group
5. Create a new SFTP user
6. Grant permissions to the specific directory

### Step1. Install SSH
Check if its installed or not
`apt list --installed |grep -i ssh`
`systemctl status ssh #Is ssh running`

### Step2. Change SSHD configuration for SFTP group
Paste the following lines at the end of the file: /etc/ssh/sshd_config
```
Match group sftp  
ChrootDirectory /home  
X11Forwarding no  
AllowTcpForwarding no  
ForceCommand internal-sftp
```
The above configuration will allow the sftp users group to access their home directories through the SFTP. However, not allowed to access the normal SSH shell.

### Step3. Reload SSH service
`sudo systemctl reload ssh`
`systemctl status ssh # Check the reload status`

### Step4. Create SFTP users group
To grant SFTP access to users, you will create SFTP user accounts. First, create a new user group for ‘SFTP’ users. For our convenience, all SFTP users will belong to the same group.

`sudo addgroup sftp`

### Step 5: Create a new SFTP user
Once the new group is added, create a new sftp user and then add this user into the sftp group

`sudo useradd -m sftp -g sftp`

Set the password for the newly created sftp user
`passwd sftpuser`

### Step 6: Grant permissions to the specific directory
Grant full permissions to the sftp user on their home directory. But, block other users on the system from accessing this directory.
`sudo chmod 700 /home/sftpuser`

SFTP server configurations are completed. 
Now, you can log in with the sftp credentials to check either everything is working properly or not.

## Login through the SFTP
You can log in via the SFTP using two different methods.
1.  Connect to the SFTP by using the command line method
2.  Connect to the SFTP using the GUI

### Connect to the SFTP by using the command line method
```shell
sftp <username>@<serverip>

Example:
master@master:~$ sftp sftpuser@192.168.0.105
The authenticity of host '192.168.0.105 (192.168.0.105)' can't be established.
ECDSA key fingerprint is SHA256:6EYMJFcMywhTzol4xEV2ZbX20n2Xx8oV1Le2OskPRDY.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '192.168.0.105' (ECDSA) to the list of known hosts.
sftpuser@192.168.0.105's password:
Connected to 192.168.0.105.
sftp> ls
jumphost  sftpuser  test2
sftp> bye #to Exit

```

## Usefull FTP commands
**FTP commands for Linux command prompt**

bye           - Terminate the session
binary       - Set binary transfer type
delete       - Delete remote file
mdelete    - Delete multiple files
get            - receive a file
mget         - receive multiple files
put            - send a file
mput         - send multiple files
