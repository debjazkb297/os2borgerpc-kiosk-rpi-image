# Raspberry Pi OS2BorgerPC Kiosk Image #

This guide has been tested on a Raspberry Pi 4.

## How to create a bootable OS2BorgerPC RPI Kiosk Image ##
1. Download and install [Raspberry Pi Imager](https://www.raspberrypi.com/software/) on a PC. I have used a Lenovo Laptop running Ubuntu, but it should be possible from Windows too.
2. Place a SD-card in the card reader of your PC.
3. Start the Raspberry Pi Imager program
   - In **Raspberry Pi Device** select **Raspberry Pi 4**
   - In **Operating system**. Scroll down and unfold **Other general-purpose OS**. Choose **Ubuntu**. Scroll down and select **Ubuntu Server 22.04.04 LTS (64 bit)**
   - In **Storage**. Choose the SD-card you have inserted.
   <br><br>
   <img src="https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/assets/1641342/5fe1044c-099b-4608-97ec-374a01dfdec0" width="800">


5. Then you are asked if you want to apply OS customization settings. Press **No**. We do that by applying our own config-files in the next step.
    <br><br>
   <img src="https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/assets/1641342/4d967a39-a7d9-44a0-a625-9361ee86069e" width="600">
   <br><br>

7. Now confirm to continue. Press **Yes**
   <br><br>
   <img src="https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/assets/1641342/095c50c3-b1b3-4b24-8e1a-7acb26dbd397" width="600">
   <br><br>

9. The Ubuntu Image is written to your SD-card. This will take a few minutes.

---
   
Now we need to configure the Ubuntu Image with some custom configuration files.
1. Access the  SD-card through the file manager. Open the `system-boot` directory.
    <br><br>
   <img src="https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/assets/1641342/0f6667fd-6ae9-4c45-bf35-94f64ae21c2e" width="800">
   <br><br>

2. Overwrite three files with the ones provided in this project.
   - `user-data`
   - `config.txt`
   - `network-config`

3. Validate the contents of `network-config`. It will be inserted into /etc/netplan/config.yml and thereby become the network setup for your RPI. You might have different networking preferences. The provided version both support wired connection and wifi. Please provide the SSID you want the RPI to connect to. 
4. Now your can insert the SD-card into the RPI and boot. **IMPORTANT**: Your RPI **must** be connected to the internet during first boot
 On first boot cloud-init configures the RPI and installs the OS2BorgerPC client. Wait for cloud-init to finish. It can take a few minutes.
5. Now you are ready to connect the RPI to OS2BorgerPC Admin. Run `sudo os2borgerpc_kiosk_setup` as you would normally do after installing a OS2BorgerPC Kiosk PC.

## Cloning your RPI ##
After step 4 - before you run `sudo os2borgerpc_kiosk_setup` - is a good time to clone your RPI. The result is a generic OS2BorgerPC RPI image. This image can be applied to new SD-cards using the Raspberry PI Imager software. In this way you can quickly make more OS2BorgerPC Kiosk RPIs. 

1. Turn off your RPI and remove the SD-card
2. Insert the SD-card into a card reader of a PC. In this guide I use a Linux PC.
3. Follow this very fine guide to make an image from your Raspberry Pi SD-card (https://www.pragmaticlinux.com/2020/12/how-to-clone-your-raspberry-pi-sd-card-in-linux/)
   


  


