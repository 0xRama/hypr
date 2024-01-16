# HyprV4
Welcome to the fourth version of the Hyprland installation script. This script is designed to streamline the setup of Hyprland on a brand-new, clean installation of Arch Linux, specifically on physical hardware.

For those who prefer a more hands-on approach, you have the option to manually fetch the dot config files and install the necessary packages. Instructions are provided below for your convenience.

If your system requires Nvidia support, make sure to execute the following steps prior to beginning the installation process:
```
yay -S linux-headers nvidia-dkms qt5-wayland qt5ct libva libva-nvidia-driver-git

```
/etc/mkinitcpio.conf
```
MODULES=(nvidia nvidia_modeset nvidia_uvm nvidia_drm)
```
generate a new initramfs image
```
sudo mkinitcpio --config /etc/mkinitcpio.conf --generate /boot/initramfs-custom.img
```
Create NVIDIA Configuration
```
echo "options nvidia-drm modeset=1" | sudo tee /etc/modprobe.d/nvidia.conf
```
verify
```
cat /etc/modprobe.d/nvidia.conf
```
shoud return: 
```
options nvidia-drm modeset=1
```
now reboot
```
reboot
```

Now install the below for Hyprland

```
yay -S hyprland kitty jq mako waybar-hyprland swww swaylock-effects \
wofi wlogout xdg-desktop-portal-hyprland swappy grim slurp thunar \
polkit-gnome python-requests pamixer pavucontrol brightnessctl bluez \
bluez-utils blueman network-manager-applet gvfs thunar-archive-plugin \
file-roller btop pacman-contrib starship ttf-jetbrains-mono-nerd \
noto-fonts-emoji lxappearance xfce4-settings sddm-git sddm-sugar-candy-git 
```

Alternatively, for a hassle-free installation, utilize the included "set-hypr" script. This will efficiently handle the entire setup process for you.