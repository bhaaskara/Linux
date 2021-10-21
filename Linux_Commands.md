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
current user | `who am i`
List of all logged in users | `who`
Add a user | `sudo useradd <uname> -s /sbin/nologin`#Add a user without login access
