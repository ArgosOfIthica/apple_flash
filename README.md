
These are instructions for booting a Linux USB and flashing libreboot on the Macbook 2,1 and iMac 5,2 with no use of proprietary software.

You'll need: <br>
-at least one flash drive, two is optimal <br>

Your first course of action when trying to boot from these machines is to use a disc if possible, as its very simple to boot a 64 bit OS. 
Unfortunately, the optical drives on these machines are failing in mass, and cannot be relied upon.

Normal Linux ISO's will not boot on the Macbook 2,1 and iMac 5,2, as these machines have 32 bit EFI despite having 64 bit processors. 
Most Linux ISO's do not support this kind of configuration by default, so we will have to create our own.

# Instructions 
First, download Trisquel netinstall (amd64). 
This method will likely work for many OS's, but only Trisquel's netinstall has been tested due to its universality.

Follow this guide https://mesom.de/efi32boot/index.html. 
Follow the instructions for building the correct partitions and filesystems, until the section labeled "Testing the stick". 
If the webpage ever goes down, there should be backup on the internet archive as well as in this repo.
An archive of bootia32.efi is also provided in this repo, rehosted from https://github.com/jfwells/linux-asus-t100ta

# GRUB
Once you test your USB, you will probably be thrown in a GRUB command prompt. From here, type

`ls (hd0,2)/`

You should see the contents of your ISO. Then type:
```
linux (hd0,2)/linux root=/dev/sda1
initrd (hd0,2)/initrd.gz
boot
```
# Installing Libreboot
Congratulations! 
You've finally reached a Linux environment. 
Go through some prompts and then press "Go Back". 
We aren't actually here to install Trisquel after all, we're here to replace the existing firmware with flashrom. 
Execute a shell.


From here, we're just putting Libreboot on the machine. 
You should put the libreboot utils and your desired rom on the USB, mount it, copy the files over, and follow the instructions on the libreboot website. 
Note that to flash the rom, you'll use:

```sh flash i945apple_firstflash yourrom.rom```

Its also worth noting that its fine to remove the netinstall USB after executing a shell. 
You may need to for the Macbook 2,1, as the USB ports are so close together that wide USB drives may not fit side by side.
