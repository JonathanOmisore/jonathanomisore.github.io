---
title: How to install GRUB on an external hard drive
author: Jonathan Omisore
layout: post
---
When I attempted to install Arco Linux on my external hard drive, I faced a glitch in which the Calameres installer decided to install GRUB on my computer's internal hard drive rather than my external hard drive. Here  is how I solved this problem.

First boot into a live Linux USB with the external hard drive connected to your computer.

List all partitions to identify the EFI partition and the Linux  partition
```
lsblk
```
Suppose /dev/sdb1 is the Linux partition and /dev/sdb2 is the EFI partition. Mount the Linux partition to /mnt and the EFI partition to /mnt/boot/efi
```
sudo mount /dev/sdb1 /mnt
sudo mount /dev/sdb2 /mnt/boot/efi
```
Mount special locations
```
sudo mount --rbind /proc /mnt/proc
sudo mount --rbind /dev /mnt/dev
sudo mount --rbind /sys /mnt/sys
```
Chroot into the mounted path
```
sudo chroot /mnt
```
Install GRUB to the external hard drive
```
sudo grub-install /dev/sdb
```
Update GRUB
```
sudo update-grub
```
But you aren't finished yet. You need to make sure your computer knows to boot into your EFI partition.
Find the UUID of your EFI partition
```
blkid
```
Edit fstab
```
cp /etc/fstab /etc/fstab.bak  
sudo nano /etc/fstab  
````
Add the  following line, setting the value of UUID equal to the UUID you obtained from the ```blkid``` command.
```
UUID=   /boot/efi   vfat   umask=0077   0   1  
```
Now reboot into your external hard drive.
