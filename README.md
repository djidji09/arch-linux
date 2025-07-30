# arch-linux
## arch-linux's setup
if the the wifi interface is software blocked you can do this 
```terminal 
rfkill list
rfkill unblock all
```
```terminal 
iwctl
station wlan0 scan
station wlan0 get-networks
station wlan0 connect YOUR_WIFI_NAME
```

## omarchy's setup

```terminal 
wget -qO- https://omarchy.org/install | bash
```
## configuration 
### first copy all the dot files into there correct path
### update & upgrade the system
```terminal 
sudo pacman -Syu
```
### download necesary stuff 
```terminal 
 yay -s google-chrome nano visual-studio-code-binR discord vlc
```
### fix chrome's keyboard problem


```terminal 
setxkbmap fr
```
### delete uncesary stuff 

```terminal 
 sudo pacman -Rns spotify zoom neovim typora
```

```terminal 
cd ~/.local/share/applications
rm -rf HEY.desktop GitHub.desktop Basecamp.desktop
```
## change the boot screen with (plymouth)

visit [this website](https://github.com/adi1090x/plymouth-themes)

## mount the shared disk 

first we gotta create a folder to mount the disk on 
```terminal 
sudo mkdir mnt/shared
```
then we mount the selected drive shown with the command "lsblk"
```terminal 
sudo mount /dev/sda9 /mnt/shared
```
then we create a shortcut of the drive
```terminal 
ln -s /mnt/shared/ ~/djidji/shared
```