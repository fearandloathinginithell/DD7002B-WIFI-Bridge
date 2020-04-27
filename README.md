# DD7002B WIFI Bridge
## Requirements
DD7002B WIFI Bridge firmware 0.8.0

EZSync010 [amazon affiliate link](https://www.amazon.com/gp/product/B010KJSCR8/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B010KJSCR8&linkCode=as2&tag=fearandloa051-20&linkId=ba84822693d1dd483c71e3913e287d01)
or other RS485 bridge


![EZSync010](https://github.com/fearandloathinginithell/DD7002B-WIFI-Bridge/blob/master/EZSync010.jpg)

## Drivers
### macOS Catalina
No additional drivers required
### Windows 10 1909
Drivers for chipset https://www.ftdichip.com/FTDrivers.htm

### Raspberry Pi
No additional drivers required

## Connecting to Bridge Raspberry Pi
Install Screen if required
```Shell
sudo apt-get install screen
```
```Shell
screen /dev/ttyUSB0 9600
```
## Connecting to Bridge macOS Catalina
List USB devices to retreive the name of the EZSync010

```Shell
ls /dev/tty.*
/dev/tty.Bluetooth-Incoming-Port	/dev/tty.usbserial-AB0KFHEJ
```
Connect to EZSync010 and specify the baud rate
```Shell
screen /dev/tty.usbserial-AB0KFHEJ 9600
```
## Issue Commands
### Query Bridge
```Shell
!123D000v?;
```
#### Response
```Shell
!123D001vZ10;!123D002vZ10;!123D003vU10;!123DFFFv000;
```
## Blind information
| Value  | Description |
| ------------- | ------------- |
| !123D001vZ10  | Dining Room 1, One Way Blind |
| !123D002vZ10  | Dining Room 2, One Way Blind |
| !123D003vU10  | Kitchen Blind, Two Way Blind |
| !123DFFFv000  | Unknown |

## Home Assistant
Working Home Assistant configuration
###
```
switch:
  platform: command_line
  switches:
    blind_dining_nw:
      command_on: '/bin/bash -c "( stty raw speed 9600 >&2; echo -ne ''!123D001o;'' ) >/dev/ttyUSB0 <&1"'
      command_off: '/bin/bash -c "( stty raw speed 9600 >&2; echo -ne ''!123D001c;'' ) >/dev/ttyUSB0 <&1"'
      friendly_name: Blind Dining North West
    blind_dining_n:
      command_on: '/bin/bash -c "( stty raw speed 9600 >&2; echo -ne ''!123D002o;'' ) >/dev/ttyUSB0 <&1"'
      command_off: '/bin/bash -c "( stty raw speed 9600 >&2; echo -ne ''!123D002c;'' ) >/dev/ttyUSB0 <&1"'
      friendly_name: Blind Dining North
    blind_kitchen:
      command_on: '/bin/bash -c "( stty raw speed 9600 >&2; echo -ne ''!123D003o;'' ) >/dev/ttyUSB0 <&1"'
      command_off: '/bin/bash -c "( stty raw speed 9600 >&2; echo -ne ''!123D003c;'' ) >/dev/ttyUSB0 <&1"'
      friendly_name: Blind Kitchen
```
### customize_glob.yaml
```
switch.blind_*:
  icon: mdi:blinds
```

## Issues
###
Current command line solution does not allow for blind feed back from two way blinds i.e. Kitchen
### Issuing commands to the two way blind just returns possition
This issue was resolved with bridge firmware 0.8.0
