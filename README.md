# ESP-IDF MJD Ublox NEO-M8N GPS component
This is component based on ESP-IDF for ESP32.

## Example ESP-IDF project
my_neom8n_gps_using_lib

## Shop Product.
Ublox NEO-M8N GPS Module with Shell.

## CHIP SYSINFO for this specific GPS Board
- The system software runs from ROM (opposed to from Flash). The module contains no Flash so firmware upgrades are not possible (which is OKAY as the ROM contains a recent version V3.x).
- The board supports UBX Protocol Version 18.00 (a recent version).
- Dumping Message UBX->MON->VER:

```
	swver: ROM CORE 3.01 (107888)
	hwver: 00080000
	ext:    
	    PROTVER=18.00
	    FWVER=SGP 3.01
```

## Tool u-center V8.29 from ublox:
- @download https://www.u-blox.com/en/product/u-center-windows
- Purpose: to test and configure the device.
- Use an FTDI USB-UART board to connect the GPS Board to the computer.
- Set baudrate = 9600 in the Ublox software.
- Go to the ucenter Messages view to discover the hexadecimal code sequences for UBX commands (Slide up the lower half of the split window & copypaste to my programme!).
- All multi-byte values of the UBX commands are ordered in Little Endian format, unless otherwise indicated.
- The checksum of the UBX commands is calculated over the Message, starting and including the CLASS field, up until, but excluding, the Checksum Field.

## WIRING INSTRUCTIONS
### MCU
a. Adafruit HUZZAH32
- UART Serial COM3
- Pin #13 = Blue LED on the PCB

b. Lolin32 Lite
- UART Serial COM5
- Pin #22 = Blue LED on the PCB

### GPS Board
```
- You have to cut off the wires from the big internal connector.

- External 6-pin DF13 connector. This is the GPS UART interface.
    MY DUPONT CABLE    GPS Cable    Function
 	 -----------------  ----------   ----------
    Groen              RED          VCC
    Grijs              BLACK        GND
 	 Paars              YELLOW       UART TXD
 	 Blauw              ORANGE       UART RXD

- External 4-pin DF13 connector. This is the COMPASS I2C interface ***NOTUSED***.
    GPS Cable   Function
    ---------   --------
    GREEN       I2C SCL
    BLACKISH    I2C SDA
```

## Data Sheet
Go to the _doc directory.
https://www.u-blox.com/en/product/neo-m8-series

## GPS FAQ
- OK 3.3V.
- The max speed for the UART is 9600 (this baudrate is also used by the Ublox u-center software).
- GNSS stands for Global Navigation Satellite System, and is an umbrella term that encompasses all global satellite positioning systems. This includes constellations of satellites orbiting over the earth’s surface and continuously transmitting signals that enable users to determine their position. The Global Positioning System (GPS) is one component of the Global Navigation Satellite System.
- The blue led on top of the GPS shell blinks if the GPs has a FIX (mostly "3D").
- It comes with the latest M8N chip module (suffix 010) and it carries the latest firware v3.1.
- Chip: u-blox NEO-M8N (the one with ROM, but no Flash). The firmware cannot  be upgraded but that is not a problem because the current ROM firmware version is very recent!
- Features a GPS Receiver + Compass.

