# Hyprland Dots
Here you will find the hyprland configuration I use on my laptop which is running Arch. This is just a fun little project for me to do on the side since I enjoy the idea that I can make this computer work and feel in exactly the way I like. I do not do any sort of coding professionally; configuring these files is just something I enjoy doing and learning about. 

With that said, since I am a novice, I did have some help from the Internet. I followed the Arch Wiki for the initial installation, then I tried a bunch of other people's dotfiles and tried to understand how they work. I made a list of necessary and quality of life programs, and following that, I reinstalled Arch with all the programs I had listed. From there I tried to edit config files by myself, but I did base some of my configs off some other dotfile templates that I found floating around. Most things are based on the default configuration files of the programs I am using; nothing is taken directly from someone else's configuration except the [swaylock](https://github.com/JaKooLit/Hyprland-v2.1/blob/main/config/hypr/swaylock/config) config. Even for that, however, I think I changed the time format. 

All in all, I'm very happy with the way my system has turned out, and I think that using git is a nice way to keep track of changes I make to my system, and it can even act as a backup in case I need to reinstall Arch on this machine or any other machine for any reason whatsoever. Feel free to use my config as is or as a base for your own config. Let me know if there are any ways it might be improved. 

### neofetch
![image](https://github.com/forkentiney/hyprland-dots/assets/136779764/655b1f00-10f7-46f8-a74d-60a6a89929fe)

### swaync
![image](https://github.com/forkentiney/hyprland-dots/assets/136779764/ea659259-0b94-44ee-9332-4049aa6caa6b)

### neovim
![image](https://github.com/forkentiney/hyprland-dots/assets/136779764/a64980d3-9611-4156-9c01-7b969ed7bdb0)

## Applications on my system
- blueman
- bluez-utils
- brightnessctl
- catppuccin-gtk-theme-frappe
- ffmpegthumbnailer
- git
- grim
- hyprland-nvidia
- hyprpaper
- kitty
- networkmanager
- network-manager-applet
- networkmanager-openvpn
- nmconnection-editor
- pamixer
- polkit-kde-agent
- rofi
- sddm-git
- sddm-catppuccin-git
- slurp
- swaylock-effects-git
- swaync
- thunar
- thunar-volman
- ttf-ms-win10-auto
- tumbler
- waybar
- wl-clipboard
- zsh

## Steps I took to get Hyprland working with Nvidia
 - Run archinstall with linux kernal
 - Install ```zsh```
 - run ```chsh -s $(which zsh)```
 - Logout
 - Login and type 110213041u2u3s4s5u00 to quickly configure zsh
 - Install ```linux-kernals``` package
 - Install ```nvidia-dkms``` package
 - add ```nvidia_drm.modeset=1``` to the end of /boot/loader/entries/arch.conf
 - in /etc/mkinitcpio.conf add ```nvidia nvidia_modeset nvidia_uvm nvidia_drm``` to MODULES array
 - run ```mkinitcpio --config /etc/mkinitcpio.conf --generate /boot/initramfs-custom.img```
 - add ```options nvidia-drm modeset=1``` to /etc/modprobe.d/nvidia.conf
 - Install yay:
   ```
   sudo pacman --needed base-devel git
   git clone https://aur.archlinux.org/yay.git
   cd yay
   makepkg -si
   ```
 - Install ```hyprland-nvidia``` (aur)
 - Install ```qt5-wayland qtct libva```
 - Install ```nvidia-vaapi-driver-git``` (aur)
 - Wrap the launcher by adding the following to /usr/local/bin/hyprland-wrap
   ```
   #!/bin/sh

   cd ~

   export _JAVA_AWT_WM_NONREPARENTING=1
   export XCURSOR_SIZE=24

   exec Hyprland
   ```
- Make hyprland-wrap executable 
- Reboot
- Run ```hyprland-wrap```
- Add env variables to ~/.config/hypr/hyprland.conf (done already as part of this repo)
