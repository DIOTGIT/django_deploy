## Ubuntu setup for Django development
infó: https://www.youtube.com/watch?v=437o1UUQUhY

**Linux update**
 - guest lemez futtatása
 - megegyező verziójú excentsion pack letöltése és hozzáadása : https://www.youtube.com/watch?v=efSIZA15lWM 
 - sudo apt-get update 
 - sudo apt-get upgrade -y
 - (izé lemez futtatása)
 - sudo shutdown now
 --- 
 **Chrome install**
 - wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb --no-check-certificate
 - sudo apt install ./google-chrome-stable_current_amd64.deb
 - rm google-chrome-stable_current_amd64.deb 
- chrome hiba javítása: https://superuser.com/questions/1083766/how-do-i-deal-with-neterr-cert-authority-invalid-in-chrome
---
**VSCode install**
- sudo apt install software-properties-common apt-transport-https wget
- wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
- sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
- sudo apt install code
- sudo apt autoremove
---
**install git, python**
- sudo apt-get install git
- sudo apt install -y python3-pip python3-venv
