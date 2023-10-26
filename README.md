# Raspberry Pi OS2BorgerPC Kiosk Image #

Use it like this:
1. Download Raspberry Pi Imager. Use it to install Ubuntu 22.04 Server (64 bit) on a SD-card.
2. Overwrite the `user-data` file in the `system-boot` folder partition with the one provided here
3. Boot the RPI - wait for cloud init to finish.
4. Run `sudo os2borgerpc_kiosk_setup`

This happens automatically on first boot. The RPI must have network connection.
- Creates superuser
- Changes the hostname to os2borgerPC
- Danish keyboard and timezone
- Installs the os2borgerpc client
  


