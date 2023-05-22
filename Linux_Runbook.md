# Disable swap memory
## Ubuntu 20.04
Check swap memory status
```sh
worker1@worker1:~$ swapon -s
Filename                                Type            Size    Used    Priority
/swap.img                               file            1784828 0       -2
```
Check swap memory usage
```sh
worker1@worker1:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:            981         143         549           1         288         690
Swap:          1742           0        1742
```
Disable swap memory  
`$ sudo swapoff -a`  
Check the status  
```sh
worker1@worker1:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:            981         138         548           1         294         695
Swap:             0           0           0
```
Edit `/etc/fstab` to perminantly disable the swap memory off across reboots
```sh
vi /etc/fstab
#/swap.img      none    swap    sw      0       0
> Insert # infront of the line with swap
> Save and exit
```
# Change the hostname
Modify the `/etc/hostname` file  
```sh
vi /etc/hostname
<hostname>
```
restart the server `init 6`  

**To change the hostname temporarily** 
`hostname <hostname>`
logoff and login

# Disable SELINUX on REDHAT/CentOS
Check the current SELinux status
```
sudo sestatus
```
Disable SELinux temporarily
```
sudo setenforce 0
```
Check it with `getenforce`  

Disable SELINUX permanently
```sh
vi /etc/selinux/config
#set the
SELINUX=disabled
```
Reboot the server `init 6`  

# Update ntp time
`sudo apt-get install ntpdate; sudo ntpdate ntp.ubuntu.com`

# Disable firewall
## on REDHAT/CentOS
Check the firewall status
```
sudo firewall-cmd --state
```
Stop the firewall
```
sudo systemctl stop firewalld
```
Disable it permanantly
```
sudo systemctl disable firewalld
```
Mask the FirewallD service which will prevent the firewall being started by other services
```
sudo systemctl mask --now firewalld
```

# Users
## Grant sudo access without password
### Ubuntu 20.04
`usermod -aG sudo <username>` # Add user to sudo group  
Another way is, Adding user to sudoers file
```sh
visudo
<username>  ALL=(ALL) NOPASSWD:ALL
#Save and exit
```

# Encoding and decoding
## Decode the base64 encoded data
on windows
First run the below command to make the file, linucx compatible.
convert the line endings from windows to Linux
```
((Get-Content .\terraform.tfstate) -join "`n") + "`n" | Set-Content -NoNewline .\terraform.tfstate
```
and on gitbash run the below command
```
cat decode.txt |base64 --decode
```