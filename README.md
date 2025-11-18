# zBitx Front Panel

This is the software for the front panel of the zBitx. The current release is compatible with the current release of the zBitx daemon.

## Installation

- Download the [current release](https://github.com/dg0jde/zbitxfrontpanel/releases) (zbitx_front_panel_sw.ino.uf2)
- Turn off the zBitx (unplug the power)
- Hold down the main knob button
- Connect the mini USB port labeled “CAT” to the PC
- Release the main knob button
- The zBitx screen will turn gray and a removable drive will appear on the PC
- Copy the .u2f firmware to this drive
- The update is now complete. The USB cable can be removed.


## Creating the zBitx front panel software

I use Arduino IDE version 1.8.19 on Gentoo and Debian Linux. The process should not differ significantly on other distributions, as well as on Windows or MacOS.

- Install the Arduino IDE and start it
- Open the File/Preferences menu  
  Note the “Sketchbook location” (e.g., /home/user/Arduino)
- Enter or add the following URL under “Additional Boards Manager URLs”:  
  https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json
- Open the Tools/Board/Boards Manager menu
- Install “Raspberry Pi Pico/RP2040/RP2350”
- Select the Tools/Board/Raspberry Pi RP2040/Raspberry Pi Pico W menu
- Open the Tools/Manage Libraries menu, topic “Display”
- Install TFT_eSPI
- Close Arduino IDE
- Open Shell, change to “Sketchbook location” (```cd /home/user/Arduino```)
- ```git clone https://github.com/dg0jde/zbitxfrontpanel.git zbitx_front_panel_sw```
- In the “Sketchbook location” in the “libraries/TFT_eSPI” directory, edit the “User_Setup_Select.h” file:
- Comment out the line with “```#include <User_Setup.h>```” (precede with //)
- Below insert the following line (replace /home/user/Arduino with your own “Sketchbook location”):  
  ```#include “/home/user/Arduino/zbitx_front_panel_sw/TFT_setup.h” // Setup file for zBitx Front Panel```
- Continue in Arduino IDE
- Open the File/Sketchbook/zbitx_front_panel_sw menu
- Click “Verify” (v). After successful compilation, the .uf2 firmware file can be found at:  
  /tmp/arduino_build_xxxxxx/zbitx_front_panel_sw.ino.uf2  
  This can now be installed according to the instructions above.
- When closing the Arduino IDE, the directory with the .u2f firmware is removed.
