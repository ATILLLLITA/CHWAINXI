# CHWAINXI
**CHUWI HI8**

Hardware Information |  |  |
---|---|---
Touchscreen controller | gslx680 | Work
Touchscreen  | | Work
Audio | Realtek ALC5642 | Work
WIFI | Broadcom BCM43430 | Work
Bluetooth | Realtek RGN RTL8723BS | Work
Gyro Sensor | Bosch BMG160 | Work

**Chuwi hi8 Manjaro linux wifi/bt/touchscreen work.**
**Clone my git**
```
git clone https://github.com/ATILLLLITA/CHWAINXI.git
```
**Touchscreen firmware copy.**
```
sudo cp silead_ts.fw /lib/firmware/
```
**Broadcom (BT/Wi-Fi) firmware copy.**
```
sudo cp -n /brcmfmac43430a0-sdio.bin /lib/firmware/brcm
sudo cp -n /brcmfmac43430a0-sdio.Insyde-BayTrail.txt /lib/firmware/brcm
sudo cp -n /brcmfmac43430a0-sdio.txt /lib/firmware/brcm
sudo cp -n /BCM4343A0.hcd /lib/firmware/brcm
```
**Kernel module for get touchscreen work install**

**blacklist old driver and unload**
```
echo "blacklist silead" | sudo tee /etc/modprobe.d/blacklist-silead.conf
sudo rmmod silead
```
**install new driver**
```
pacman -Syu git make gcc dkms
cd gslx680-acpi-master
MODULE_VER=$(grep VERSION dkms.conf |  awk -F '"' '{print $2}')
sudo mkdir /usr/src/gslx680-acpi-$MODULE_VER
sudo cp -r * /usr/src/gslx680-acpi-$MODULE_VER/
sudo dkms add gslx680-acpi/$MODULE_VER
sudo dkms install gslx680-acpi/$MODULE_VER
```
**check touchscreen**
```
sudo modprobe gslx680_ts_acpi
```
**Calibrator for touchscreen install**
```
sudo apt-get install xinput_calibrator
xinput_calibrator
```
**plase result into**
```
sudo atom /etc/X11/xorg.conf.d/99-calibration.conf
```
