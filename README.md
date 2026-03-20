# EOS-Post-Install-Guide
Standard EndeavourOS Post Installation Guide (2026)

It is encouraged to visit the EndeavourOS Wiki at https://discovery.endeavouros.com/

## Updating the system
* Proceed to update the system using:
```
yay
```

### Recommended ways to update
```
yay
```
* or
```
sudo pacman -Syu
```
* Avoid `sudo pacman -Sy` as it updates your local package database (-y) but does not update installed packages (-u), leading to dependencies mismatches, broken applications, and potentially a broken system

### Recommended ways to install
* If first installation of the session, before any update:
```
sudo pacman -Syu [package-name]
```
* If system is already updated:
```
sudo pacman -S [package-name]
```

## zram
* Setup zram by installing `zram-generator`
```
sudo pacman -Syu zram-generator
```
* Create a config file in `/etc/systemd/zram-generator.conf`
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

## zram optimizations (optional)
* Edit `/etc/sysctl.d/99-zram.conf`
```
sudo nano /etc/sysctl.d/99-zram.conf
```
* Add the following:
```
vm.swappiness = 180
vm.watermark_boost_factor = 0
vm.watermark_scale_factor = 125
vm.page-cluster = 0
```

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
* Use `vainfo` to check multimedia info

## Nvidia drivers
* For **older** GPUs (Pascal, etc) use the following, for modern GPUs since RTX omit and proceed to the next
```
yay -s nvidia-580xx-dkms nvidia-580xx-utils nvidia-580xx-settings
```
* Install Nvidia drivers for **modern** GPUs with:
```
yay -S nvidia-dkms nvidia-utils nvidia-settings
```
* Reboot after the build:
```
sudo reboot
```
* Check with:
```
nvidia-smi
```

## EnvyControl for GPU
* Also, install `EnvyControl` to switch GPU usage with:
```
sudo pacman -S envycontrol
```
* Switch between GPUs with:
```
sudo envycontrol -s hybrid ## for hybrid setup with PRIME OFFLOAD
sudo envycontrol -s integrated ## for integrated GPU only
sudo envycontrol -S nvidia ## for Nvidia GPU only
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

## LibreOffice
* Install LibreOffice with `latest features` with:
```
sudo pacman -S libreoffice-fresh
```
* Install LibreOffice `stable` with:
```
sudo pacman -S libreoffice-still
```

## StandardNotes (end-to-end encrypted notes)
* Install end-to-end encrypted notes StandardNotes with:
```
yay -S standardnotes-bin
```

## VSCodium
* Install VSCodium for software development with:
```
yay -S vscodium-bin
```

## Zen kernel
* Recommended for gaming setup
* Install Linux Zen kernel for optimized performance with:
```
sudo pacman -S linux-zen linux-zen-headers
```
* Reboot to use the Zen kernel
```
sudo reboot
```
* The `linux-zen` kernel will be set as default, to change to previous `linux-kernel` use the **Advanced settings** at Boot

## Gaming setup
* Recommended: `linux-zen` kernel
* Install lib32 packages with:
```
yay -S vulkan-icd-loader lib32-vulkan-icd-loader
```
* Install lib32 Vulkan with:
```
yay -S vulkan-intel lib32-vulkan-intel
```
* Install lib32 Nvidia for **older** GPU (Pascal, etc) with:
```
yay -S lib32-nvidia-580xx-utils
```
* Install lib32 Nvidia for **modern** GPU since RTX with:
```
yay -S lib32-nvidia-utils
```

## Steam
* Install Steam with:
```
sudo pacman -S steam
```

## Mangohud
* Mangohud and goverlay help you set GPU preferences like FPS cap
* Install Mangohud and Goveray with:
```
sudo pacman -S mangohud lib32-mangohud goverlay
```
* Set GPU settings on `goverlay`
* Activate as `environment variable` with:
```
mangohud
```
