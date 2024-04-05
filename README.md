
# Shelly convert to Tasmota
This guide explains how to convert Shelly ESP32 and ESP32-C3 driven devices to Tasmota (no other firmware!)

## :warning: **There is no way back to Shelly firmware if you have initiated the convert process!**

The convert workflow provides a safe update. However, it is a risky operation to overwrite the bootloader. If something unexpected happens, it will probably render the device inoperable until it is recovered.
To recover a failed convert, flashing Tasmota over a wired serial connection is needed.

## Prerequisites

1. ⚠️ Needed ⚠️ Update the device to the latest **stable** firmware (Internet access!!)
2. Download the name corresponding zip package for your device (See [release section](https://github.com/tasmota/mgos32-to-tasmota32/releases))

## Let’s start

### Replace Shelly with Tasmota32 firmware

1. Connect to your Shelly device via Wi-Fi or LAN
2. Navigate to Settings > Firmware and drag & drop the convert "zip" in the firmware update area (do **NOT** update via URL)
3. Click the **Update** button
4. Device is updating, finished in 1-2 minutes
5. If Shelly Web frontend is back after the update, repeat the steps above.
6. The Web frontend does not react anymore now.
7. Connect to the newly opened Tasmota Wi-Fi access point and add the device to your Wi-Fi (**full Internet access needed**). 
### ⚠️ NEEDED ⚠️ Convert to Tasmota Safeboot and update to latest Tasmota release
8. Configure the device using Tasmota Auto configuration. (Configuration > Auto-configuration > Select new auto-configuration) Select your device and hit enter. **This replaces the locked bootloader** (without this step device gets bricked with the next firmware update).
9. Wait until the device is online again. Takes 1-2 minutes
11. Under consoles, open the Partition Wizard and start the Safeboot Conversion by hitting the button "Start Migration". The conversion will update to the latest Tasmota version too.
12. Wait until the device is online again. Takes 1-2 minutes
13. Optional: Use Partition Wizard to increase the Filesystem size to its maximum. This removes all obsolete files too.

## Supported Devices

| **Device** | **State** |
|------|------|
| **PlusHT** |   :warning:**untested**   |
| **PlusPlugS** |   :white_check_mark:**tested**   |
| **PlusPlugUK** |   :white_check_mark:**tested**   |
| **PlusPlugIT** |   :warning:**untested**   |
| **PlusPlugUS** |   :white_check_mark:**tested**  |
| **PlusI4** |   :white_check_mark:**tested**   |
| **PlusWallDimmer** |   :warning:**untested**   |
| **Plus1PM** |   :white_check_mark:**tested**   |
| **Plus1**   |   :white_check_mark:**tested**   |
| **Plus2PM** |   :white_check_mark:**tested**   |
| **Pro1**   |   :white_check_mark:**tested**   |
| **Pro1PM** |   :white_check_mark:**tested**   |
| **Pro2**   |   :white_check_mark:**tested**   |
| **Pro2PM** |   :white_check_mark:**tested**   |
| **Pro3**   |   :warning:**untested**   |
| **Pro4PM** |   :white_check_mark:**tested**   |
| **Pro3EM** |   :warning:**untested**   |
| **Plus1PMMini**  |   :white_check_mark:**tested**   |
| **Plus1Mini**    |   :white_check_mark:**tested**   |
| **PlusPMMini**   |   :white_check_mark:**tested**   |
| **Plus10V**   |   :white_check_mark:**tested**   |
| **Mini1PMG3**  |   :white_check_mark:**tested** |
| **Mini1G3**    |   :white_check_mark:**tested** |
| **MiniPMG3**   |   :white_check_mark:**tested** |

##### Pro4PM is build with LVGL support

### If you confirmed an **untested** device working please open an issue!

## What if my device is not listed?

If your Shelly device is not listed, please open an issue with a link to the Shelly Knowledge Base.

Or buy the device from my [Amazon Wishlist](https://www.amazon.de/hz/wishlist/ls/2ZS2NBA6PPEDD) and I will reverse engineer and confirm the device working.

## Credits

I would like to thank [Jason2866](https://github.com/Jason2866) for providing help with the custom Tasmota files and [s-hadinger](https://github.com/s-hadinger) for the Berry code fixing startup of Tasmota.

## License

This repository is released under the GNU General Public License v3.0. Refer to the [LICENSE](LICENSE) file for more information. 

Copyright (C) 2023 Philipp '3D' ten Brink 
