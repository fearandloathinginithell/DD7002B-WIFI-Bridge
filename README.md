# DD7002B-WIFI-Bridge
## Requirements
DD7002B WIFI Bridge

EZSync010 [amazon affiliate link](https://www.amazon.com/gp/product/B010KJSCR8/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B010KJSCR8&linkCode=as2&tag=fearandloa051-20&linkId=ba84822693d1dd483c71e3913e287d01)
or other RS485 bridge


![EZSync010](https://github.com/fearandloathinginithell/DD7002B-WIFI-Bridge/blob/master/EZSync010.jpg)

## Connecting to Bridge
List USB devices to retreive the name of the EZSync010

```Shell
ls /dev/tty.*
/dev/tty.Bluetooth-Incoming-Port	/dev/tty.usbserial-AB0KFHEJ
```
Connect to EZSync010 and specify the baud rate
```Shell
screen /dev/tty.usbserial-AB0KFHEJ 9600
```
