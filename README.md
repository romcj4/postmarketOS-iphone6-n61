# postmarketOS-iphone6-n61
## Linux Distro on Iphone 6 (PostmarketOS) Build 

Thanks for starting reading this guide, i recommend to use ArchLinux for installing PostmarketOS on your device 
First that you should to do is install [pmbootstrap](https://wiki.postmarketos.org/wiki/Pmbootstrap#Installation)
Download git to clone this repo and binary files

## Preparing 

Boot the PongoOS on device by checkra1n
```sh
sudo /path/to/checkra1n -v -V -p -c -k /Pongo.bin
```
Ener your device in dfu and it will boot in pongoOS

When your device will fully boot you should load linux 
```sh
sudo python3 load_linux.py -k Kernel.lzma -d dtbpack -r initramfs
```
## After we booted into netboot mode we will see on iphone screen "Waiting for netboot"

In this part we should to setup pmbootstrap

```sh
pmbootstrap init
pmbootstrap install
pmbootstrap initfs hook_add netboot
pmbootstrap export
```
You need to setup root img for your device by this steps

## Repairing chroot (necessary)

! You mustn't skip this step because it fixes boot !

```sh
pmbootstrap chroot -r
sudo rm /usr/lib/NetworkManager/conf.d/50-tethering.conf
exit
```
After that rebuild root image
```sh
pmbootstrap install
```

## Booting device!

For first booting use:
```sh
pmbootstrap netboot serve --replace
```

For second booting and etc use:
```sh
pmbootstrap netboot serve
```

## Setting up system

Log in by ssh: 
```sh
sudo ssh user@172.16.42.1
```

Start xfce4

```sh
sudo script -f /dev/tty1
startxfce4
```
## Fix bug with opening GUI Applications 
```sh
export DISPLAY=:0
```

## Set up internet over USB

[tutorial](https://wiki.postmarketos.org/wiki/USB_Internet)

## Ending

Thanks for reading this guide, if you have questions - write me (romcikbaho4ik@gmail.com)
I'll help you if you will have problems with installing

Have a good day




