---
title : 'GRUB Bootloader'
date : 2024-03-10T19:17:15+01:00
tags:
    - Linux
    - Article
draft : false
---

## First of all, what is GRUB?
GRUB is a boot loader, which lets you boot up your system. The abbreviation stands for GNU GRand Unified Bootloader, and is a boot loader package from the GNU Project. GRUB is the primary bootloader for many Linux distributions, allowing users to choose from multiple operating systems or different versions of the same operating system at boot time. It's designed to be highly configurable and supports a wide range of operating systems, not just Linux.

## Why make this guide?
The reason I made this simple guide is so you know what to do when you get to [Arch Linux installation guide, chapter 3.8](https://wiki.archlinux.org/title/Installation_guide).

## GRUB features include:
- The ability to boot multiple operating systems, including Linux, Windows, and macOS.
- Support for reading data from various file systems, allowing it to load boot files from these file systems directly.
- A flexible and powerful command-line interface that can be used to troubleshoot boot issues.
- The capability to load operating systems from a network, which is particularly useful in managed IT environments.
- A customizable menu interface that can display graphics and themes, allowing for a visually appealing boot menu.

GRUB has evolved over time, with GRUB 2 being the successor to the original GRUB (referred to as GRUB Legacy). GRUB 2 offers improved modularity, portability, and features compared to its predecessor.

## Installing GRUB EFI in Arch Linux
First off, we install some packages:
```
sudo pacman -S vim networkmanager grub efibootmgr dosfstools os-prober mtools
```

(Networkmanager is optional, but highly recommended)

## EnableNetworkManager
```
systemctl enable NetworkManager
```
## Mount EFI-partition
```
mount --mkdir /dev/drive /boot/EFI
```
## Install GRUB
```
grub-install --target=x86_64-efi --bootloader-id=grub_uefi --efi-directory=/boot/EFI --no-nvram --removable --recheck
```
## Make grub config file
```
grub-mkconfig -o /boot/grub/grub.cfg
```
## Reboot
- Exit the chroot environment by typing `exit` or pressing `Ctrl+d`.
- Optionally manually unmount all the partitions with `umount -R /mnt`: this allows noticing any "busy" partitions, and finding the cause
- Finally, restart the machine by typing `reboot`: any partitions still mounted will be automatically unmounted by *systemd*.
- Remember to remove the installation medium and then login into the new system with the root account
