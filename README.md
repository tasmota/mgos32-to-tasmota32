# Updating Shelly Firmware from Mongoose OS to Tasmota

This guide is designed to help users of Shelly Plus and Pro ESP32 devices to update their devices from the Mongoose OS firmware to the Tasmota firmware over the air (OTA).

## WARNING :warning:

This application provides generally safe updates to devices over the air (OTA). 

However, it is important to understand that overwriting the boot loader via an OTA update is a risky operation. If something unexpected fails during the update, it may render the device inoperable until serial flash.

If this happens, you need to know how to flash a new firmware over a wired connection in order to recover the device.

## Prerequisites

1. Your Shelly device must have Mongoose OS firmware version 0.12.0 or higher installed.
2. You must have the mgos32-to-tasmota32 firmware http link for your device copied from the table below.

## Process

### Conversion

1. Connect your Shelly device to your local wifi or LAN with an internet connection.
2. Navigate to Settings > Device Settings > Firmware > Custom Firmware and paste the previously prepared http link. 
3. Click the **Upload Firmware** button.
4. Wait for the device to finish updating.
5. Once the update is finished, connect to the device's new Tasmota wifi access point and add the device back to your network. If Shelly OS (Mongoose OS) boots back up after the OTA update, please update (using the OTA link from this repo) again.
6. Now you can configure your device. You can find templates for your device [here](https://templates.blakadder.com/search.html).
7. If you want to use the Shelly factory calibration data follow the next steps. If not you can delete `Shelly_data.be` and `Shelly_data.tapp` from the file system which speeds up (re)boot times.

### Optional: Use factory calibration data

1. Check that the files `shelly.bin` and `aux.bin` have been generated in the file system (FS). If not, type `import Shelly_data` into the Berry Console and hit Return twice. This will save the device-specific data in these two files.
2. Download `shelly.bin` and `aux.bin` in the file system to your PC.
3. Find calibration data in `shelly.bin` around 0x1000 with a HEX viewer for your OS.
4. Delete `Shelly_data.be` and `Shelly_data.tapp` from the file system

### Optional: Convert to Tasmota Safeboot 

1. ***MANDATORY*** Download **ALL** files in the file system to your PC.
2. Open the Partition Wizard -> Menu Entry. Choose **Increase FS to max** and click the corresponding button. This will increase the FS and erase anything that is currently present in it. If option is not available, continue
3. Upload the in Step 1. downloaded `Partiton_wizard.tapp` and `Partitions_update.be` to the Tasmota FS if not already there. Inside the Berry Console, type `import Partitions_update` and hit Return twice. Afterwards, restart the device.
4. Upload the in Step 1. downloaded `Partiton_wizard.tapp` to the Tasmota FS. Restart.
5. Open the Partition Wizard and start the Safeboot Conversion process. If it is not possible to start due to something is marked in red, then an OTA Tasmota upgrade is needed. Perform the upgrade, and the Safeboot Conversion process can then be started.
6. The size of the Partition FS is now larger than the default size. If desired, the default 320kB size can be restored using the Partition Wizard.
7. Finally, configure device using [templates here](https://templates.blakadder.com/search.html).

## Supported Devices and OTA Links

| **Device** | **Link** | **State** |
|------|------|------|
| **PlusHT** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-PlusHT.zip`   |   :warning:**untested**   |
| **PlusPlugS** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-PlusPlugS.zip`   |   :white_check_mark:**tested**   |
| **PlusPlugIT** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-PlusPlugIT.zip`   |   :warning:**untested**   |
| **PlusPlugUS** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-PlusPlugUS.zip`   |   :warning:**untested**   |
| **PlusPlugUK** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-PlusPlugUK.zip`   |   :warning:**untested**   |
| **PlusI4** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-PlusI4.zip`   |   :white_check_mark:**tested**   |
| **PlusWallDimmer** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-PlusWallDimmer.zip`   |   :warning:**untested**   |
| **Plus1PM** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Plus1PM.zip`   |   :white_check_mark:**tested**   |
| **Plus1** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Plus1.zip`   |   :white_check_mark:**tested**   |
| **Plus2PM** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Plus2PM.zip`   |   :white_check_mark:**tested**   |
| **Pro1** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Pro1.zip`   |   :white_check_mark:**tested**   |
| **Pro1PM** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Pro1PM.zip`   |   :white_check_mark:**tested**   |
| **Pro2** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Pro2.zip`   |   :warning:**untested**   |
| **Pro2PM** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Pro2PM.zip`   |   :white_check_mark:**tested**   |
| **Pro3** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Pro3.zip`   |   :warning:**untested**   |
| **Pro4PM** |   `http://ota.tasmota.com/tasmota32/shelly/mgos32-to-tasmota32-Pro4PM.zip`   |   :white_check_mark:**tested**   |

##### Pro4PM is build with LVGL support

### If you confirmed an **untested** device working please open an issue!

## What if my device is not listed?

If your Shelly device is not listed in the templates, please open an issue with a link to the Shelly Knowledge Base.

Or buy the device from my [Amazon Wishlist](https://www.amazon.de/hz/wishlist/ls/2ZS2NBA6PPEDD) and I will reverse engineer and confirm the device working.

## Credits

I would like to thank [Jason2866](https://github.com/Jason2866) for providing help with the custom Tasmota files.

## License

This repository is released under the GNU General Public License v3.0. Refer to the [LICENSE](LICENSE) file for more information. 

Copyright (C) 2023 Philipp '3D' ten Brink 
