# raspberrypi-home-server

The setup of my Raspberry Pi home server that can be used to play media, download files via BitTorrent, act as an MQTT broker for various IOT devices, wirless access point, DNS, and more.

## Table of Contents

- [Install Raspberry PI OS in headless mode](#Install-Raspberry-PI-OS-without-Desktop)
- [SSH Access](doc/SSH.md)
- [Install Kodi](doc/Kodi.md)
- [Install Mosuitto MQTT](doc/Mosquitto.md)

### Install Raspberry PI OS without Desktop

1. Download and install the Raspberry Pi Imager software on your computer.
2. Connect your Raspberry Pi to your network using an Ethernet cable and power it on.
3. Open the Raspberry Pi Imager software on your computer and select the "Raspberry Pi OS (other)" option.
4. Choose the version of Raspberry Pi OS without desktop and click "Next".
5. In the "Choose SD Card" screen, select the SD card you want to use for the installation and click "Write".
6. Once the image has been written to the SD card, navigate to the "boot" partition on the SD card using your computer's file explorer.
7. Create an empty file named "ssh" (without any file extension) in the "boot" partition.
8. Create a file named "wpa_supplicant.conf" in the "boot" partition, and add the following configuration:
 ```conf
country=YOUR_COUNTRY_CODE
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="YOUR_SSID"
    psk="YOUR_WIFI_PASSWORD"
    key_mgmt=WPA-PSK
}
 ```
9. Replace `YOUR_COUNTRY_CODE`, `YOUR_SSID`, and `YOUR_WIFI_PASSWORD` with your own country code, WiFi network name, and password, respectively.
10. Remove the SD card from your computer and insert it into the Raspberry Pi.
11. Power on the Raspberry Pi and wait for it to boot up and connect to the network.
12. You should now be able to connect to your Raspberry Pi via SSH from your computer using the default hostname (`raspberrypi`) and the username (`pi`) and password (`raspberry`).