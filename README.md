### Installation of Linux Debian v9 on Lenovo ThinkPad e531 laptop

If you'd like to start your journey with linux I personally recommend Debian - it is simple enough to get you started but also complex enough to learn you something

A complete iso image is available under [this](https://www.debian.org/CD/live/index.en.html) directory. Many graphical environments are available but I recommend gnome - it offers a lightweight apple-like interface. The other ones are cinnamon, kde, lxde, mate, xfce.

After downloading you need to "burn" your iso file somewhere - it can be either cd, dvd or pendrive. To do it you need special program - like Win32 Disk Imager for Windows or dd tool for Linux (little disclaimer - it is known that unetbootin can cause serious problems with installation process. DO NOT use this software). Then you need restart computer (but be sure your image is plugged in somewhere) and break the loading sequence (usually it means pressing one of the F buttons when BIOS screen shows up, for my ThinkPad it's F12).

The launched choice menu will contain, among many options, graphical installation of Debian Linux - choose this way. Next you will need to go through some pretty common installation process. I won't go too much into it - the only dangerous step is partitioning your disc space - you may choose either default (recommended) or custom (dangerous) partitioning. Custom partitioning is necessary for dual boot (Windows + Linux). When installator asks you about installing GRUB or LILO I recommend to choose GRUB.

If some errors occur you probably will be able to omit the step (usually caused by network drivers missing).

If you are lucky enough all of the drivers are there for you ready to launch your new system. My ThinkPad is not so smart so it requires some high tech assistance.

#### WiFi driver

First case to solve for me was to find missing wifi driver. During installation process I got an error like this
```
# cat /var/log/installer/syslog | grep rtl
Feb 22 17:22:45 check-missing-firmware: looking for firmware file rtl_nic/rtl8168e-3.fw requested by r8169
Feb 22 17:22:45 check-missing-firmware: missing firmware files (rtl_nic/rtl8168e-3.fw) for r8169
Feb 22 17:22:53 kernel: [   44.794844] r8169 0000:05:00.0: firmware: failed to load rtl_nic/rtl8168e-3.fw (-2)
Feb 22 17:22:53 kernel: [   44.794846] r8169 0000:05:00.0: Direct firmware load for rtl_nic/rtl8168e-3.fw failed with error -2
Feb 22 17:22:53 kernel: [   44.794849] r8169 0000:05:00.0 enp5s0: unable to load firmware patch rtl_nic/rtl8168e-3.fw (-2)
Feb 22 16:23:59 check-missing-firmware: looking for firmware file rtl_nic/rtl8168e-3.fw requested by r8169
Feb 22 16:23:59 check-missing-firmware: missing firmware files (rtl_nic/rtl8168e-3.fw) for r8169
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8107e-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8107e-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168h-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168h-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8402-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-3.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-1.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169^M
Feb 22 16:34:47 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169^M
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8107e-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8107e-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168h-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168h-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8402-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-3.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-1.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-2.fw for module r8169
Feb 22 16:35:00 in-target: W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169
```
Because we want to download commercial software we need to add the following entry to /ect/apt/sources.list file (su required)

Then we can run:
```
# apt-get update
# apt-get install realtek-firmware
# apt-get update && apt-get upgrade && apt-get dist-upgrade -y
```
Then we install linux headers and broadcom WiFi driver software:
```
# apt-get install linux-headers-`uname -r`
# apt-get install broadcom-sta-dkms

You should have fully functional WiFi now (available in top right menu).

#### Bluetooth driver

After reboot probably some red text has occured on bootlog - this means you don't have bluetooth driver.
```
# dmesg | egrep -i 'blue|firm'
[    0.136396] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   14.965277] Bluetooth: Core ver 2.21
[   14.965287] Bluetooth: HCI device and connection manager initialized
[   14.965290] Bluetooth: HCI socket layer initialized
[   14.965292] Bluetooth: L2CAP socket layer initialized
[   14.965296] Bluetooth: SCO socket layer initialized
[   17.337137] Bluetooth: hci0 command 0x1001 tx timeout
[   25.333133] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[   25.337211] Bluetooth: hci0: BCM: chip id 70
[   25.353237] Bluetooth: hci0: mint
[   25.353240] Bluetooth: hci0: BCM (001.001.011) build 0000
[   26.277585] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   26.277589] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   26.446564] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.446566] Bluetooth: BNEP filters: protocol multicast
[   26.446568] Bluetooth: BNEP socket layer initialized
```
This line means the system did not find driver file for bluetooth:
```
[   26.277585] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
```
**<span style="color:red">Now a BIG disclaimer - what is described further violates actually ALL security rules that should be applied while using and administering Linux system. The decision whether you run those commands is only up to you. I can only say that this solved my problem.
</span>**

For bluetooth driver installation you will need to go to [this](https://github.com/winterheart/broadcom-bt-firmware/tree/master/brcm) website


Download file BCM43142A0-0a5c-21d7.hcd and then copy to /lib/firmware/brcm/BCM.hcd
```
# wget https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM43142A0-0a5c-21d7.hcd
# mkdir -p /lib/firmware/brcm
# cp BCM43142A0-0a5c-21d7.hcd /lib/firmware/brcm/BCM.hcd
```
After that run:
```
# sudo modprobe -r btusb
# rfkill unblock bluetooth
# reboot
```
You should have working bluetooth driver installed (also available in top right).
