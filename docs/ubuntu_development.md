## Ubuntu setup for Django development
infó: https://www.youtube.com/watch?v=437o1UUQUhY

**Linux update**
 - guest lemez futtatása
 - megegyező verziójú excentsion pack letöltése és hozzáadása : https://www.youtube.com/watch?v=efSIZA15lWM 
 - sudo apt-get update 
 - sudo apt-get upgrade -y
 - (izé lemez futtatása)
- sudo apt autoremove
- sudo shutdown now

 --- 
 **Add goolge certificates **
 https://superuser.com/questions/437330/how-do-you-add-a-certificate-authority-ca-to-ubuntu
 with firefox save the cert files
 - sudo cp SSL-SG1-GDEFR11.crt /usr/local/share/ca-certificates
 - sudo cp Cloud-Services-Root-CA.crt /usr/local/share/ca-certificates
 - sudo update-ca-certificates


 --- 
 **Chrome install**
 - wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb --no-check-certificate
 - sudo apt install ./google-chrome-stable_current_amd64.deb
 - rm google-chrome-stable_current_amd64.deb 
- chrome certificate hiba javítása: https://superuser.com/questions/1083766/how-do-i-deal-with-neterr-cert-authority-invalid-in-chrome
---
**VSCode install**
- wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
- sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
- sudo apt install code
---
**install git, python**
- sudo apt install -y git python3-pip python3-venv
- git config --global user.name "DIOTGIT"
- git config --global user.email "diothomeautomation@gmail.com"
---
**install Bulidozer for kivy**
https://buildozer.readthedocs.io/en/latest/installation.html
- sudo apt install openjdk-8-jdk
- pip install -y kivy buildozer cython
- sudo apt update
- sudo apt install -y git zip unzip openjdk-8-jdk python3-pip autoconf libtool pkg-config zlib1g-dev libncurses5-dev libncursesw5-dev libtinfo5 cmake libffi-dev libssl-dev
- pip3 install --upgrade Cython==0.29.19 virtualenv
- export PATH=$PATH:~/.local/bin/

ssl
openssl x509 -outform der -in google-com.pem -out google-com.crt
sudo apt install nautilus-admin # hogy a fájl szerkesztőből menjen az admin

wget https://curl.se/ca/cacert.pem --no-check-certificate

