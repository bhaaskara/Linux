# Important files
## System
## Users and groups
Contents/Details | Ubuntu | Redhat/CentOS
---------------- | ---- | ----
User details | `/etc/passwd`
Encrypted passwords | `/etc/shadow`
Groups info | `/etc/group`
Config for Sudo | `/etc/sudoers`
log files | `/var/log/syslog` <br/> `/var/log/auth.log`| `var/log/messages` <br/> `/var/log/secure`
Switch to root without paasword | `sudo su`




# System commands
Usage | Command
:------ | :------
  OS Version | `cat /etc/os-release`#For Ubuntu</br>`cat /etc/redhat-release`#For Redhat</br>`cat /etc/centos-release`#For Centos
  Kernel Version | `uname -a` </br> `hostnamectl status`
  Reboot | `sudo reboot` #Server will be rebooted immediatly </br>`sudo shutdown -r` #Rebooted after a min </br>`sudo shutdown -r +10` #Reboot after 10 min</br>`sudo shutdown -r 16:15` #Scheduled reboot</br>`sudo shutdown -c`#Cancel the schedule reboot
  Port status | `netstat -anp \|grep <PortNum>`
  Memory usage | `free -m`
  Shell   | `echo $SHELL`

## Install a Package/Software
### CentOS / Redhat
Usage | Command
------ | ------
Search for a package | `yum list <pkg>`
Pachage info | `yum info <pkg>`
Install a package | `yum install <pkg> -y`
Install a package from rpm file | `yum localinstall <rpmfile> -y`

Ref: https://access.redhat.com/sites/default/files/attachments/rh_yum_cheatsheet_1214_jcs_print-1.pdf

### Ubuntu
Usage | Command
------ | ------
List installed packages | `apt list --installed`

# Users
Usage | Command
----- | -------
current user | `whoami`
List of all logged in users | `who`
Add an user | `sudo useradd <username>`
Set password for an user | `sudo passwd <username>`
Add a user without login access | `sudo useradd <uname> -s /sbin/nologin`
Switch user<br />Swich to root user | `su <username>` <br /> `su` or `su bash` 
Delete an user | `sudo userdel <username>`
Modify an User |`sudo usermod`
Change an user account password expiration | `sudo chage`

`It is also important to note that, as opposed to other Linux flavors, the user that is created when Ubuntu is first installed has superuser privileges out-of-the-box.`



# Groups
Usage | Command
----- | -------
Add a group | `sudo groupadd <groupname>`
Add an user to group | `sudo useradd -g <Groupname> <username>`
list the UID,Groups for current user | `id`  
list the UID,Groups for a user | `id <user name>`
Delete a group | `sudo groupdel <groupname>`

# grep  (Search)
Usage | Command
----- | -------
Search in a file | `grep <pattern> <filename>`
Case insensitive | `grep -i <pattern> <filename>`
Search results with line numbers | `grep -in <pattern> <filename>`
Search that doesnt match | `grep -iv <pattern> <filename>`
Search in a dir | `grep -ir <pattern> <dir>`

# Sorting
Usage | Command
----- | -------
Case insensitive sorting | `sort -f`
Reverse sort | `sort -r`
Numeric sorting | `sort -n`

# Permissions
Usage | Command
----- | -------
Change the owner | `chown <user> <file>`
Change the permission | `chmod 777 <file>`
Add read permission | `chmod +r <file>`
Remove read permission | `chmod -r <file>`

# Files
Usage | Command
----- | -------
List of opened files | `lsof`
Files opened by a user | `lsof -u <username>`

# Zip / Unzip
Usage | Command
----- | -------
Zip a file | `tar -cvf <tar-filename> <folder>`
Unzip a tar file | `tar -xvf <tar-file>`

# Selected column o/p
Usage | Command
----- | -------
only one column | `cut -c1 <file>`
o/p first two columns | `cut -c1-2 <file>`

# SED (cli text editor)
Usage | Command
----- | -------
Replace in a file | `sed 's/<string>/<new-string>' <file>`

# o/p only unique/Remove duplicates
Usage | Command
----- | -------
o/p only unique/Remove duplicates | `unique <filename>`

# Monitor a command o/p
Usage | Command
----- | -------
monitor a command <br/> o/p refreshes every 2 secs| `watch <command>`

# Base64 encoding/decoding
base64 encoding: `echo -n 'string' | base64`
base64 decoding: `echo "encodedstring" | base64 --decode`
# Networking
Usage | Command
:-----| :-------
IP address | `ifconfig -a`

# Edit text files
## Vi Editor
