# arch-linux
## arch-linux's setup
if the the wifi interface is software blocked you can do this 
```  
rfkill list
rfkill unblock all
```
```  
iwctl
station wlan0 scan
station wlan0 get-networks
station wlan0 connect YOUR_WIFI_NAME
```
once the wifi is turned on we use the archinstall script to install linux
```  
archinstall
```
follow the install and dont forget to get "wget" as additional packages because we are gonna use it to get omarchy

## omarchy's setup

```  
wget -qO- https://omarchy.org/install | bash
```
## configuration 
### first copy all the dot files into there correct path
### update & upgrade the system
```  
sudo pacman -Syu
```
### download necesary stuff 
```  
 yay -s google-chrome nano visual-studio-code-binR discord vlc
```
### fix chrome's keyboard problem


```  
setxkbmap fr
```
### delete uncesary stuff 

```  
 sudo pacman -Rns spotify zoom neovim typora
```

```  
cd ~/.local/share/applications
rm -rf HEY.desktop GitHub.desktop Basecamp.desktop
```
## change the boot screen with (plymouth)

visit [this website](https://github.com/adi1090x/plymouth-themes)

to list the installed wallpapers
```  
sudo plymouth-set-default-theme -l
```
```  
yay -S plymouth-theme-Circuit-git plymouth-theme-Colorful-Loop-git plymouth-theme-Cross-HUD-git plymouth-theme-Cuts-git plymouth-theme-Dark-Planet-git plymouth-theme-Hexagon-Dots-git plymouth-theme-IBM-git plymouth-theme-Loader-git plymouth-theme-Loader-2-git plymouth-theme-Loader-Alt-git plymouth-theme-lone-git plymouth-theme-Owl-git 
```
now you can set a theme 
``` 
sudo plymouth-set-default-theme -R NAME
```
## mount the shared disk 

first we gotta create a folder to mount the disk on 
```  
sudo mkdir mnt/shared
```
then we mount the selected drive shown with the command "lsblk"
```  
sudo mount /dev/sda9 /mnt/shared
```
then we create a shortcut of the drive
```  
ln -s /mnt/shared/ ~/djidji/shared
```

## fix discord update 
go to : 
```  
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
```
sudo systemctl unmask tpm2.target
sudo systemctl unmask systemd-tpm2d.service
```

## install a login manager 
first we disable the auto login (seamless-login.service)
```
sudo systemctl disable --now omarchy-seamless-login.service
```
if you wanna re-enable it again
```
sudo systemctl enable --now omarchy-seamless-login.service
```
### installing sddm 
```
sudo pacman -S sddm
sudo systemctl enable --now sddm.service
```
### styling sddm 
go this [github repo](https://github.com/Keyitdev/sddm-astronaut-theme)

then use the automatic script to install the style you want 
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/keyitdev/sddm-astronaut-theme/master/setup.sh)"
```
### selecting a theme 
edit this line "ConfigFile=Themes/astronaut.conf" in : 
```
nano /usr/share/sddm/themes/sddm-astronaut-theme/metadata.desktop
```
all the themes are in :
```
cd /usr/share/sddm/themes/sddm-astronaut-theme/Themes
```

#neovim 
i am edditing this in neovim :
##config files 

