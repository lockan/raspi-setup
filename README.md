# RasPi Setup Notes 
 
## Initial Setup
1. Download / install official OS imager from RaspberryPi.org
1. Use imager to format SD card
1. Use imager to install desired version of OS (prefer 64-bit lite version)
1. Remove and re-insert sd card 
1. Add wpa_supplicant.conf and ssh to drive root
    1. Add ssid and password
1. Eject storage device
1. Insert SD card into RasPi and boot
1. ssh pi@{ip-address} -> login with default password
1. sudo apt update && sudo apt upgrade
1. sudo apt-get install vim
1. sudo vim /etc/dhcpcd.conf --> 
    1. edit static ip config for wlan0 and save. 
1. run raspi-config -> set various options as desired 
    1. extend partition
    1. change password
    1. set hostname
    1. set locale and timezone
    1. other settings as required. 
1. sudo shutdown -r 0 
1. ssh pi@{static-ip-address} -> login with new password

## Rancher K3S Kubernetes - Single-Node Installation
1. sudo apt update
1. sudo apt  upgrade
1. /boot/cmdline.txt -> add cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1 into the end of the file
1. sudo vim /boot/cmdline.txt
1. Reboot pi and login
1. curl -sfL https://get.k3s.io | sh -s - --write-kubeconfig-mode 644

 
 