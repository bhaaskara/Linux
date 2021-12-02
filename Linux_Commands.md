# Important files
Contents/Details | File
---------------- | ----
User details | `/etc/passwd`


Usage | Command
------ | ------
  OS Version | `cat /etc/os-release`#For Ubuntu</br>`cat /etc/redhat-release`#For Redhat
  Reboot | `sudo reboot` #Server will be rebooted immediatly </br>`sudo shutdown -r` #Rebooted after a min </br>`sudo shutdown -r +10` #Reboot after 10 min</br>`sudo shutdown -r 16:15` #Scheduled reboot</br>`sudo shutdown -c`#Cancel the schedule reboot
  Port status | `netstat -anp \|grep <PortNum>`
  
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

# Groups
Usage | Command
----- | -------
Add a group | `sudo groupadd <groupname>`
Add an user to group | `sudo useradd -g <Groupname> <username>`
Delete a group | `sudo groupdel <groupname>`

# grep  (Search)
Usage | Command
----- | -------
Search in a file | `grep <pattern> <filename>`
Case insensitive | `grep -i <pattern> <filename>`
Search results with line numbers | `grep -in <pattern> <filename>`
Search that doesnt match | `grep -iv <pattern> <filename>`
