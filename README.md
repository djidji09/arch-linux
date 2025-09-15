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
once the wifi is turned on we use the archinstall script to install linux
```terminal 
archinstall
```
follow the install and dont forget to get "wget" as additional packages because we are gonna use it to get omarchy

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

to list the installed wallpapers
```terminal 
sudo plymouth-set-default-theme -l
```
```terminal 
yay -S plymouth-theme-Circuit-git plymouth-theme-Colorful-Loop-git plymouth-theme-Cross-HUD-git plymouth-theme-Cuts-git plymouth-theme-Dark-Planet-git plymouth-theme-Hexagon-Dots-git plymouth-theme-IBM-git plymouth-theme-Loader-git plymouth-theme-Loader-2-git plymouth-theme-Loader-Alt-git plymouth-theme-lone-git plymouth-theme-Owl-git 
```
now you can set a theme 
```terminal
sudo plymouth-set-default-theme -R NAME
```
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

## fix discord update 
go to : 
```terminal 
/opt/discord/resources
```
and edit the version to the current version

## fix the boot time 
### Mask TPM2 target and daemon so systemd won’t wait on it
```
sudo systemctl mask tpm2.target
sudo systemctl mask systemd-tpm2d.service
```

### Re-enable TPM2 (if you ever need it again)
``` terminal
sudo systemctl unmask tpm2.target
sudo systemctl unmask systemd-tpm2d.service
```