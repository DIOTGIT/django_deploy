# VM ubuntu server set IP

### infó:  [https://www.wpdiaries.com/virtualbox-for-web-development/](https://www.wpdiaries.com/virtualbox-for-web-development/)  
  
VM hálózat: 1. bridge, többi letiltva

parancsok:

-   cd /etc/netplan/
-   sudo nano 00-installer-config.yaml

>     network:  
> 	    ethernets:  
> 		    enp0s3:  
> 			    dhcp4: false  
> 			    addresses: [192.168.1.98/24]  
> 			    gateway4: 192.168.1.1  
> 			    nameservers:  
> 				    addresses: [8.8.8.8, 8.8.8.4]  
>     version: 2

-   sudo netplan apply
