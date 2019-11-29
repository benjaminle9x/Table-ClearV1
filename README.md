# TABLE CLEAR V1

## Table of Contents
* [Introduction](#intro)
* [Parts](#parts)
* [Time Commitment](#time)
* [Connecting the GPSV3 Neo Sensor to Raspberry Pi 3b+ with Breadboard](#bread)
* [PCB Designing & Soldering](#pcb)
* [Power Up](#power)
* [Configurating services](#config)
* [Unit Testing](#unit)

## <a name="intro">Introduction</a>
* The Table Clear project is a wait-list, reservations and seating management system that turns smartphones into pagers, revolutionizing the way restaurants connect with their customers.
* Table Clear allows restaurants to see reservations, booking information and wait-list in real-time database, sends notification to customers when their table is ready, seats them efficiently and confirms the booking by sending notification messages.

## <a name="parts">Parts</a>
* Raspberry Pi any version (Preferred 3B, 3B+ or 4) with microSD Card preinstalled with Raspbian Full Version. ($70 ~ $75)
* GPSV3 Neo 6M Sensor with Antenna Module. ($110 ~ $120)
* HDMI to VGA cable, VGA to VGA cable, Ethernet cable, Ethernet Adapter, Raspberry Pi Power cable ($30 ~ $40)
* Monitor, keyboard, mouse. (optional)
* Breadboard.

Total: $210 ~ $235. 

## <a name="time">Time Commitment</a>
* The hardware part of the project can be done within 2 ~ 3 weeks. The Gantt chart below shows the exact schedule of the project.
![GanttChart](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/schedule.png)

## <a name="bread">Breadboard Design</a>
* There are only 4 wires needed to connect the GPS Module to the Raspberry Pi
* GPSV3 Neo 6M              Raspberry Pi
* VCC               to      Pin 1 (3.3V)
* TX                to      Pin 10 (RX - GPIO15)
* RX                to      Pin 8 (TX - GPIO14)
* GND               to      Pin 6 (GND)
![Breadboard](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/breadboard.png)

## <a name="pcb">PCB Designing and Soldering</a>
* PCB Board design: Retrieve the Fritzing file in `Electric Folder/GY-NEO6MV2.fzz`, export the PCB design as Production in Gerber files format.
![PCBDesign](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/pcb.png)
* PCB Soldering
![PCBSold1](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/solder1.jpg)
![PCBSold2](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/solder2.jpg)

## <a name="power">Power Up</a>
![Power](https://github.com/benjaminle9x/Table-ClearV1/blob/master/Images%20Folder/pcbpowered.jpg)

## <a name="config">Configurating services</a>
* Install pip: `sudo apt-get install python-pip`
* Install pynmea2: `sudo pip install pynmea2`
* Install GPS software: `sudo apt-get install gpsd gpsd-clients python-gps minicom`
* Modify serial port cmdline.txt: `sudo nano /boot/cmdline.txt` and replace all the content with the following lines: ```dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles```
* Change startup settings: `sudo nano /boot/config.txt` and Add the following lines at the end of 'config.txt' file:
```
dtparam=spi=on
dtoverlay=pi3-disable-bt
core_freq=250
enable_uart=1
force_turbo=1
init_uart_baud=9600
```
* Reboot the system: `sudo reboot`
* Configure the module for the 9600 rate: `stty -F /dev/ttyAMA0 9600`
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




