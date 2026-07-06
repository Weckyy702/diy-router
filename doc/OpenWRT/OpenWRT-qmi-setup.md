## Check for QMI modem
Check if a device has been recognized as /dev/cdc-wdm0:
```
ls /dev/cdc*
cdc-wdm0
``` 

Check if the device is detected:
```
cat /sys/kernel/debug/usb/devices
```

If the device is already in QMI mode you can proceed with
the installation of the kernel module.

## Install USB QMI Kernel module
```
apk update
apk install kmod-usb-net-qmi-wwan uqmi luci-proto-qmi
```

Reboot the device, so everything gets loaded.

## Setup the OpenWRT interface LuCI: 
Go to "Interfaces"
Click on "Add"
Select "Protocol" -> "QMI Cellular"
Add "Device" -> "wwan0" or "/dev/cdc-wmd0"
Set "Firewall Settings" to "wan"

### For Aldi Talk only
APN = "internet.eplus.de"
Authentication Type = "PAP"
username = "eplus"
password = "internet"
And don't forget your SIM pin if one is set. 
