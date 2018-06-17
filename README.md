June 2018.

# ESP32 MJD Starter Kit Software
## Introduction
Do you also want to create innovative IoT projects that use the ESP32 chip, or ESP32-based modules, of the popular company Espressif? Well, I did and still do. And I hope you do too.

The objective of this well documented Starter Kit is to accelerate the development of your IoT projects for ESP32 hardware using the ESP-IDF framework from Espressif.

Are you ready to discover how you can get started quickly?

## Why would you need this ESP32 MJD Starter Kit Software?
The ESP-IDF framework (and its documentation) is very powerful and extensive.

But I found it difficult to get started quickly, for me being a seasoned full stack developer (backend/frontend) without much experience developing IoT solutions using embedded systems.

More specifically, I could understand all the features of the ESP-IDF framework but I had a hard time gluing everything together, and quickly develop real projects for real solutions using peripherals such as sensors and GPS boards and LED strips. For example, I wanted to start with projects controlling various sensors in a network and analyzing the data on a central server, and then move on to more complex projects.

Secondly, it was difficult to find good documentation (data sheets, diagrams, photo's of the wiring) of the various peripheral devices such as meteo sensors, GPS boards, RGB LED's, etc. And how to use these devices in combination with an ESP32-based development board.

So I developed over time these extra components, good documentation, and many working projects targeting a whole suite of peripherals/sensors that are typically used in IoT projects.

And I think now is a good time to give something back to the ESP32 community and release everything I learned so far, so everyone can benefit from this work.

## Why choose the ESP-IDF framework?
You have 2 options to start developing for the ESP32 chip:

1. Use "ESP-IDF", the extensible official Espressif IoT Development Framework of Espressif. \
This is the official development framework for the ESP32 chip. It is targeted for C/C++ applications and it includes a port of the popular (Amazon) FreeRTOS O.S. This is the most powerful framework of the two and it contains a ton of excellent libraries so you can use all features of the ESP32 environment. It assumes you are at least an intermediate C Developer and it has a stiff learning curve.

2. Use the official "Arduino Core For ESP32" framework of Espressif for the Arduino IDE. \
This is a hardware abstraction layer for Arduino IDE so you can target the ESP32 chip. The big advantage is that you can empower your existing knowledge of the Arduino IDE. The downside is that it is not that feature-rich compared to ESP-IDF when it comes to specific ESP32 functionality. And the development pace is slower and not all features of ESP-IDF have been ported to Arduino.

It is important to know that both frameworks are stable and usable but they are still under significant development by Espressif, and major new releases are coming out on a regularly basis; I expect this to continue at least until 2018Q4.

After experimenting with both frameworks I decided to go with the ESP-IDF framework, more specifically V3 and higher. I always try to release libraries that are compatible with the last major release and eventually the master branch.

## What are the requirements of the ESP32 MJD Starter Kit?
### Hardware
- A decent ESP development board. I suggest to buy for starters a popular development board with a good influx of technical documentation. Examples: [Adafruit HUZZAH32](https://www.adafruit.com/product/3405), [Pycom WiPy](https://pycom.io/hardware/). A good budget board is the [Wemos D32](https://wiki.wemos.cc/products:d32:d32).
- The peripherals that are used in the project. @tip The README of each component contains a section "Shop Products".
 
### Software
- A working installation of the Espressif ESP-IDF V3 development framework (instructions @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
- A C language editor or the Eclipse IDE CDT (instructions also @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).

## What is in the ESP32 MJD Starter Kit?
### Development Boards /development_boards
Firstly it contains basic information about a few ESP32 development boards that I have used initially:
1. Adafruit HUZZAH32.
2. Wemos Lolin32 Lite.

### Working Projects
Secondly the Starter Kit includes various working projects that you can run instantly (opposed to snippets that you have to glue together yourself, which is not easy for a beginner).

These projects:
- Give insights in how to actually use the official ESP-IDF framework efficiently.
- Include a ton of best coding practices and configuration practices.
- Demonstrate how to use the new ESP-IDF components of this Starter Kit, such as RGB LED strips and meteo sensors (see next section).

Let's highlight a few projects that demonstrate how to use the core ESP-IDF framework.
- `my_button_basics` Demonstrates how to interface with buttons (switches).
- `my_gpio_basics` Demonstrates how to interact with GPIO pins of the development board.
- `my_gpio_scanner` Demonstrates how to scan all GPIO pins and discover their I/O function.
- `my_i2c_scanner` Demonstrates how to scan all slave devices on the I2C pins, and identify their I2C slave address. This is handy when working with new I2C slave devices.
- `my_ledc_pwm_basics` Demonstrates how to use the standard ESP-IDF LEDC driver (a LED Controller driver using PWM).
- `my_rmt_basics` Demonstrates how to use the standard ESP-IDF RMT driver.
- `my_spiffs_basics` Demonstrates how to use the standard ESP-IDF SPIFFS file system driver.
- `my_sw180_tilt_sensor` Demonstrates how to interface with this tilt sensor (no extra components needed).
- `my_timer_basics` Demonstrates how to use the standard ESP-IDF Timer driver.
- `my_uart_basics` Demonstrates how to use the standard ESP-IDF UART driver.
- `my_wifi_device_scanner` Demonstrates how to scan all Wifi channels and discover the devices.
- `my_wifi_ssid_cloner` Demonstrates how to clone existing Access Points.
- `my_wifi_ssid_scanner` Demonstrates how to scan all Wifi channels and discover the Access Points.
- `my_wifi_ssid_spammer` Demonstrates how to create additional Access Points in the area.

Let's highlight a few projects that demonstrate how to use the extra components of the ESP32 Starter Kit.
- `mjd_components` Demonstrates best practices when using ESP-IDF and example code for all non-peripheral components such as linked lists, ESP chip interfaces, Wifi, networking, MQTT, ....
- `my_am2320_temperature_sensor_using_lib` Demonstrates how to read data from the Aosong AM2320 meteo sensor.
- `my_bh1750fvi_lightsensor_using_lib` Demonstrates how to read data from the BH1750 light intensity sensor.
- `my_bme280_sensor_using_lib` Demonstrates how to read data from the Bosch BME280 meteo sensor.
- `my_bmp280_sensor_using_lib` Demonstrates how to read data from the Bosch BMP280 meteo sensor.
- `my_dht11_temperature_sensor_using_lib` Demonstrates how to read data from the Aosong DHT11 temperature sensor.
- `my_dht22_temperature_sensor_using_lib` Demonstrates how to read data from the Aosong DHT22/AM2302 temperature sensor.
- `my_hcsr501_pir_sensor_using_lib` Demonstrates how to read data from the HC-SR501 PIR human infrared sensor.
- `my_ky032_obstacle_sensor_using_lib` Demonstrates how to read data from the KY-032 infrared obstacle avoidance sensor.
- `my_ledrgb_using_lib` Demonstrates how to control RGB LED strips (such as the Adafruit Neopixels and BTF-LIGHTNING products).
- `my_linked_list_basics` Demonstrates how to use the Linked List component.
- `my_neom8n_gps_using_lib` Demonstrates how to get GPS data from the GPS Ublox NEO-M8N module.
- `my_zs042_clock_using_lib` Demonstrates how to get/set data from the ZS-042 DS1302 RTC realtime clock board.

### Extra ESP-IDF Components
Thirdly I noticed that many coding patterns came back again and again in the first projects that I developed for the ESP32.

So after a while I started putting those coding patterns in separate libraries. The ESP-IDF is an extensible framework so these libraries are implemented as new ESP-IDF components which can be injected easily in any ESP-IDF based project (a big plus I reckon).

The components can roughly be divided in 3 groups:
1. Related to programmming in the C language (which has its own quirks as all other programming languages). Example: linked lists.
2. Related to the ESP32 environment and the specifics of embedded systems. Examples: an easy Wifi component. They make those ESP-IDF features much easier to use.
3. Related to networking. Some examples: interfacing with an MQTT server and some DNS functions. The component abstracts the complexity, and makes it much easier to use.
4. Related to the peripherals that you wire up to the ESP32 chip or ESP32 module. Some examples: RGB LED's, temperature sensors, GPS boards, RTC clocks, PIR sensors, and obstacle sensors. The component abstracts the complexity of the peripheral.

This is the list of new components:
- `mjd` The base component which contains general purpose functions.
- `mjd_am2320` Component for the Aosong AM2320 meteo sensor.
- `mjd_bh1750fvi` Component for the BH1750 light intensity sensor.
- `mjd_bme280` Component for the Bosch BME280 meteo sensor.
- `mjd_bmp280` Component for the Bosch BMP280 meteo sensor.
- `mjd_dht11` Component for the Aosong DHT11 temperature sensor.
- `mjd_dht22` Component for the Aosong DHT11/AM2302 temperature sensor.
- `mjd_hcsr501` Component for the HC-SR501 PIR human infrared sensor.
- `mjd_ky032` Component for the KY-032 infrared obstacle avoidance sensor.
- `mjd_ledrgb` Component for controlling various RGB LED strips (Worldsemi WS28xx chips such as the Adafruit Neopixels product line).
- `mjd_list` Component that implements the Linked Lists as used in the Linux Kernel.
- `mjd_log` Component to facilitate logging in the app.
- `mjd_mqtt` Component for interacting with an MQTT server (as an MQTT client).
- `mjd_neom8n` Component for the GPS Ublox NEO-M8N module.
- `mjd_net` Component to facilitate various networking features (getting IP address, DNS resolve hostnames, etc.). 
- `mjd_wifi` Component to facilitate, as a Wifi Station, a connection to a Wifi Access Point.
- `mjd_zs042` Component for the ZS-042 DS1302 RTC realtime clock.

Let's categorize these components in more detail:
 
#### C Language
- Linked lists using the Linux Kernel implementation.
- Manage strings.
- Manage date & time.
- Manage BCD (binary-coded-decimal).

#### ESP32 General
- Logging.
- Deep sleep.

#### ESP32 Networking
- Synchronizing the datetime (SNTP).
- Resolve hostnames using DNS.
- Get current IP address.
- Check if Internet is available.

#### ESP32 Wifi
- Manage Wifi connections.

#### ESP32 MQTT
- Manage MQTT publish/subscribe.

#### ESP32 Peripherals - Devices
- GPS Ublox NEO-M8N module.
- ZS-042 DS1302 Real Time Clock.

#### ESP32 Peripherals - RGB LED's
This component supports several RGB LED packages. It comes with the essential documentation such as data sheets, schematics, and instructions on how to wire them to your development board and eventually an extra power supply.

- RGB LED packages such as the WS2812, WS2812B, WS2813xs chips from the manufacturer Worldsemi http://www.world-semi.com/solution/list-4-1.html 
- Adafruit's Neopixels that use the aforementioned packages.

#### ESP32 Peripherals - Sensors
These components come with the essential documentation such as data sheets, schematics, and instructions on how to wire them to your development board.

- AM2320 temperature sensor by Aosong.
- DHT11 temperature sensor by Aosong.
- DHT22/AM2302 temperature sensor by Aosong.
- BH1750FVI light sensor.
- Bosch BME280 meteo sensor.
- Bosch BMP280 meteo sensor.
- HC-SR501 PIR motion sensor.
- KY-032 Infrared obstacle avoidance sensor.

## How do you use the ESP32 MJD Starter Kit?
The easiest way is to open the directory of a project that contains the features that you are interested in.

Read the instructions in the README for the hardware, wiring, and software setup.

The wiring instructions of the components can be found in the component's directory under ./_doc/. The documentation typically documents the wiring for the Adafruit HUZZAH32 (a good ESP32 development board) and that info can be extrapolated to other ESP32 dev boards easily, and some FAQ about the component.

Procedure:
1. A working installation of the Espressif ESP-IDF V3 development framework (instructions @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
2. A C language editor or the Eclipse IDE CDT (instructions @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
3. Clone this Github repository. `git clone https://github.com/pantaluna/esp32-mjd-starter-kit.git`
4. `cd` into the directory of the project you want to explore under `./projects`.
5. Read the instructions in the README of the project.
6. Read the instructions in the README of all the extra components that are used in this project. Remember that if relevant the wiring instructions are always documented in the component's directory ./_doc/ (not in the project directory).
7. Run `make menuconfig` to modify the settings of the project that you want to run (e.g. GPIO PIN#, wifi credentials, ...).
8. Run `make flash monitor` to build and upload the example to your dev board and monitor the execution via the serial terminal.

## FAQ
- The ESP32 Starter Kit gets you started quickly. If you need extra features of an existing component, or you wish to propose a new component, then please submit an issue.
- The Kit is not designed to implement all conceivable features of any ESP32 project. If a new feature is very specific for your project then the best approach is to make your own bundle of ESP-IDF components with the functionality that you want. You can use these components as the foundation; please do not forget to mention that you obtained the components from this Starter Kit.
- What does "MJD" stands for? It is a unique acronym and it is used in the C language to make identifiers unique. This approach ensures that you can use these new ESP-IDF components in any other C project.
- Why are all projects and components stored in one Github repository (opposed to have a Github repo for each project and each component)? I think this makes the Kit easier to use for beginners. In the future the Kit might be setup using Git submodules.

## Known Issues

## What Is Next for me
- Release extra components for TFT Displays and RGB LED matrixes.
- To release an Iot Platform to the public so you can manage the devices in the field and analyze the incoming data.
- To make a new website for the technical documentation of this Kit.

## What Is Next for you
- Please share your experiences using this ESP32 MJD Starter Kit with the ESP32 community.
