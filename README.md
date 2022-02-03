# RasPi Setup Notes 
 
## Initial Setup
1. Download / install official OS imager from RaspberryPi.org
1. Use imager to format SD card
1. Use imager to install desired version of OS (prefer 64-bit lite version)
1. Remove and re-insert sd card to re-mount the boot drive.
1. Add `wpa_supplicant.conf` and `ssh` (empty file) to drive root
    1. Add ssid and password to `wpa_supplicant.conf`
1. Eject storage device
1. Insert SD card into RasPi and boot
1. `ssh pi@{ip-address}` -> login with default password
1. `sudo apt update && sudo apt upgrade`
1. `sudo apt-get install vim`
1. `sudo vim /etc/dhcpcd.conf` 
    1. edit static ip config for wlan0 and save. 
1. run `raspi-config` -> set various options as desired 
    1. extend partition
    1. change password
    1. set hostname
    1. set locale and timezone
    1. other settings as required. 
1. `sudo shutdown -r 0` to reboot 
1. `ssh pi@{static-ip-address}` -> login with new password

## Rancher K3S Kubernetes - Single-Node Installation
1. `sudo vim /boot/cmdline.txt`
    1. add `cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1` to end of file/line
1. `sudo shutdown -r 0` to reboot
1. `curl -sfL https://get.k3s.io | sh -s - --write-kubeconfig-mode 644` to install k3s
1. `kubectl get nodes` to verify it's running.

## Configure Kubectl for Remote Access
1. Install required version of kubectl from https://kubernetes.io/docs/tasks/tools/
1. ssh into raspi
1. `cat /etc/rancher/k3s/k3s.yaml`
1. Copy contents into new file
1. Save file as `${HOME}/.kube/config` on remote machine
1. Edit the server address and context name as needed. 
1. `kubectl config get-contexts` to confirm context is present/correct.