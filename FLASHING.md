# Flashing the Corne halves

This repository builds firmware for the **Eyelash Peripherals Corne** with a `nice_nano_v2` controller on each half. The controller's UF2 bootloader temporarily appears as a USB drive, so you can flash firmware by copying a file to it. You do not need to change the keyboard firmware to enable this.

## Get the firmware

1. Open this repository on GitHub and go to **Actions**.
2. Open a successful firmware build and download its firmware artifact.
3. Unzip the download. The build includes separate firmware for the left and right halves. Use the matching `.uf2` file for each half; do not use the `settings_reset` firmware for normal flashing.

## Flash each half

1. Connect one half to your computer by USB.
2. Quickly double-tap the reset button on that half. It should appear as a USB drive, often named `NICENANO` (the name may vary).
3. Copy the matching `.uf2` file onto that drive. 
4. Wait for the drive to disappear automatically and the half to restart.
5. Disconnect it, then repeat with the other half and its matching firmware.

Flash the **left** firmware to the left half and the **right** firmware to the right half. Each half has its own controller and must be flashed separately.

## If the drive does not appear

- Make sure you are double-tapping the reset button, rather than holding it down.
- This keyboard can enter deep sleep when **Q, S, and Z** are held together for two seconds. If that happened, press reset once to wake it, then double-tap reset to enter the bootloader.
- Try another USB cable or port; some USB cables only provide power and cannot transfer data.