## Sending UBX CFG Messages using the u-center software
```
===UBX-RXM-PMREQ: Requests a Power Management task=== power down (time delimited or infinite)
HEX Commands:
- ucenter Version=0 Duration=15000 Action=2: 15 seconds
    B5 62 02 41 08 00 98 3A 00 00 02 00 00 00 1F 91
    {0xB5, 0x62, 0x02, 0x41, 0x08, 0x00, 0x98, 0x3A, 0x00, 0x00, 0x02, 0x00, 0x00, 0x00, 0x1F, 0x91}

- ucenter Version=0 Duration=0 Action=2: infinite (=12 days!) It ALSO wakes up when you send whatever UBX command...
    B5 62 02 41 08 00 00 00 00 00 02 00 00 00 4D 3B
    {0xB5, 0x62, 0x02, 0x41, 0x08, 0x00, 0x00, 0x00, 0x00, 0x00, 0x02, 0x00, 0x00, 0x00, 0x4D, 0x3B}

---Message Structure---
Header (uint8 uint8)
	0xB5 0x62
Class ID (uint8)
	0x02
ID (uint8)
	0x41
Length (uint16) The number format of the length field is a Little-Endian unsigned 16-bit integer.
	8
Payload
	Offset  NbrFmt              Scaling Name 		Unit 	Description
	0 	    U4 Unsigned Long	-	    duration    ms      Duration of the requested task, set to zero for infinite duration. The maximum supported time is 12 days.
    4       X4 Bitfield         -       flags       -       task flags (bit#1 = "backup" The receiver goes into backup mode for a time period defined by duration. Provided that it is not connected to USB)
Checksum (The two 1-byte CK_A and CK_B fields hold a 16-bit checksum whose calculation is defined below)
	CK_A	uint8
	CK_B	uint8


===UBX-CFG-RST: Reset Receiver / Clear Backup Data Structures===
HEX Commands:
- ucenter Startup=Coldstart + Reset=Forced(Watchdog): ***All information is lost so the GPS has to start finding all satellites again (this takes a lot of time)***
    B5 62 06 04 04 00 FF B9 00 00 C6 8B
    {0xB5, 0x62, 0x06, 0x04, 0x04, 0x00, 0xFF, 0xB9, 0x00, 0x00, 0xC6, 0x8B}

- ucenter GNSS=stop + Startup=User Defined + Reset=*NONE: (only stops GNSS  = low power!)
    B5 62 06 04 04 00 00 00 08 00 16 74
    {0xB5, 0x62, 0x06, 0x04, 0x04, 0x00, 0x00, 0x00, 0x08, 0x00, 0x16, 0x74}

- ucenter GNSS=start + Startup=User Defined + Reset=*NONE: (only starts GNSS = normal power!)
    B5 62 06 04 04 00 00 00 09 00 17 76
    {0xB5, 0x62, 0x06, 0x04, 0x04, 0x00, 0x00, 0x00, 0x09, 0x00, 0x17, 0x76}

---Message Structure---
Header (uint8 uint8)
	0xB5 0x62
Class ID (uint8)
	0x06
ID (uint8)
	0x04
Length (uint16) The number format of the length field is a Little-Endian unsigned 16-bit integer.
	4
Payload
	Offset NbrFmt Scaling 	Name 		Unit 	Description
	0 	uint16	-	navBbrMask	-	BBR Sections to clear. The following Special Sets apply: 
									0x0000 Hot start
									0x0001 Warm start
									0xFFFF Cold start
	2 	uint8 	- 	resetMode 	- 	Reset Type: 
									0x00 - HW reset
									0x01 - Controlled SW reset
									0x02 - Controlled SW reset (GNSS only)
									0x04 - HW reset after shutdown
									0x08 - Controlled GNSS stop
									0x09 - Controlled GNSS start
	3	uint8	-	reserved1	-	Reserved
Checksum (The two 1-byte CK_A and CK_B fields hold a 16-bit checksum whose calculation is defined below)
	CK_A	uint8
	CK_B	uint8


===UBX-CFG-RATE: Navigation/Measurement Rate Settings===
HEX Commands:
- ucenter TimeSource="1-GPS Time" MeasurementPeriod=1000ms: ***DEFAULT***
    B5 62 06 08 06 00 E8 03 01 00 01 00 01 39
    {0xB5, 0x62, 0x06, 0x08, 0x06, 0x00, 0xE8, 0x03, 0x01, 0x00, 0x01, 0x00, 0x01, 0x39}

- ucenter TimeSource="1-GPS Time" MeasurementPeriod=100ms:
    B5 62 06 08 06 00 64 00 01 00 01 00 7A 12
    {0xB5, 0x62, 0x06, 0x08, 0x06, 0x00, 0x64, 0x00, 0x01, 0x00, 0x01, 0x00, 0x7A, 0x12}

- ucenter TimeSource="1-GPS Time" MeasurementPeriod=5000ms:
    B5 62 06 08 06 00 88 13 01 00 01 00 B1 49
    {0xB5, 0x62, 0x06, 0x08, 0x06, 0x00, 0x88, 0x13, 0x01, 0x00, 0x01, 0x00, 0xB1, 0x49}

---Message Structure---
Header (uint8 uint8)
	0xB5 0x62
Class ID (uint8)
	0x06
ID (uint8)
	0x08
Length (uint16) The number format of the length field is a Little-Endian unsigned 16-bit integer.
	6
Payload
	Offset 	NbrFmt 	Scaling	Name 		Unit 	Description
	0 	uint16	-	measRate	ms	The elapsed time between GNSS measurements, which defines the rate, e.g. 100ms => 10Hz, 1000ms => 1Hz, 10000ms => 0.1Hz
								   75ms = 0x4B 0x00 FASTEST
								 1000ms = 0xE8 0x03 DEFAULT
								 5000ms = 0x88 0x13 SLOWER
								50000ms = 0x50 0xC3 SLOWEST

	2 	uint16 	- 	navRate 	cycle 	The ratio between the number of measurements and the number of navigation solutions, 
							e.g. 5 means five measurements for every navigation solution. Max. value is 127.
								1 = DEFAULT (OK).
Checksum (The two 1-byte CK_A and CK_B fields hold a 16-bit checksum whose calculation is defined below)
	CK_A	uint8
	CK_B	uint8
```

##
## FYI PixHawk flight controller instructions:
Connect the GPS’s Hirose DF13 6-pin connector to the Pixhawk GPS port and the compass’s Hirose DF13 4-pin connector to the I2C port.


## Known ISSUES
/
