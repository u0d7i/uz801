# UZ801
Qualcomm MSM8916 LTE 4G WiFi Dongle

## Images
| ![i1](img/4g-01.png?raw=true) | ![i4](img/4g-04.png?raw=true) |
|-------------------------------|-------------------------------|
| ![i2](img/4g-02.png?raw=true) | ![i5](img/4g-05.png?raw=true) |
| ![i3](img/4g-03.png?raw=true) |                               |

## Labeling
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
```
[verbose lsusb output](lsusb.txt)

## Web Interface

| ![w](img/www01.png?raw=true) |                              |
|------------------------------|------------------------------|
| ![w](img/www02.png?raw=true) | ![w](img/www03.png?raw=true) |

## EDL

Device can enter [EDL](https://en.wikipedia.org/wiki/Qualcomm_EDL_mode) mode by short cutting D+ to GND on USB,
and releasing after plug-in.  The easiest way to do so is via [DIY EDL cable](https://wiki.bananahackers.net/development/edl/diy-edl-cable).

Dmesg in EDL mode:

```
usb 1-8: New USB device found, idVendor=05c6, idProduct=9008, bcdDevice= 0.00
usb 1-8: New USB device strings: Mfr=0, Product=2, SerialNumber=0
usb 1-8: Product: QHSUSB__BULK

```
lsusb in EDL mode:
```
Bus 001 Device 015: ID 05c6:9008 Qualcomm, Inc. Gobi Wireless Modem (QDL mode)
```

[Standard edl client](https://github.com/bkerler/edl) works out of the box without the need of specifiing loader manually:
```
$ edl
Qualcomm Sahara / Firehose Client V3.53 (c) B.Kerler 2018-2021.
main - Trying with no loader given ...
main - Waiting for the device
main - Device detected :)
main - Mode detected: firehose
firehose - Nop succeeded.
firehose - No supported functions detected, configuring qc generic commands
firehose - 
firehose_client
firehose_client - [LIB]: No --memory option set, we assume "eMMC" as default ..., if it fails, try using "--memory" with "UFS","NAND" or "spinor" instead !
firehose - TargetName=MSM8916
firehose - MemoryName=eMMC
firehose - Version=1
firehose_client - Supported functions:
-----------------
configure,program,firmwarewrite,patch,setbootablestoragedrive,ufs,emmc,power,benchmark,read,getstorageinfo,getcrc16digest,getsha256digest,erase,peek,poke,nop,xml

```

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

## screenshots
Despite device is is lacking screen, you can still view what supposed to be on it.

Check current screen off timeout value:
```
$ adb shell settings get system screen_off_timeout
60000
```
It's 60000 milliseconds = 1 minute, meaning if we try doing screenshot in 1 minute
we will get blank screen. Let's change it.
```
$ adb shell dumpsys power | grep OffTimeout
  mScreenOffTimeoutSetting=60000
  mMaximumScreenOffTimeoutFromDeviceAdmin=2147483647 (enforced=false)
$ adb shell settings put system screen_off_timeout 2147483647
$ adb shell settings get system screen_off_timeout
2147483647

```
Wake the screen by pressing Power Button
```
$ adb shell input keyevent 26
```

Make a screenshot, and download it:
```
$ adb shell screencap /sdcard/Download/screen01.png
$ adb pull /sdcard/Download/screen01.png
```

I'm not good at Mandarin, so, need to do something about it
```
$ adb shell "setprop persist.sys.locale en-US; setprop ctl.restart zygote"
```

Tap the screen to remove the warning:
```
$ adb shell input tap 100 100
```

| ![s1](img/screen01.png?raw=true) | ![s2](img/screen02.png?raw=true) | ![s3](img/screen03.png?raw=true) |
|----------------------------------|----------------------------------|----------------------------------|

Rin some apps and see the output:
```
$ adb shell am start -n 'com.android.settings/.deviceinfo.Status'
Starting: Intent { cmp=com.android.settings/.deviceinfo.Status }

$ adb shell screencap /sdcard/Download/screen04.png
$ adb pull /sdcard/Download/screen04.png
```
Some other commands to try:
```
com.android.settings/.RadioInfo
com.android.settings/.BatteryInfo
```
Use dumpsys to get candidate activities list in the app:
```
$ adb shell dumpsys package com.android.settings | grep com.android.settings/
```
P.S. [scrcpy](https://github.com/Genymobile/scrcpy) is not supported on this device (requires API 21 / Android 5.0).


## Featuring
- [hackaday](https://hackaday.com/2022/08/03/hackable-20-modem-combines-lte-and-pi-zero-w2-power/)
- [openwrt forum](https://forum.openwrt.org/t/uf896-qualcomm-msm8916-lte-router-384mib-ram-2-4gib-flash-android-openwrt/131712)
- [4pda](https://4pda.to/forum/index.php?showtopic=849043)
- [blinkenlights](https://www.blinkenlights.ch/ccms/posts/aliexpress-lte-1/)
- [extrowerk](https://extrowerk.com/2022/07/31/OpenStick/)
