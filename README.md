# Welcome to AMD OS X Vanilla


## What you'll need :
* GNOME Disks is a graphical front-end for udisks included in the "gnome-disk-utility" package.
* GParted is a free partition editor for graphically managing your disk partitions.
* DMG2IMG comand line tool that allows you to convert a (compressed) Apple Disk Images
* gibMacOS - An awesome tool from CorpNewt ( https://github.com/corpnewt/gibMacOS )
* The Vanilla AMD config courtesy of AlGrey ( https://github.com/AMD-OSX/AMD_Vanilla )
* A USB drive 8gb+
* Some patience...
## This guide will support the following versions of macOS on Zen and 15H/16H AMD:

### High Sierra 10.13.6 (17G65, 17G66, 17G8030)
### Mojave 10.14.6 (18G84, 18G87, 18G95)

# Getting the macOS Installer
## Get macOS Installer with gibMacOS
* Downloading the installer files fairly straight forward process but may take a while depending on your internet speeds.
* To start extract gibMacOS and and open your terminal change directory to the gibmacos.command script.
* Run it with ./gibMacOS.command
### This will allow you to choose the macOS version to download.
<img src="pict/2019-09-11_12-41.png" width=600>

* In my case I chose option 1. It will download the macOS installer files.
* Make sure that BaseSystem.dmg is downloaded completely thats what we will use to create the installer
* Once downloaded you can proceed to the next step.
# Creating the macOS Install USB
## Now to create the install USB...

* Find BaseSystem.dmg inside `/gibMacOS-master/macOS\ Downloads/publicrelease/`
 * Drag it to your desktop or somewhere else if you prefer.
 * Open your terminal and change directory to where the BaseSystem.dmg file is in my case:
 * `cd Desktop`
 * Then run `dmg2img BaseSystem.dmg base.iso` it will convert the the `dmg` file to `iso` file named `base.iso`
 * Open `Disks` AKA "Gnome-Disk-Disk-Utility" and drag `base.iso` to it and hit start restoring.
 * This will take a wile.
 <img src="pict/2019-09-11_12-54.png" width=700>
 
 * Once it is done restoring the iso open up `Gparted` and select your usb-drive.
 <img src="pict/2019-09-11_11-39.png" width=700> 
 
 * Rigth click on the macOS partition and hit recize/move
  <img src="pict/2019-09-11_11-54.png" width=700> 
  
  * Give it `200MB` of space make sure you hit the `+` for it to work :) and hit Recise/Move
  * It will move the whole hfs+ partition to the right and give us 200MB free space for our EFI partition. 
  * This will take a long times sit tight.
  <img src="pict/2019-09-11_11-56.png" width=700>  
  
  * Do not forget to hit apply 
   <img src="pict/2019-09-11_11-58.png" width=700> 
   
   * Right click on your new 200MB unallocated space. 
     <img src="pict/2019-09-11_12-08.png" width=700>
     
     * Hit New
     <img src="pict/2019-09-11_12-09.png" width=700>
     
     * In `File System add fat32 and Lable EFI`     
     <img src="pict/2019-09-11_12-12.png" width=700>
     
     * Hit apply again 
     <img src="pict/2019-09-11_12-13.png" width=700>
     
     * Once done applying changes righ click on your new EFI partition and hit `Manage Flags`
     <img src="pict/2019-09-11_12-15.png" width=700> 
     
     * Select boot and esp
      <img src="pict/2019-09-11_12-16.png" width=700>     
     
