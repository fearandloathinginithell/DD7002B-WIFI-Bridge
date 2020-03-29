# DD7002B-WIFI-Bridge
## Requirements
DD7002B WIFI Bridge

EZSync010 [amazon affiliate link](https://www.amazon.com/gp/product/B010KJSCR8/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B010KJSCR8&linkCode=as2&tag=fearandloa051-20&linkId=ba84822693d1dd483c71e3913e287d01)
or other RS485 bridge


![EZSync010](https://github.com/fearandloathinginithell/DD7002B-WIFI-Bridge/blob/master/EZSync010.jpg)

## Drivers
### macOS Catalina
No additional drivers required
### Windows 10 1909
Drivers for chipset https://www.ftdichip.com/FTDrivers.htm

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
Query Bridge
```Shell
!123D000v?;
```
Response
```Shell
!123D001vZ10;!123D002vZ10;!123D003vU10;!123DFFFv000;
`
| Value  | Description |
| ------------- | ------------- |
| !123D001vZ10  | Dining Room 1, One Way Blind |
| !123D002vZ10  | Dining Room 2, One Way Blind |
| !123D003vU10  | Kitchen Blind, Two Way Blind |
