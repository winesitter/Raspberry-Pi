# Raspberry-Pi

Solution from: https://www.raspberrypi.org/forums/viewtopic.php?p=1075238
    
- Grab the latest Raspbian image from https://www.raspberrypi.org/downloads/raspbian/
- Grab the Etcher software from https://etcher.io/
- Use Etcher to write the Raspbian image to your SD card.
    You don't need to extract the image or format the card prior to writing.
        Just run Etcher, choose the Raspbian .zip you downloaded, pick your SD card and write.
        If you have trouble, verify the SHA256 checksum of the download.
        Writing an image to your card will erase everything previously on it!
- Remove and reinsert the SD card so that your Windows or Mac PC can see the small FAT32 partition on the card (labelled "boot").
        If you get a message telling you the card must be formatted, cancel it.
    On that small FAT32 partition, create a file with the name ssh (or ssh.txt). It can be empty, the contents don't matter.
    To connect to a wireless network, create another file on the card called wpa_supplicant.conf, which has the following inside:

    Code: Select all

    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    country=US

    network={
         ssid="Your network name/SSID"
         psk="Your WPA/WPA2 security key"
         key_mgmt=WPA-PSK
    }

        Edit country=, ssid= and psk= with your information and save the file.
        Use the 2 letter country abbreviation in CAPS (without this you will have no WiFi).
        Use a pure text editor, not a word processor, to edit the wpa_supplicant.conf file.
    Make sure that both files are in the main directory of the small FAT32 partition, not in any folder.
    Safely eject the card from your PC and use it to boot the Pi.
