### Fix grub2-mkconfig syntax error in linux
---------------------------------------------------------------------------------------------------------------------------------------

When you run any command as mentioned below and getting error :

`grub2-mkconfig -o /boot/efi/EFI/redhat/grub.cfg` If you have installed the RHEL system in EFI mode

**or**

`grub2-mkconfig -o /boot/grub2/grub.cfg` when you have installed the system in legacy BIOS (mbr) mode.


**Error Output :**

          $> grub2-mkconfig -o /boot/grub2/grub.cfg
          Generating grub configuration file ...
          Found linux image: /boot/vmlinuz-3.18.7-200.fc21.x86_64
          Found initrd image: /boot/initramfs-3.18.7-200.fc21.x86_64.img
          Found linux image: /boot/vmlinuz-3.17.4-301.fc21.x86_64
          Found initrd image: /boot/initramfs-3.17.4-301.fc21.x86_64.img
          Found linux image: /boot/vmlinuz-0-rescue-7fbd7ba795d34c92b039b5d6561474ff
          Found initrd image: /boot/initramfs-0-rescue-7fbd7ba795d34c92b039b5d6561474ff.img
          Found Windows 8 (loader) on /dev/sda2
          error: out of memory.
          error: syntax error.
          error: Incorrect command.
          error: syntax error.
          Syntax error at line 161
          Syntax errors are detected in generated GRUB config file.
          Ensure that there are no errors in /etc/default/grub
          and /etc/grub.d/* files or please file a bug report with
          /boot/grub2/grub.cfg.new file attached.
          

##### Please check last line if there is mentioned like : *`/boot/grub2/grub.cfg.new file attached`* then proceed to next steps mainly.
_________________________________________________________________________________________________

**step 1:**   Go to */boot/grub2/* and find *grub.cfg.new*

**step 2:**   Remove file *grub.cfg* by typing `rm -r grub.cfg`

**step 3:**   Rename file `"grub.cfg.new" >> "grub.cfg"`

_________________________________________________________________________________________________

#### Done!
**Regards**

**Ashish Kr**
