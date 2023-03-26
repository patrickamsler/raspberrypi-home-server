# Kodi

Kodi is a free and open-source media player software that can be used to play a wide variety of media files, including videos, music, and photos. Originally developed for the Xbox gaming console, Kodi is now available on a wide range of platforms, including Raspberry Pi.

One of the key features of Kodi is its ability to handle a wide range of media formats, including high-resolution video and audio formats. It also supports subtitles and can automatically download and sync subtitles for media files.

## Installation

If you're running Raspberry Pi OS in headless mode and want to use Kodi on a TV connected through the HDMI output, you can follow these steps:

1.	Open a terminal window on your Raspberry Pi.
2.	Update the package list by running the following command: `sudo apt-get update`
3.	Install Kodi by running the following command: `sudo apt-get install kodi`
4.	Configure Raspberry Pi to use the HDMI output as the default display by running the following command: `sudo raspi-config`
5.	In the Raspi-config menu, select "Advanced Options" and then "Resolution". Choose the resolution that matches your TV and press Enter.
6.	In the same menu, select "Advanced Options" again and then "Audio". Choose "Force HDMI" and press Enter.
7.	Press the "Tab" key to highlight "Finish" and press Enter to exit the Raspi-config menu.
8.	Restart your Raspberry Pi by running the following command: `sudo reboot`
9.	Once your Raspberry Pi has restarted, Kodi should automatically launch on your TV through the HDMI output.

That's it! You now have Kodi running on your TV through the HDMI output of your Raspberry Pi.

In general, the user that runs Kodi on a Raspberry Pi needs to belong to the "video" and "audio" groups. This is because Kodi requires access to the video and audio devices on the system to play media. The default pi user belongs to this group. If run Kodi with a differen user you may add it to the groups.

To add a user to the "video" and "audio" groups, you can run the following commands:
```bash
sudo usermod -a -G video <username>
sudo usermod -a -G audio <username>
```