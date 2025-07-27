# arch-linux
## arch-linux's setup

´´´terminal 
iwctl
´´´

## omarchy's setup

´´´terminal 
wget -qO- https://omarchy.org/install | bash
´´´
## configuration 
### first copy all the dot files into there correct path
### update & upgrade the system
´´´terminal 
sudo pacman -Syu
´´´
### download necesary stuff 
´´´terminal 
 yay -s google-chrome nano visual-studio-code-bin

´´´
### fix chrome's keyboard problem


´´´terminal 
setxkbmap fr
´´´
### delete uncesary stuff 

´´´terminal 
 sudo pacman -Rns spotify zoom neovim typora
´´´