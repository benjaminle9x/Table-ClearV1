# TABLE CLEAR V1

## Table of Contents
* [Introduction](#intro)
* [Parts](#parts)
* [Time Commitment](#time)
* [Raspberry Pi Configuration](#rpicon)
* [Connecting the GPSV3 Neo Sensor to Raspberry Pi 3b+ with Breadboard](#bread)
* [PCB Designing & Soldering](#pcb)
* [Power Up](#power)
* [Configurating services](#config)
* [Unit Testing](#unit)

## <a name="intro">Introduction</a>
![Project_Image](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/project.jpg)
* The Table Clear project is a wait-list, reservations and seating management system that turns smartphones into pagers, revolutionizing the way restaurants connect with their customers.
* Table Clear allows restaurants to see reservations, booking information and wait-list in real-time database, sends notification to customers when their table is ready, seats them efficiently and confirms the booking by sending notification messages.

## <a name="parts">Parts</a>
* Raspberry Pi any version ([Preferred 3B, 3B+, 4](https://www.amazon.ca/RS-Components-Raspberry-Model-Motherboard/dp/B07BFH96M3/ref=sr_1_4?crid=5P53UCWHTKDB&keywords=raspberry+pi+3b%2B&qid=1575998783&sprefix=raspb%2Caps%2C168&sr=8-4)) with [MicroSD Card preinstalled with Raspbian Full Version](https://www.amazon.ca/EnjoyGadgets-Raspberry-Pre-Installed-Raspbian-OpenELEC/dp/B07GZVN8DP/ref=sr_1_2?keywords=sd+card+preinstalled+with+raspbian&qid=1575998847&sr=8-2). ($95 ~ $100)
* [GPSV3 Neo 6M Sensor with Antenna Module](https://www.amazon.ca/GY-GPSV3-M8N-NEO-M8N-001-Eighth-Beidou-Control/dp/B07Z442LSN/ref=sr_1_fkmr1_1?keywords=gpsv3+neo+6m&qid=1575998891&sr=8-1-fkmr1). ($40 ~ $50)
* [HDMI to VGA cable](https://www.amazon.ca/VicTsing-Adapter-Gold-Plated-Active-Converter/dp/B00YMN9VV0/ref=sr_1_3?keywords=hdmi+to+vga&qid=1575998971&sr=8-3), [VGA to VGA cable](https://www.amazon.ca/DTECH-Computer-Resolution-Projectors-Displays/dp/B0781876KT/ref=sr_1_1_sspa?keywords=vga+to+vga&qid=1575998991&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExWVhZRDhNTFlZNlcwJmVuY3J5cHRlZElkPUEwNzIyODM2MzNWSUNTRVpTNVpKNSZlbmNyeXB0ZWRBZElkPUEwMjkxMjAzMjJDME1YS1JDT1A1QyZ3aWRnZXROYW1lPXNwX2F0ZiZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=), [Raspberry Pi Power cable](https://www.amazon.ca/Adapter-Charger-Portable-Samsung-External/dp/B071KWFZ9Z/ref=sr_1_2_sspa?keywords=raspberry+pi+power+cable&qid=1575999008&sr=8-2-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExUVFCSlpFRllLUVVSJmVuY3J5cHRlZElkPUEwNjMwMDI1QlRCRlczTk5QQk1NJmVuY3J5cHRlZEFkSWQ9QTA1NzA0MTkyREpEMDhQS1Q2U1MwJndpZGdldE5hbWU9c3BfYXRmJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ==) ($30 ~ $40)
* [GPS Antenna with strong Wifi connection](https://www.amazon.ca/dp/B071DS35G2/ref=pe_3034960_233709270_TE_item_image) + [RF U.FL Mini PCI to RP-SMA Female Adapter](https://www.amazon.ca/dp/B07NVT8FMT/ref=pe_3034960_236394800_TE_dp_i1) ($30)
* Monitor, keyboard, mouse, breadboard. (optional)
* [8 doubled female pins and 4 singled female pins](https://www.amazon.ca/Gikfun-2-54mm-Female-Straight-Connector/dp/B01K77Y3GC/ref=sr_1_4?keywords=8+double+female+pins&qid=1575999712&sr=8-4) 
* PCB Design - [Click here to retrieve the Gerber file for PCB](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Electric%20Folder/HoangLongLe_TableClearV3.zip)


Total: $240 ~ $265. 

## <a name="time">Time Commitment</a>
* Purchasing and delivering parts would take approximately 1 week.
* Assemblying, testing and implementing codes would take take approximately 1 week.
* Total: ~ 2 weeks

## <a name="rpicon">RaspberryPi Configuration</a>
* Create your Raspberry Pi's [image](https://github.com/six0four/StudentSenseHat/blob/master/cribpisdcard.md) for your project.

## <a name="bread">Breadboard Design</a>
* There are only 4 wires needed to connect the GPS Module to the Raspberry Pi
* GPSV3 Neo 6M      -            Raspberry Pi
* VCC               -            Pin 1 (3.3V)
* TX                -            Pin 10 (RX - GPIO15)
* RX                -            Pin 8 (TX - GPIO14)
* GND               -            Pin 6 (GND)
![Breadboard](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/breadboard.png)

## <a name="pcb">PCB Designing and Soldering</a>
* PCB Board design: Retrieve the Fritzing file in `Electric Folder/GY-NEO6MV2.fzz`, export the PCB design as Production in Gerber files format.
![PCBDesign](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/pcb.png)
* PCB Soldering
![PCBSold1](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/solder1.jpg)
![PCBSold2](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/solder2.jpg)

## <a name="power">Power Up</a>
* Before powering up the entire Hardware, make sure you test the resistance between the VCC and the GND pin on the PCB Board. The resistance there should be extremely high. If not, the PCB Board is shorted and eventually will damage Raspberry Pi, as well as the GPS Sensor.
![Power](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/piv1.jpg)

## <a name="config">Configurating services</a>
* Install pip:
```
sudo apt-get install python-pip
```
* Install pynmea2: 
```
sudo pip install pynmea2
```
* Install GPS software: 
```
sudo apt-get install gpsd gpsd-clients python-gps minicom
```
* Modify serial port cmdline.txt: `sudo nano /boot/cmdline.txt` and replace all the content with the following lines: 
```
dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles
```
* Change startup settings: `sudo nano /boot/config.txt` and Add the following lines at the end of 'config.txt' file:
```
dtparam=spi=on
dtoverlay=pi3-disable-bt
core_freq=250
enable_uart=1
force_turbo=1
init_uart_baud=9600
```
* Reboot the system: 
```
sudo reboot
```
* Configure the module for the 9600 rate: 
```
stty -F /dev/ttyAMA0 9600
```
* Connect AMA0 to the GPS Software:
* 1st: Kill the process and add the device to the gpsd tool: 
```
sudo killall gpsd
sudo nano /etc/default/gpsd
```
* 2nd: Edit the file /etc/default/gpsd and add the serial port in DEVICES:
```
DEVICES="/dev/ttyAMA0"
```
* 3rd: Restart the software
```
sudo systemctl enable gpsd.socket
sudo systemctl start gpsd.socket
sudo cgps -s
```

## <a name="unit">Unit Testing</a>
* Testing the terminal output of the sensor works: `cat /dev/ttyAMA0`
![Raw](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/raw.PNG)
* Run the script:
```
cd Python-NEO-6M-GPS-Raspberry-Pi
sudo python Neo6mGPS.py
```
* Implement the source code:
```
import serial
import pynmea2
def parseGPS(str):
    if str.find('GGA') > 0:
        msg = pynmea2.parse(str)
        print "Timestamp: %s -- Lat: %s %s -- Lon: %s %s -- Altitude:
%s %s" %
(msg.timestamp,msg.lat,msg.lat_dir,msg.lon,msg.lon_dir,msg.altitude,m
sg.altitude_units)
serialPort = serial.Serial("/dev/ttyAMA0", 9600, timeout=0.5)
while True:
    str = serialPort.readline()
    parseGPS(str)
```
* Output terminal:
![Out](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/output.PNG)
* Both hardware and software part for this project is quite simple; therefore, it would be possible to make a thousand of such project in a short period of time without skipping any steps or processes.




