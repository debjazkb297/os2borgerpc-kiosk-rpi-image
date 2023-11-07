# Raspberry Pi OS2BorgerPC Kiosk Image #

Use it like this:
1. Download Raspberry Pi Imager. Use it to install Ubuntu 22.04 Server (64 bit) on a SD-card.
2. While you have the SD-card in the card reader open the `system-boot` folder on the card. Overwrite the two files with tho ones provided in this project.
3. - `user-data`
   - `config.txt`
4. Boot the RPI - wait for cloud init to finish.
5. Run `sudo os2borgerpc_kiosk_setup`

This happens automatically on first boot. The RPI must have network connection.
- Creates superuser
- Changes the hostname to os2borgerPC
- Danish keyboard and timezone
- Installs the os2borgerpc client
  


