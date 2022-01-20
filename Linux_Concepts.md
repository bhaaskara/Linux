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
|__  /boot       - contains static files required to boot the system
|__  /dev        - contains device nodes that represent the devices attached to the system
|__  /etc         - System configuration files
|__  /home     - Users' home directories 
|__  /lib
|__  /media   - Automatically detected removable media is mounted in the `/media` directory.
|__  /mnt       - reserved for temporarily mounted file systems, such as NFS file system 
                        mounts.
|__  /opt        - reserved for software and add-on packages that are not part of the default 
                        installation.
|__  /srv        - contains site specific data served by RHEL system
|__  /tmp       - Temporary files. Often not preserved between system reboots   
|__  /usr        - (multi-)user utilities and applications
|__  /proc     - contains special files that either extract information from the kernel or send 
                       information to it
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