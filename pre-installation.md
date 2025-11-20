This covers everything done before logging into the OMV web interface for the first time

1) Hardware 
    Documented hardware and external storage details.

    PI Model:                       Rasberry PI 3 Model B (1GB RAM)
    Internal Storage:               SanDisk Extreme 64GB
    External Storage:               SanDisk 16GB Cruizer FIt
    Micro SD card adapter:          Vanja SD/Micro SD card reader

2) Operating System
    Flashed 64-bit Raspberry Pi OS Lite (Bookworm/Debian 12) using the Raspberry Pi Imager. Configured SSH and secure non-root user via advanced settings.

3) Initial OMV installation
    Logged into MySky app to view the PI's Default IP address and SSH into the PI and:
    Used the wget installation script command. Noted the warning regarding Debian 11/12 support and confirmed Bookworm compatibility. This takes between 20-40 minutes, during the installation, the connection might drop. Its normal as the script reconfigures the network settings, dont panic. Wait 40 minutes to be safe.

    wget -O - https://raw.githubusercontent.com/OpenMediaVault-Plugin-Developers/installScript/master/install | sudo bash

    Note: PI connected to a HDMI cable, to Capture card adapter to PC/Laptop and use OBS software to log into the PI and view IP address works too. But this requires a wireless keyboard.

4) Network Configuration
    Post-install, Configured the network interface in order to access the web interface. Detailed steps below:
    1) sudo omv-firstaid > Select Configure Network Interface
    2) Depending on your setup, choose lan0 if your planning for the PI to stay in your house, or wlan0 if you want to use DHCP. I chose wlan0.
    3) Do you want to configure IPv4 for this interface? > Yes
    4) Do you want to configure DHCP for this interface? > Yes
    5) Do you want to configure IPv4 for this interface? > No
    6) Do you want to enable WOL for this interface? > No
    7) Enter SSID, hotspot or Wireless Router SSID works fine.
    8) Select frequency band
    9) Select management mode > WPA2 or WPA3 (whatever is availabe that your router is configured to)
    10) Enter password - Note: Configure Network Interface can be reconfigured at any time
    11) Is this network hidden or is hiding its SSID > No (makes it easier for the PI to find it)
    12) Gave the PI between 2-5 minutes to connect.
    13) Done!, the PI will now have a new IP Address, now the web interface can be accessed via:
        http://YOUR_IP_HERE
    14) See "setup_notes.md" for steps after installation.






