# Raspberry Pi OS2BorgerPC Kiosk Image #

## How to create a bootable OS2BorgerPC RPI Kiosk Image ##
1. Download [Raspberry Pi Imager](https://www.raspberrypi.com/software/). Use it to install Ubuntu 22.04 Server (64 bit) on a SD-card.
2. While you have the SD-card in the card reader open the `system-boot` directory in a file manager.
3. Overwrite these two files with the ones provided in this project.
   - `user-data`
   - `config.txt`
   - `network-config`


4. Validate the contents of `network-config` as it will be inserted into /etc/netplan/config.yml and thereby become the network setup for your RPI. You might have different networking preferences. The provided version both support wired connection and wifi. Please provide the SSID you want the RPI to connect to. 
5. Now your can insert the SD-card into the RPI and boot. IMPORTANT: Your RPI must be connected to the internet during first boot
5. On first boot cloud-init configures the RPI and installs OS2BorgerPC client. Wait for cloud-init to finish.
6. Run `sudo os2borgerpc_kiosk_setup`

## Cloning your RPI ##
After step 5 - before you run `sudo os2borgerpc_kiosk_setup` - is a good time to clone your RPI. The result is a generic OS2BorgerPC RPI image. This image can be applied to new SD-cards using the Raspberry PI Imager software. In this way you can quickly make more OS2BorgerPC Kiosk RPIs. 

1. Turn off your RPI and remove the SD-card
2. Insert the SD-card into a card reader of a PC. In this guide I use a Linux PC.
3. Follow this very fine guide to make an image from your Raspberry Pi SD-card (https://www.pragmaticlinux.com/2020/12/how-to-clone-your-raspberry-pi-sd-card-in-linux/)
   


  


