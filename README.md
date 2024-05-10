# Raspberry Pi OS2BorgerPC Kiosk Image #

   <img src="https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/assets/1641342/3d7cc208-148c-44e5-a444-a693ab52f44e" width="600">
   
   *Raspberry Pi 4 in an Argon One v2 case placed behind a wall mounted display screen*

DISCLAIMER: This is an experimental project not supported by Magenta. It has been developed by Agnete Moos, Sønderborg Kommune with support from Dennis Borup Jacobsen, Aarhus Kommune. Questions or comments should be directed to Agnete Moos agms@sonderborg.dk.

###### Contents
[How to create a bootable OS2BorgerPC RPI Kiosk Image](https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/blob/main/README.md#how-to-create-a-bootable-os2borgerpc-rpi-kiosk-image)\
[Speed up the process - Clone your Raspberry Pi SD-card and turn it into an img-file](https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/blob/main/README.md#speed-up-the-process---clone-your-raspberry-pi-sd-card-and-turn-it-into-an-img-file)\
[The RPI case](https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/blob/main/README.md#the-rpi-case)\
[Chromium installation and startup](https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/blob/main/README.md#chromium-installation-and-startup)\
[Protect the SD-card by making it read-only](https://github.com/bibsdb/os2borgerpc-kiosk-rpi-image/blob/main/README.md#protect-the-sd-card-by-making-it-read-only)


## How to create a bootable OS2BorgerPC RPI Kiosk Image ##
You can not use the standard OS2BorgerPC Kiosk Image on a Raspberry Pi because RPI use an ARM processor, that is not build on the x86 chip architecture.
There are key diffrences in how you install a RPI. You don´t run an installer to enter username, timezone and other prefereces and information. Instead you modify configuration files in the image and the boot the RPI. On boot the settings are applied.

We start with a gereric Ubuntu Server 22.04.04 LTS (64 bit) ARM image. We modify it to be a OS2BorgerPC RPI Kiosk Image and then we boot an Raspberry Pi with this image. On first boot the magic happens. The OS2BorgerPC Client is installed and you preferences are applied. 

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

## Speed up the process - Clone your Raspberry Pi SD-card and turn it into an img-file
If you need to make more than a few OS2BorgerPC Kiosk RPIs you want to speed up the process. 

Install a RPI as described above.  After boot - but before you connect to the Admin system - you can take a snapshot of the SD-card and turn it into a .img file. This image can be applied to new SD-cards using the Raspberry PI Imager software. Thereby you make pre-installed OS2BorgerPCs. Just insert a preinstalled SD-card into a RPI, turn it on and run `sudo os2borgerpc_kiosk_setup`. You are ready to rock!

1. Turn off your RPI and remove the SD-card
2. Insert the SD-card into a card reader of a PC. In have used a Lenovo Laptop running Ubuntu.
3. Follow this very fine guide to make an image from your Raspberry Pi SD-card (https://www.pragmaticlinux.com/2020/12/how-to-clone-your-raspberry-pi-sd-card-in-linux/)

## The RPI case
The official Raspberry Pi case is simple and cheap. It has no on/off button, no HDMI port and it doesn't provide cooling for the CPU. 

If you want cooling and the RPI to look more "Intel NUC-like" you can choose the [Argon One v2 case](https://raspberrypi.dk/en/product/argon-one-case-for-pi-4-aluminum-with-cooling/) (If it is out of stock just mail them...)
You need to install a custom software package support the power button and cooling regulation. 

Here is a OS2borgerPC scripts that installs the software:

[Argon One v2 case - software package installation](https://github.com/bibsdb/os2borgerpc-local-scripts/blob/master/2204rpi-argon-case.sh)

## Chromium installation and startup
Use these two scripts to install Chromium and launch the browser in full screen.

[Install Chromium on RPI](https://github.com/bibsdb/os2borgerpc-local-scripts/blob/master/2204rpi_chromium_install.sh)

[Launch Chromium on RPI](https://github.com/bibsdb/os2borgerpc-local-scripts/blob/master/2204rpi-chromiumsetup.sh)

## Protect the SD-card by making it read-only
A commonly discussed problem is that SD-cards are worn out, when beeing used as a hard drive, that has to do a lot of read-write operations. 
A way to protect the SD-card is to make it read-only. The way to accomplish that is to install the [Overlay read-only file system](https://en.wikipedia.org/wiki/OverlayFS).

When the Overlay filesystem is enabled, all changes to the harddisk are instead stored in RAM. Changes you make to the filessytem are not persisted - they are gone upon reboot. Even changes made by superuser disappears. If you need to make lasting changes, you have to turn off Overlay filesystem, do your changes and then turn Overlay filesystem back on.

Script to [Turn the Overlay Filesystem on/off](https://github.com/bibsdb/os2borgerpc-local-scripts/blob/master/2204rpi_overlayfs.sh)





  


