# Raspberry Pi OS2BorgerPC Kiosk Image #

## How to create a OS2BorgerPC RPI Kiosk Image ##
1. Download [Raspberry Pi Imager](https://www.raspberrypi.com/software/). Use it to install Ubuntu 22.04 Server (64 bit) on a SD-card.
2. While you have the SD-card in the card reader open the `system-boot` directory in a file manager.
3. Overwrite these two files with the ones provided in this project.
   - `user-data`
   - `config.txt`
4. Now your can insert the SD-card into the RPI and boot. IMPORTANT: Your RPI must be connected to the internet during first boot
6. On first boot cloud-init configures the RPI and installs OS2BorgerOC client. Wait for cloud-init to finish.
7. Run `sudo os2borgerpc_kiosk_setup`

## Cloning your custom image ##
After step 3 - before first boot - you kan clone the contents 

## This happens on first boot ##
This happens automatically on first boot. The RPI must have network connection.
- Creates superuser
- Changes the hostname to os2borgerPC
- Danish keyboard and timezone
- Installs the os2borgerpc client
- HDMI setup
  


