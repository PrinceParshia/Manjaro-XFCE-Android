## MANJARO-XFCE
![Screenshot_2024-11-21_08-03-21](https://github.com/user-attachments/assets/762326c2-71d5-4dd9-9a12-a056a02fcd66)


---
Open Termux and execute these commands.
```
pkg update && pkg upgrade
pkg install x11-repo
pkg install proot-distro termux-x11 wget pulseaudio
```
Now install Manjaro using Proot-Distro.
```
proot-distro install manjaro
proot-distro login manjaro
```
After installation, You should see this [root@localhost ~]#. If it is, execute the following commands.
```
pacman -Syu
```
```
nano /etc/pacman.conf
```
You should see a text editor page, scroll down using down arrow and try to find a line called "SigLevel" and replace the value with Never. Heres an example how it will look like.
```
SigLevel = Never
```
After this to exit the page press CTRL 1 time then press these keys on your keyboard X then Y then ENTER.

Now execute the following commands in the Manjaro Shell.
```
pacman -S sudo git xfce4 xfce4-goodies tumbler engrampa
```
You have to download a browser to access the internet. FireFox is recommended.
```
pacman -S chromium
```
```
pacman -S firefox
```
Then create a user to acces the Manjaro Desktop.
```
useradd -m <username>
```
Give the sudo permission to your user.
```
nano /etc/sudoers
```
Paste this under root ALL=(ALL:ALL) ALL.
```
<username> ALL=(ALL:ALL) ALL
```
CTRL - X - Y - ENTER

Now set a password to access your new user.
```
passwd <username>
``` 
Manjaro Default Xfce theme doesn't comes with it. We have to download it manually. If you dont want the Manjaro default theme you can skip it.
```
su - <username>
```
Then execute these commands.
```
git clone https://gitlab.manjaro.org/profiles-and-settings/manjaro-xfce-settings.git
```
```
rm -r ~/.config/xfce4
```
```
rm -r ~/.config/Thunar
```
```
mv manjaro-xfce-settings/skel/.config/xfce4 ~/.config
```
```
mv manjaro-xfce-settings/skel/.config/Thunar ~/.config
```
Now install the startup command using wget (Termux-X11 app is required). In Termux Shell (If your in manjaro shell execute ```exit```).
```
wget https://raw.githubusercontent.com/PrinceParshia/manjaro-xfce-android/refs/heads/main/manjaro-xfce.sh
```
```
nano manjaro-xfce.sh
```
Scroll and change ```<username>``` (line 20) to the user you created in manjaro shell.
CTRL - X - Y - ENTER
```
chmod +x manjaro-xfce.sh
```
Now run downloaded startup file to start the desktop. You can use it later to run the desktop again.
```
./manjaro-xfce.sh
```
Download the theme files called Matcha-dark-sea and Papirus-teal-folders.
Then execute this commands in Termux-X11 opened manjaro terminal.
```
cd Downloads
```
Adjust the file name with your downloaded files.
```
tar -xf Matcha-dark-sea.tar.xz
```
```
tar -xf Papirus*.tar.xz
```
```
mv Matcha-dark-sea /usr/share/themes
```
```
mv Papirus* /usr/share/icons
```
```
mv Papirus-dark /usr/share/icons
```

Now you can start your desktop using the startup file and you can close it by terminating termux using the exit button on the notification bar. 
Note: Before exiting check if ur all info in desktop is saved otherwise unsaved changes may gone.