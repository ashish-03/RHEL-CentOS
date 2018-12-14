### For enable windows boot option in grub after installing rhel/centos. 
________________________________________________________________________________________________________________________________________

**Step 1:** *Please be ensure that you have not wiped your Hard Disk while installing rhel/centOS*

________________________________________________________________________________________________________________________________________
**Step 2:** *Try:*

          `grub2-mkconfig -o /boot/efi/EFI/redhat/grub.cfg` if you have installed the RHEL system in EFI mode
          
                          or
                          
          `grub2-mkconfig -o /boot/grub2/grub.cfg` when you have installed the system in legacy BIOS (mbr) mode

________________________________________________________________________________________________________________________________________
##### Else Below: 

**Step 3:** Open terminal in linux and type : `su`
                               password :
**Step 4:** Type : `fdisk -l`
      
**output :** 

      ----------------------------------------------------------------------
      Disk /dev/sda: 255 heads, 63 sectors, 1106 cylinders
      Units = cylinders of 16065 * 512 bytes
      
      Device Boot    Start       End    Blocks   Id  System
      /dev/sda1   *         1         4     32098+  83  Linux
      /dev/sda2             5      1106   8851815    5  Extended
      /dev/sda5             5       323   2562336   83  Linux
      /dev/sda6           324       515   1542208+  83  Linux
      /dev/sda7           516       643   1028128+  83  Linux
      /dev/sda8           644       720    618471   82  Linux swap
      /dev/sda9           721       771    409626   83  Linux
      /dev/sda10          772      1106   2690856   83  Linux
      ----------------------------------------------------------------------
**Step 5:** Find **`*`** marked device path from above output, here is `/dev/sda1` so we use *"(hd0,1)"* in next step.

**Step 6:** Now type `vi /etc/grub.d/40_custom` and enter below code without delete any line from file.
          
          menuentry "Windows 10" 
          { set root = (hd0,1)
          chainloader +1 }
          
**Step 7:** Type `grub2-mkconfig -o /boot/grub2/grub.cfg` **or** `grub2-mkconfig -o /boot/efi/EFI/redhat/grub.cfg` [already mentioned above]

**Step 8:** It's done, now reboot your System.
________________________________________________________________________________________________________________________________________

If it shows any error please find below link: 

[rhel-centos/Fix grub2-mkconfig-syntax-error.md](https://github.com/ashish-03/rhel-centos/commit/9b6e5d8fe952dfa80d864874ca9f700abb7c2302)
      
#### Thanks!
**Ashish Kr**
