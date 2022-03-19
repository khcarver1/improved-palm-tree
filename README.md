# improved-palm-tree

Download puTTy here. This is what you will use to create the klipper.bin file that will be flashed to your main board. You'll enter your pi's IP address and leave everything else alone. The username is PI, password is raspberry. This can be changed later. After downloading, go to the next step.
https://www.puttygen.com/download-putty

Taken from klipper3d.org...

Building and flashing the micro-controller¶
To compile the micro-controller code, start by running these commands on the Raspberry Pi:


cd ~/klipper/
make menuconfig
Select the appropriate micro-controller and review any other options provided. Once configured, run:


make
It is necessary to determine the serial port connected to the micro-controller. For micro-controllers that connect via USB, run the following:


ls /dev/serial/by-id/*
It should report something similar to the following:


/dev/serial/by-id/usb-1a86_USB2.0-Serial-if00-port0
It's common for each printer to have its own unique serial port name. This unique name will be used when flashing the micro-controller. It's possible there may be multiple lines in the above output - if so, choose the line corresponding to the micro-controller (see the FAQ for more information).

For common micro-controllers, the code can be flashed with something similar to:


sudo service klipper stop
make flash FLASH_DEVICE=/dev/serial/by-id/usb-1a86_USB2.0-Serial-if00-port0
sudo service klipper start
Be sure to update the FLASH_DEVICE with the printer's unique serial port name.

When flashing for the first time, make sure that OctoPrint is not connected directly to the printer (from the OctoPrint web page, under the "Connection" section, click "Disconnect").

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Download WINSCP here. You'll find the "klipper.bin" file in the home>pi>out folder. For the SKR board you have, rename this to firmware.bin, put this on a clean SD card, and flash it to your printer. You'll put this card in your printer-powered off, make sure the pi is unplugged from your printer, and allow it 5 minutes to sit after turning on. Then you can plug your pi in.
https://winscp.net/eng/download.php

