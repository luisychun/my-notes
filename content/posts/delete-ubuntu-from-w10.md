---
title: "Delete Dual Boot Ubuntu From Windows 10"
date: 2020-06-18T20:55:25+08:00
tags: []
draft: false
---

## Delete Ubuntu partition in Windows 10
[How to Uninstall Ubuntu from Windows Dual Boot Safely](https://itsfoss.com/uninstall-ubuntu-linux-windows-dual-boot/)

[How to delete GRUB files from a Boot EFI partition in Windows 10](https://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)

[How to Uninstall a Linux Dual-Boot System From Your Computer](https://www.howtogeek.com/141818/how-to-uninstall-a-linux-dual-boot-system-from-your-computer/)

- Open Windows disk management tool
- Delete Linux assigned partitions (look at the partition which doesn’t have a file system and drive number) 
- Right click the partition and select **Delete Volume**
- Deleted partition will be available as a chunk of free space

## Create and use a recovery drive in Windows 10
- Open Windows and search **Create a Recovery Drive**
- Ensure that USB drive you will be using is formatted as NTFS

## Boot Windows 10 from drive
- Restart PC and press F11/F12 to get BIOS boot mode
- Select boot from drive
- Repair your computer - Troubleshoot - Advanced options - Command Prompt
- At the command prompt, type **bootrec.exe /fixmbr**

## If the option above doesn't works
- Get BIOS mode, select **boot from Windows** and boot into Windows OS
- Open command prompt as Administrator and follow the commands list below, key in line by line

{{< rawhtml >}}
  <p class="show-in-mobile">
    <a href="https://gist.github.com/luisychun/fa742f109e591c41babce6a7bd064ba6" target=_blank>Gist</a>
  </p>
{{< /rawhtml >}}

```shell
diskpart
list disk
sel disk 0
list vol
sel <vol no>
/* <vol no> is a number which your FAT32 file system column */
assign letter = {letter}
/* assign any letter to {letter}  to make it easier to work with */
exit
cd /d{letter}:
ls
cd EFI
ls
rmdir /S ubuntu
```