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
