# Welcome to AMD OS X Vanilla Made On Linux


## Tools you'll need :
 GNOME Disks is a graphical front-end for udisks included in the "gnome-disk-utility" package.  
 GParted is a free partition editor for graphically managing your disk partitions.  
 DMG2IMG comand line tool that allows you to convert a (compressed) Apple Disk Images  
 gibMacOS - An awesome tool from CorpNewt ( https://github.com/corpnewt/gibMacOS )  
 The Vanilla AMD config courtesy of AlGrey ( https://github.com/AMD-OSX/AMD_Vanilla )  
 A USB drive 8gb+  
 Some patience...
## This guide will support the following versions of macOS on Zen and 15H/16H AMD:  

### High Sierra 10.13.6 (17G65, 17G66, 17G8030)  
### Mojave 10.14.6 (18G84, 18G87, 18G95)  
### Catalina 10.15 (19A583)
  
  ## Get macOS Installer with gibMacOS  
  Downloading the installer files fairly straight forward process but may take a while depending on your internet speeds.  
  To start extract gibMacOS and and open your terminal change directory to the gibmacos.command script.  
  Run it with `./gibMacOS.command `   
  ***This will allow you to choose the macOS version to download.*** 
  <img src="pict/2019-09-11_12-41.png" width=700>  

  In my case I chose option 1. It will download the macOS installer files.  
  Make sure that BaseSystem.dmg is downloaded completely thats what we will use to create the installer  
  Once downloaded you can proceed to the next step.  
  ## Creating the macOS Install USB  
  Find BaseSystem.dmg inside `/gibMacOS-master/macOS\ Downloads/publicrelease/`  
  Drag it to your desktop or somewhere else if you prefer.  
  Open your terminal and change directory to where the BaseSystem.dmg file is in my case:  
  `cd Desktop`  
  Then run `dmg2img BaseSystem.dmg base.iso` it will convert the the `dmg` file to `iso` file named `base.iso`  
  Open `Disks` AKA "Gnome-Disk-Disk-Utility" and drag `base.iso` to it and hit start restoring.
  This will take a wile.  
  <img src="pict/2019-09-11_12-54.png" width=700>  
 
  Once it is done restoring the iso open up `Gparted` and select your usb-drive.  
  <img src="pict/2019-09-11_11-39.png" width=700>   
 
  Rigth click on the macOS partition and hit resize/move  
  <img src="pict/2019-09-11_11-54.png" width=700>   
  
   Give it `200MB` of space make sure you hit the `+` for it to work :) and hit Resise/Move  
   It will move the whole hfs+ partition to the right and give us 200MB free space for our EFI partition.     
     
   <img src="pict/2019-09-11_11-56.png" width=700>   
  
   Do not forget to hit apply, This will take a long time sit tight.     
   <img src="pict/2019-09-11_11-58.png" width=700>   
   
   Right click on your new 200MB unallocated space.   
   <img src="pict/2019-09-11_12-08.png" width=700>  
     
   Hit New  
   <img src="pict/2019-09-11_12-09.png" width=700>  
     
   In File System set it to `fat32` and in Label `EFI`         
   <img src="pict/2019-09-11_12-12.png" width=700>  
     
   Hit apply again   
   <img src="pict/2019-09-11_12-13.png" width=700>  
     
   Once done applying changes righ click on your new EFI partition and hit `Manage Flags`  
   <img src="pict/2019-09-11_12-15.png" width=700>   
     
   Select boot and esp  
   <img src="pict/2019-09-11_12-16.png" width=700>    
      
   ***Now whe need to mount the EFI partition***  
   The easiet way is to open up `Disks` again and mount it that way     
   <img src="pict/2019-09-11_12-18.png" width=700>   
      
   Now you should see an empty EFI partition in your file system  
       
   <img src="pict/2019-09-11_12-19.png" width=700>  
        
   ## Installing Clover  
       
   ***Download CloverISO-xx.tar.lzma***      
   https://github.com/Dids/clover-builder/releases            
   Extract it then extract the iso as well and copy the EFI folder to the empty EFI partition    
   <img src="pict/2019-09-11_12-26.png" width=700>  
        
   ## Drivers  
   Now open EFI/CLOVER/drivers/UEFI and all we need there are:    
   ApfsDriverLoader.efi AptioMemoryFix.efi HFSPlus.efi    
   <img src="pict/2019-09-11_12-28.png" width=700>
        
        
   ## Kexts  
        
   Now download your kexts here:    
   https://onedrive.live.com/?authkey=%21APjCyRpzoAKp4xs&id=FE4038DA929BFB23%21455036&cid=FE4038DA929BFB23    
   Place your kexts in /EFI/CLOVER/kexts/other   
   To know what kexts you need check this link:  
        https://vanilla.amd-osx.com/setting-up-clover-for-amd-vanilla/kexts.html

   You will also need [AppleMCEReporterDisabler.kext](https://github.com/AMD-OSX/AMD_Vanilla/raw/master/Extra/AppleMCEReporterDisabler.kext.zip) on Catalina too.
        
   ***This is how my kexts folder looks like***    
   <img src="pict/2019-09-11_12-31.png" width=700>   
        
   You should have a sample `config.plist` inside /EFI/CLOVER remove it.  
    If on amd cpu get your sample config.plist here:  
        https://github.com/AMD-OSX/AMD_Vanilla  
        
   If on Intel cpu you can get a sample here:  
   https://github.com/corpnewt/Hackintosh-Guide   
        
   ***Make sure to learn the basics of config.plist***  
   https://github.com/corpnewt/Hackintosh-Guide/blob/master/config.plist-basics.md   
        
  This shoud be enough to boot into the installer GOOD Luck!!  
        
  [![Video](https://github.com/Broly1/Hackintosh-linux-Installer/blob/master/pict/novo.png)](https://youtu.be/DDJka-Ykzn8 "Video")


        
        
   ## All Credits to:
   **CorpNewt algrey Shannee XLNC.**        
