# Teletype
![Teletype Logo](https://s3.eu-central-1.amazonaws.com/teletype/printer_logo.png)

# Document in development!

 Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam ac lectus sapien. Phasellus pretium, diam id molestie bibendum, tellus justo volutpat nisi, eget condimentum ex metus sit amet nulla. Integer ac sollicitudin eros, et aliquam odio. Etiam euismod dapibus dolor. Curabitur convallis, tellus in vehicula lacinia, est turpis vestibulum orci, facilisis egestas quam diam in eros. Cras a augue nec turpis rhoncus pharetra et et massa. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae;
 Sed ultricies enim orci, mattis ullamcorper felis placerat eget. Mauris sed consequat erat. Phasellus consequat finibus quam nec fringilla. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas pretium id dui ullamcorper consectetur. Aliquam ut ligula magna. Sed convallis eleifend lacus eu tincidunt. Morbi quis dui feugiat, feugiat lectus hendrerit, interdum risus. Aenean mattis elit vel lectus vestibulum rhoncus. Donec congue nibh sed viverra dictum. Sed eget leo in augue dapibus rhoncus sed nec metus. Mauris commodo quis neque vitae vestibulum. Duis pellentesque ipsum eu accumsan condimentum. Suspendisse tempus molestie dignissim. Duis nec pulvinar risus.

 ## Getting started

1. Overview
2. Parts List
3. Tools
4. Raspberry Pi Setup
5. Configure network
6. Soldering
7. Firebase Setup 
8. Teletype Setup
9. Case Assembly
10. Troubleshooting

-----

### Overview

Maecenas pretium id dui ullamcorper consectetur. Aliquam ut ligula magna. Sed convallis eleifend lacus eu tincidunt. Morbi quis dui feugiat, feugiat lectus hendrerit, interdum risus. Aenean mattis elit vel lectus vestibulum rhoncus. Donec congue nibh sed viverra dictum. Sed eget leo in augue dapibus rhoncus sed nec metus. Mauris commodo quis neque vitae vestibulum. Duis pellentesque ipsum eu accumsan condimentum. Suspendisse tempus molestie dignissim. Duis nec pulvinar risus.


### Parts List

* [Raspberry Pi Model B](https://www.raspberrypi.org/products/model-b-plus/)
* [Mini Receipt Printer](https://www.adafruit.com/products/597)
* [50 foot long receipt paper. BPA-free.](https://www.adafruit.com/products/599)
* [5V 10A power adapter](https://www.adafruit.com/products/658)
* [2.1mm Panel Jack](https://www.adafruit.com/products/610)
* [4GB SD](http://www.amazon.com/Sandisk-MicroSDHC-Memory-Card-Adapter/dp/B000SMVQK8)
* [8GB USB Flash drive](http://www.amazon.com/SanDisk-Cruzer-Low-Profile-Drive-SDCZ33-008G-B35/dp/B005FYNSUA)
* [Mini WiFi Adapter](https://www.adafruit.com/products/814)
* [USB TTL Console Cable](https://www.adafruit.com/products/954)
* T-cobbler PCB + 2x13 female header
* Enclosure + hardware

### Tools

* SD (or microSD) card reader
* USB keyboard
* Monitor (HDMI or composite) and cable
* USB cable: A to micro B
* Small screwdriver
* Soldering iron and solder
* Wire cutter and stripper
* A wireless (WiFi) access point
* Computer with USB, internet connection and at least 4.5 gigabytes free disk space
* Optional: sticky tape, heat-shrink tubing

-----

### Raspberry Pi Setup

>##### Some of these steps are already covered in depth in other tutorials.We’ll provide links with detailed discriptions.

![Raspberry Pi Model B](https://s3.eu-central-1.amazonaws.com/teletype/raspberry_pi.png)

The software for this project is built upon the "text here", 
a version of Linux for the Raspberry Pi with some  additions of our own baked in. 
Click the following link to download the IMG file:

[Teletype Distro - Teletype v0.2]()

The file is about 4.0 gigabytes and will take some time to download. 

#### While that’s working you can do:

>For Teletype project, we decided to boot our system not directly from SD Card but from USB Flash drive. During test explanation period (about 3 months) we discovered that
it's absolutely impossible to guarantee stable system work from SD Card. SD Cards have a limited read/write cycle, and when running these kind of projects from SD card, it won’t take long before you start getting corruptions and failures.

* Insert the SD card in the card reader, connect to your computer and format the card as a 
FAT32 (MS-DOS) filesystem with Disk Utility. 
Choose your SD Card from the devices listed on the right, then click on ‘Erase’, choose FAT32 in the Formats list and click on ‘Erase’

* Unmount your SD card

* Plug in your USB Flash drive, launch Disk Utility and format your SD Card using
FAT32 (MS-DOS) filesystem. 
Choose your SD Card from the devices listed on the right, then click on ‘Erase’, choose FAT32 in the Formats list and click on ‘Erase’

* Download & Install [ApplePi-Baker](http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/)

After downloading the Teletype v0.2 software, be ready for next steps: 

#### Backing Teletype.v0.2.img to USB stick – Using a Mac:

* Plug in your USB stick and launch ApplePi-Baker


* Select your USB Flash Drive and locate Teletype.v0.2.img 


* Press "Restore" button & wait about 10-15 minutes


* After procce will be finished close ApplePi-Baker


#### Install and run Teletype Distro from a USB Flash Drive:

* Insert the SD card in the card reader

* Open up the USB Flash Drive volume and copy all the files from that onto your SD card.
This copies the all-important files and instructions to tell your Raspberry Pi to boot from the USB Flash Drive.



* We need to change the default boot path to tell the Raspberry Pi to boot from your USB drive.
Open a new Finder window and go to your SD card. Open up the file called *cmdline.txt* in TextEdit or similar and amend the line which reads:

```
root=/dev/mmcblk0p2
```

to this:

```
root=/dev/sda2
```

This will instruct your Raspberry Pi to boot from the USB Flash Drive instead of from the SD card.

* Save the cmdline.txt file and close the Finder window. 

* Unmount both your USB Flash Drive and your SD card and insert them both into your Raspberry Pi

* Connect Raspberry Pi to monitor

* Connect USB keyboard

* Connect Raspberry Pi to power source

* If all goes well, it should boot from your USB Flash Drive.


**Expand the Raspbian partition**

* Login to system with next the authorization data:

```
user: teletype
password: teletype2016

```
You can [change username and password](https://www.raspberrypi.org/documentation/linux/usage/users.md)


* We neeed to utilise all the available space on your USB Flash drive.
From your Raspberry Pi, type the following command to start FDisk:

```
sudo fdisk /dev/sda
```

* Press **p** and **enter** to see the partitions. There should only be 2.

We’re going delete the Linux partition, but before we do this, we make a note of the start position for the linux partition sda2.

* Press **d** and then when prompted type 2 and then hit **enter**. This will delete the partition

We need to create a new partition, and make it large enough for the OS to occupy the full space available on the USB Flash Drive

* Type **n** to create a new partition, when prompted to give the partition type, press **p** for primary. Then it will as for a partition number, press **2** and **enter**

* You will be asked for a first sector, set this as the start of partition 2 as noted earlier. In my case this as 18280 but this is likely to be different for you.

* After this it will ask for an end position, hit **enter** to use the default which is end of disk. 

* Type w to commit the changes

* You will see a message about the Kernel using some table blah blah blah, just ignore this

* Reboot

```
sudo reboot
```

After Raspberry Pi has rebooted, we need to resize the partition

* Login to system with your password and type

```
sudo resize2fs /dev/sda2
```

This will take some time. Once it’s done reboot again.

* Login to system with your password and type

```
df -h
```

This will show the partitions and the space, you’ll see the full USB Flash Disk has all the space available now.

-----

### Configure network

_in progress_

-----

### Soldering (_in progress_)

Images and text by [Phillip Burgess at Adafruit](https://learn.adafruit.com/pi-thermal-printer/soldering)

> Some of the later soldering steps take place close to pieces of the case. Be very careful where you set your soldering iron so as not to damage the plastic parts! Also watch out for flux spatter.
During the soldering and assembly process, certain parts will become “tethered” together by wires…always pick up and move these parts together, don’t let pieces hang by the wires…this could damage parts or solder joints

>First we’ll be joining the T-Cobbler board and 26-pin socket.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/1.jpg)

>Normally the Cobbler would have a header soldered to the top, but we’re doing something different with this kit: the socket sits on the underside of the board.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/2.jpg)

>Tack the header in place by soldering just one pin (any will do) on the top side of the board. Notice we’re soldering on the label side for this step

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/3.jpg)

> Check that the header is straight and square. If not, heat the one soldered pin and realign the header.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/4.jpg)


> Once the header is straight, the rest of the pins can be soldered.
It’s normal for a bit of solder to drain or “wick” down the hole being soldered…in fact, this is good and proper soldering technique. But only a little. If you keep feeding solder, the socket holes on the other side will fill in with solder and won’t plug into the Raspberry Pi!

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/5.jpg)

>After soldering (and allowing some time to cool), you can test fit the Cobbler on the Raspberry Pi. Gently pry it off with your fingers afterward…more soldering lies ahead…

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/6.jpg)


> We don’t need that much length inside the case, so we’ll be cutting them in half. Do not throw away the other half! We’ll be repurposing the extra wire in a subsequent step.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/7.jpg)


> The power cable has a different connector at each end. We want to keep the wider of the two connectors for the printer. The small connector at the other end can be clipped off.
The data cable has wide connectors at both ends. One should be left connected, the other can be clipped off and discarded. 
If you inadvertently cut the wrong connector off the power cable, you may be able to salvage it using a jeweler’s screwdriver to push the pin sockets out (there’s a small tab on the side that keeps them in place) and replace the connector at the other end.


![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/8.jpg)


>After cutting, you should have two cables, each about 7 inches long, both with a “wide” connector: one for power (red and black) and one for data (green, yellow and black).
You should also have five loose wires (two black, one red, yellow and green). Keep these for later steps.
The two connectors (one small, one wide) can be discarded.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/9.jpg)


>There are three “legs” on the DC jack, but we’ll just be using two of them.
The large center leg corresponds to the power supply tip, which will be +5V.
The “outer” of the two small legs is the power supply ring (ground).
The “inner” small leg is not connected.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/10.jpg)

> Strip about 1/4" insulation from the red and black wires on the power cable and the spare wires. 
Twist the wires a bit to prevent the strands from fraying.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/11.jpg)

> Twist the two red wires together, feed through the large center leg (+) and solder in place.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/12.jpg)

> Repeat with the two black wires through the “outer” small leg (–).
Remember, the “inner” small leg is not connected.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/13.jpg)

> In the next few steps, we’ll be connecting components to the Cobbler according to the following diagram:

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/14.png)

