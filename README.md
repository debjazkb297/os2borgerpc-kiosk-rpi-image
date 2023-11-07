# Raspberry Pi OS2BorgerPC Kiosk Image #

## How to create a bootable OS2BorgerPC RPI Kiosk Image ##
1. Download [Raspberry Pi Imager](https://www.raspberrypi.com/software/). Use it to install Ubuntu 22.04 Server (64 bit) on a SD-card.
2. While you have the SD-card in the card reader open the `system-boot` directory in a file manager.
3. Overwrite these two files with the ones provided in this project.
   - `user-data`
   - `config.txt`
4. Now your can insert the SD-card into the RPI and boot. IMPORTANT: Your RPI must be connected to the internet during first boot
5. On first boot cloud-init configures the RPI and installs OS2BorgerOC client. Wait for cloud-init to finish.
6. Run `sudo os2borgerpc_kiosk_setup`

## Cloning your RPI ##
After step 5 - before you run `sudo os2borgerpc_kiosk_setup` - is a good time to clone your RPI. The result is a generic OS2BorgerPC RPI image. This image can be applied to new SD-cards using the Raspberry PI Imager software. In this way you can quickly make more OS2BorgerPC Kiosk RPIs. 


  


