# RobotDyn CP2104 UART USB To TTL 3.3V 5V Serial Adapter
# =====================================================
Bought Apr2018.

https://www.aliexpress.com/item/CP2104-USB-TTL-UART-Serial-adapter-microcontroller-5V-3-3V-Micro-USB/32808495412.html

https://robotdyn.com/usb-serial-adapter-microcontroller-cp2104-5v-3-3v-digital-i-o-micro-usb.html

## Usages
1. As an UART Logger for ESP32 dev boards (typically when it is battery-only powered so no USB line is connected to the ESP32 dev board).
2. To hook up UART devices, such as the u-blox NEOM8N GPS Board, directly to the PC.

## USB Type of the connector: Micro-USB.

## Three pads for setting Voltage 3.3V/5V:
@doc This board uses 5V SIGNAL LEVELS by default.

@doc This board needs a soldering job before it can be used (to switch the default 5V mode to 3.3V else your MCU will blow up).

0. Look at the pictures.
1. Cut the trace between the two pads closest to the corner of the board (back of the board, label "5V").
2. Solder connect the two pads furthest away from the corner of the board (back of the board, label "3.3V").
    
## PIN LAYOUT
```
    (front side of the board)
    1 DTR *not used*
    2 3V3 *not used, when the board is used in combination an ESP32 dev board*
    3 5V  *not used*
    4 TXD
    5 RXD
    6 GND
```

## ***Wiring Instructions: using the board as an UART Logger in combination with an ESP32 dev board:
```
- [Do not connect voltage pins!]
- pin 4 TXD -> devboard pin UART RX
- pin 5 RXD -> devboard pin UART TX
- pin 6 GND -> devboard pin GND
```

## UART Chip: Silicon Labs CP2104
[OK. This is a high-quality USB UART chip.]

https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers

# Install Driver "Silicon Labs CP210x_Windows_Drivers v6.7.5 [Sep2017]"
- @important The standard Windows Update driver version DOES NOT WORK.
- @important The latest Silicon Labs CP210x_Universal_Windows_Driver v10.1.1 [Nov2017] also DOES NOT WORK.
- @important RESTART the computer after installing the driver

# MS Windows Port COMx: Device Manager: set baud speed = 115200
	
## Config Instructions:
- The baud speed used on the UART board must be the same as the baudspeed configuration of the ESP32 MCU (typically 115200).
- The baud speed used on the UART board must be the same as the baudspeed configured in the terminal programme (MobaXterm) (typically 115200).

## FAQ
- This USB Bus Powered device gets its power from the USB bus (not from the exposed VCC pin - which is outgoing only!).
- Working voltage: 3.3V - 5V. The board contains a voltage regulator.
- Speeds 921600, 115200 and 9600 certainly work.
- OK CHECKED that when the jumper is set to 3.3V then the RX TX pins are also using 3.3V (not 5V) so it is safe for an ESP32.

## ISSUES
- The board is by default configured for 5V. You have to resolder the pads for 3.3V (see earlier).
- Disable the Microsoft Serial Mouse device (it often conflicts with Silicon Labs drivers for the CP2XX chips!)  \
	    http://www.taltech.com/support/entry/windows_2000_nt_serial_mice_and_missing_com_port
