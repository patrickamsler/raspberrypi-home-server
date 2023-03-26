# Kodi

Kodi is a free and open-source media player software that can be used to play a wide variety of media files, including videos, music, and photos. Originally developed for the Xbox gaming console, Kodi is now available on a wide range of platforms, including Raspberry Pi.

Kodi's user interface is highly customizable and allows users to organize their media library in a variety of ways. It also supports a wide range of add-ons and plugins that can be used to extend its functionality, including support for streaming services, live TV, and more.

One of the key features of Kodi is its ability to handle a wide range of media formats, including high-resolution video and audio formats. It also supports subtitles and can automatically download and sync subtitles for media files.

Overall, Kodi is a versatile media player that can be used to play, organize, and stream media files from a variety of sources, making it a popular choice for home theater enthusiasts and media enthusiasts alike.

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
