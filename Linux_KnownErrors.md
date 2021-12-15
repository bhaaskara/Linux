# Linux Known Errors
## No IP address on a Centos 7.7 VM
1. open nmtui 
   ```
   sudo nmtui
   ```
   And you'll get an interface like below:  
   ![img](https://github.com/bhaaskara/Linux/blob/fa502c2aaa5dbd5671ac702c033ec6bb10bc411e/images/centosnmtui.JPG)
   
   activate the interface.  
   Navigate by using `TAB` and select/Deselect by using `SPACE`  
2. Restart network service
   ```
   sudo systemctl restart network
   ```

## Delta RPMs disabled because applydeltarpm not installed  
**ERROR: Delta RPMs disabled because /usr/bin/applydeltarpm not installed.**  
Delta rpms (DRMS) created to save bandwidth and speed up download patches and rpm packages from the Internet. With DRMS, you download only minor changes instead of grabbing full packages. In other words, only changes (updates) between the installed and new packages are downloads.  
`Solution`
```sh
sudo yum install deltarpm
sudo yum update
```

## IPtables
**ERROR: sysctl: cannot stat /proc/sys/net/bridge/bridge-nf-call-iptables: No such file or directory**  
`Solution`
```sh
sudo modprobe br_netfilter
sudo sysctl -p
```
