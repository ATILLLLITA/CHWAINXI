# CHWAINXI

**Chuwi hi8 Manjaro linux wifi/bt/touchscreen work.**
**Clone my git**

git clone https://github.com/ATILLLLITA/CHWAINXI.git

**Touchscreen driver copy.**

sudo cp silead_ts.fw /lib/firmware/
**Broadcom (BT/Wi-Fi) driver copy.**

sudo cp -n /brcmfmac43430a0-sdio.bin /lib/firmware/brcm

sudo cp -n /brcmfmac43430a0-sdio.Insyde-BayTrail.txt /lib/firmware/brcm

sudo cp -n /brcmfmac43430a0-sdio.txt /lib/firmware/brcm

sudo cp -n /BCM4343A0.hcd /lib/firmware/brcm

**Kernel module for get touchscreen work install**

git clone https://github.com/onitake/gslx680-acpi.git

cd gslx680-acpi

make

sudo cp gslx680_ts_acpi.ko /lib/modules/$(uname -r)/kernel/drivers/

sudo insmod ./gslx680_ts_acpi.ko

**Calibrator for touchscreen install**

sudo apt-get install xinput_calibrator

xinput_calibrator

**plase result into**

sudo atom /etc/X11/xorg.conf.d/99-calibration.conf
