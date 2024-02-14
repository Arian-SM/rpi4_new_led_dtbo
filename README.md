# Your First dtb Overlay With Raspberry Pi 4

## Compile on the Target
Compile using the following command:
```bash
dtc -@ -I dts -O dtb -o led-overlay.dtbo led-overlay.dts
```
Copy the ouptut .dtbo to the `/boot/overlay` directory:
```bash
cp led-overlay.dtbo /boot/overlays/
```
Change `config.txt` to load the dtbo by its name on boot time:
```bash
eho "dtoverlay=led-overlay" >> /boot/config.txt
```

reboot the system, once it up you could see the `new_led` is added under the `/sys/class/leds/` directory.

examine this little project by turnning the led on and off using the following commands:
```bash
echo 1 > /sys/class/leds/new_led/brightness // Turnning GPIO 18 on
echo 0 > /sys/class/leds/new_led/brightness // Turnning GPIO 18 off
```
## TODO
Following sections should be added:
1. Introduction
2. Compile on the Host
3. Loading dynamically using `dtoverlay`
