## Linode django-server ubuntu setup
infó: https://www.youtube.com/watch?v=Sa_kQheCnds

 - apt-get update & apt-get upgrade
 - hostnamectl set-hostname django-server
 - nano /etc/hosts
> 139.162.164.57	django-server
---
 - adduser duser
 - adduser duser sudo
 - reconnect ssh as duser
---
 - sudo apt-get install ufw
 - sudo ufw default allow outgoing
 - sudo ufw default deny incoming
 - sudo ufw allow ssh
 - sudo ufw allow 8000
 - sudo ufw enable
 - sudo ufw status
 - --
