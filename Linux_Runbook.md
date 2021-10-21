## Disable swap memory
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