> Strip about 1/4" insulation from the BLACK and YELLOW wires of the serial data cable.
The GREEN wire should not be stripped.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/15.jpg)

> Solder the YELLOW wire to the TXD pin on the Cobbler. Solder the BLACK wire to one of the GND pins — any will do, here we’re using the one between pins 4 and 17 on the left side.
The wires are inserted from the top side of the board and soldered on the underside.
The green wire is not connected.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/16.jpg)


> Your Cobbler and cable should now look like this, with the green wire left dangling for now.

![](https://s3.eu-central-1.amazonaws.com/teletype/soldering/17.jpg)



>About That Green Wire…
The green wire is only used for rare cases where the printer returns data to the computer. It’s left unconnected because the printer works at 5 Volts and the Raspberry Pi at 3.3 Volts…connecting directly to the RXD pin could permanently damage the Raspberry Pi! (The other direction is safe as-is.)
There's only a single function in the thermal printer library that even references this (paper detect, and this isn’t used by any of our example code)…everything else moves from the computer to printer. As this is an esoteric feature, and with the risk of damage if wrongly connected, we chose to leave this unused. If (and only if) you think you might really need this feature, you can solder a 10K-Ohm resistor (not included) in-line between the GREEN wire and the RXD pin on the Cobbler. Cover this in heat-shrink tube to avoid contact with the board.

-----

### Firebase Setup


_in progress_

-----

### Teletype Setup 


_in progress_

-----

### Case Assembly


_in progress_

-----

### Troubleshooting


* **I need to diagnose a software or configuration problem, but can’t connect to the Raspberry Pi over WiFi.**

	Connect an HDMI or composite monitor and a keyboard or USB hub, 
	and you can work with the system like a regular “desktop” Raspberry Pi to troubleshoot the issue.


* **Sometimes the paper jams in the printer, especially when printing inverse blocks of text**

	Edit the file Adafruit_Thermal.py and look for this line (around line 53):
	```
	defaultHeatTime = 60
	```

	Replace '60' with a smaller number. Try decreasing it by 10 and repeating until the problem is resolved.

* **Text and graphics print very faint.**

	Edit the file Adafruit_Thermal.py and look for this line (around line 53):
	```
	defaultHeatTime = 60
	```
	Replace '60' with a larger number. Try increasing it by 10 and repeating until the output improves.






