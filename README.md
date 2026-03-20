# EOS-Post-Install-Guide
EndeavourOS Post Install Guide

## Updating the system
* Proceed to update the system using:
```
yay
```

## zram
* Setup zram by installing `zram-generator`
```
sudo pacman -Syu zram-generator
```
* Creating a config file in `/etc/systemd/zram-generator.conf`
```
sudo nano /etc/systemd/zram-generator.conf
```
* Add the following:
```
[zram0]
zram-size = ram
compression-algorithm = zstd
```
* Reload daemons and start zram
```
sudo systemctl daemon-reload
sudo systemctl start /dev/zram0
```
* Reboot
```
sudo reboot
```
* Check with:
```
zramctl
```
* or
```
swapon --show
```

## zram optimizations

## Bluetooth
* Turn on bluetooth with:
```
sudo systemctl enable --now bluetooth
```

## Multimedia codecs
* Install multimedia codecs with:
```
sudo pacman -S gstreamer gst-plugins-good gst-plugins-bad gst-plugins-ugly vlc vlc-plugins-all
```

## Linux headers
* Install Linux headers with:
```
sudo pacman -S linux-headers
```

## Intel drivers
* Install Intel drivers with:
```
sudo pacman -S intel-ucode intel-media-driver ffmpeg libva-utils
```
* Use `vainfo`

## Nvidia drivers
* Install Nvidia drivers with:
```
yay -S nvidia-dkms nvidia-utils nvidia-settings
```
* Also, install `EnvyControl` to switch GPU usage with:
```
sudo pacman -S envycontrol
```
* Switch GPUs with:
```
sudo envycontrol -s hybrid # for hybrid setup
sudo envycontrol -s integrated # for integrated GPU
sudo envycontrol -S nvidia # for Nvidia GPU
```

## Zen kernel
* Install Linux Zen kernel for optimized performance with:
```
sudo pacman -S linux-zen linux-zen-headers
```
* Reboot to use the Zen kernel
```
sudo reboot
```

## Microsoft fonts
* Install Microsoft fonts package on EndeavourOS with:
```
yay -S ttf-ms-fonts
```

## Web browsers
* Install Google Chrome with:
```
yay -S google-chrome
```
* Install Brave Browser with:
```
yay -S brave-bin
```

## Gaming
* Install lib32 packages with:
```
yay -S vulkan-icd-loader lib32-vulkan-icd-loader
```
* Install lib32 Nvidia with:
```
yay -S lib32-nvidia-utils
```
* Install lib32 Vulkan Intel with:
```
yay -S vulkan-intel lib32-vulkan-intel
```
* Install Steam with:
```
sudo pacman -S steam
```
* Install Mangohud and Goveray with:
```
sudo pacman -S mangohud lib32-mangohud goverlay
```

## LibreOffice
* Install LibreOffice with:
```
sudo pacman -S libreoffice-fresh
```

## VSCodium
* Install VSCodium for software development with:
```
yay -S vscodium-bin
```

## End-to-end encrypted notes
* Install end-to-end encrypted notes in StandardNotes with:
```
yay -S standardnotes-bin
```
