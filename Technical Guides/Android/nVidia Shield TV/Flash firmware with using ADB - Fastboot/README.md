# Flash nVidia Shield Android TV Pro 500gb with ADB and Fastboot

## Prerequisites
* Download latest firmware and ADB & Fastboot drivers from nVidia Developers.
* Minimum firmware version: Android 6.0.0 Marshmellow (included with Shield Experience Upgrade 3.0)

## Procedure
### Boot into bootloader / fastboot mode
#### Using ADB
If you're able to boot into the Shield and enable USB Debugging (developer menu, press repeatedly on Settings \ About \ Build Number to unlock):
* adb reboot bootloader
#### Manually
* Power down the Shield. Unplug the power.
* Insert a USB into the USB Micro port on the back of the shield, connect your computer on the other end
* Make sure HDMI is inserted, and that the TV / Monitor is on and on correct input source.
* Insert power cable WHILE holding in the power button on the Sheild Android TV unit. 
* Wait until you see bootloader mode, release power button immediatly.
* If failed: Unplug power cord and try again.


### Unlock bootloader
With nVidia Shield Android TV 500gb, the reset process after unlocking bootloader will take hours to complete. This is because the whole HDD must be formatted, even though it contains little data.
* fastboot oem unlock
* Follow instructions on the nVidia Sheild Android TV unit

### Flash the firmware
Make sure you complete flashing all the files in the same order as bellow, before attempting a reboot.
* Enter bootloader mode after bootloader unlock process is done
* fastboot flash staging blob
* fastboot flash boot boot.img
* fastboot flash recovery recovery.img
* fastboot flash system system.img
* fastboot flash vendor vendor.img
* fastboot reboot

## Troubleshoot
### Can't install drivers on Windows
Try to disable forced driver signature verification in Windows.
* [HoToGeek.com - How to disable driver signature verification on 64 bit Windows 8.1 so you can install unsigned drivers](
https://www.howtogeek.com/167723/how-to-disable-driver-signature-verification-on-64-bit-windows-8.1-so-that-you-can-install-unsigned-drivers/)
#### Disable driver signature verification on Windows 8.1 & 10
* UEFI Secure Boot = Off
* CMD as admin: "bcdedit /set testsigning on"
* Reboot
#### Enable driver signature verification on Windows 8.1 & 10
* UEFI Secure Boot = On
* CMD as admin: "bcdedit /set testsigning off"
* Reboot

## Resources
### nVidia Support
* [nVidia Shield Android TV Firmware Release Notes](https://shield.nvidia.com/support/nvidia-android-tv/release-notes/1)

### nVidia Developers
* [Recovery Images for nVidia Shield TV Pro 500gb](https://developer.nvidia.com/gameworksdownload#?search=SHIELD%20ANDROID%20TV%20Pro%20Recovery&tx=$additional,shield)
* [nVidia Shield Family USB Drivers for Windows](https://developer.nvidia.com/gameworksdownload#?search=SHIELD%20Family%20Windows%20USB)

### Google
* [Latest ADB and Fastboot tools Windows](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)
* [Latest ADB and Fastboot drivers for Windows](https://dl-ssl.google.com/android/repository/latest_usb_driver_windows.zip)
