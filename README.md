# msm8916
Qualcomm MSM8916 LTE 4G WiFi Dongle (UZ801)

## Images
![MSM8916 Dongle](img/4g-01.png?raw=true "MSM8916 Dongle")
![MSM8916 Dongle](img/4g-02.png?raw=true "MSM8916 Dongle")
![MSM8916 Dongle](img/4g-03.png?raw=true "MSM8916 Dongle")
![MSM8916 Dongle](img/4g-04.png?raw=true "MSM8916 Dongle")
![MSM8916 Dongle](img/4g-05.png?raw=true "MSM8916 Dongle")

# Labeling
On the cover:
```
4G LTE WIFI MODEM

LTE 4G WIFI Dongle
SSID: 4G-UFI-XX
WIFI KEY: 1234567890
Router IP: 192.168.100.1
Login Password: admin
DL: 150Mbps UL: 50Mbps
```

Under the cover:
```
SSID: 4G-UFI-D34
WIFI KEY: 1234567890
IP: 192.168.100.1
Password: admin
IMEI: 86399306XXXXXXX
```

On the motherboard:
```
FY_UZ801_V2.1
410-06K015062A
G124-2112-0036
801-4G
```

## dmesg
```
usb 1-4: new high-speed USB device number 8 using xhci_hcd
usb 1-4: New USB device found, idVendor=05c6, idProduct=90b6, bcdDevice=ff.ff
usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-4: Product: Android
usb 1-4: Manufacturer: Android
usb 1-4: SerialNumber: 0123456789ABCDEF
usbcore: registered new interface driver cdc_ether
rndis_host 1-4:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-4, RNDIS device, 66:d6:13:4a:9f:5d
usbcore: registered new interface driver rndis_host

```
## lsusb
```
# lsusb -s 001:008
Bus 001 Device 008: ID 05c6:90b6 Qualcomm, Inc. Android

# lsusb -s 001:008 -v

Bus 001 Device 008: ID 05c6:90b6 Qualcomm, Inc. Android
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05c6 Qualcomm, Inc.
  idProduct          0x90b6 
  bcdDevice           ff.ff
  iManufacturer           1 Android
  iProduct                2 Android
  iSerial                 3 0123456789ABCDEF
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x00aa
    bNumInterfaces          5
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass        224 Wireless
      bFunctionSubClass       1 Radio Frequency
      bFunctionProtocol       3 RNDIS
      iFunction               7 RNDIS
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      3 RNDIS
      iInterface              5 RNDIS Communications Control
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 01 00 01
      ** UNRECOGNIZED:  04 24 02 00
      ** UNRECOGNIZED:  05 24 06 00 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              6 RNDIS Ethernet Data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 01 00 00
      ** UNRECOGNIZED:  04 24 02 02
      ** UNRECOGNIZED:  05 24 06 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               9
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     66 
      bInterfaceProtocol      1 
      iInterface              4 ADB Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```

## Web Interface
![MSM8916 Dongle](img/www01.png?raw=true "MSM8916 Dongle")
---
![MSM8916 Dongle](img/www02.png?raw=true "MSM8916 Dongle")
---
![MSM8916 Dongle](img/www03.png?raw=true "MSM8916 Dongle")
---

## adb
```
$ adb devices
List of devices attached
0123456789ABCDEF        device
```

If not, in web interface, after entering admin credentials, go to this url:
http://192.168.100.1/usbdebug.html

```
$ adb shell id
uid=0(root) gid=0(root) context=u:r:shell:s0

```

The most relevant device info lines from getprop
```
$ adb shell getprop
...
[ro.build.description]: [msm8916_32_512-userdebug 4.4.4 KTU84P eng..20220715 test-keys]
[ro.build.display.id]: [V3.4.3]
[ro.build.fingerprint]: [qcom/msm8916_32_512/msm8916_32_512:4.4.4/KTU84P/eng..20220715:userdebug/test-keys]
[ro.build.host]: [be7be4acc41b]
[ro.build.id]: [UZ801]
[ro.build.product]: [msm8916_32_512]
[ro.build.version.release]: [4.4.4]
[ro.build.version.sdk]: [19]
[ro.product.board]: [ALK]
[ro.product.brand]: [qcom]
[ro.product.cpu.abi2]: [armeabi]
[ro.product.cpu.abi]: [armeabi-v7a]
[ro.product.device]: [msm8916_32_512]
[ro.product.manufacturer]: [Qualcomm Technology]
[ro.product.model]: [UZ801]
[ro.product.name]: [msm8916_32_512]

```

## Featuring
- [hackaday](https://hackaday.com/2022/08/03/hackable-20-modem-combines-lte-and-pi-zero-w2-power/)
- [openwrt forum](https://forum.openwrt.org/t/uf896-qualcomm-msm8916-lte-router-384mib-ram-2-4gib-flash-android-openwrt/131712)
- [4pda](https://4pda.to/forum/index.php?showtopic=849043)
- [blinkenlights](https://www.blinkenlights.ch/ccms/posts/aliexpress-lte-1/)
- [extrowerk](https://extrowerk.com/2022/07/31/OpenStick/)
