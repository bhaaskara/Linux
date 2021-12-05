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
