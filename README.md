# ESP32 Starter Kit MJD
## Introduction
Do you also want to create innovative IoT projects that use the ESP32 chip, or ESP32-based modules, of Espressif? Well, I did and still do and I hope you do too.

The objective of this Starter Kit is to accelerate the development of your IoT projects for ESP32 using the ESP-IDF framework from Espressif.

Are you ready to discover how you can get started quickly?

## Why choose the ESP-IDF framework?
You have 2 options to start developing for the ESP32 chip:

1. Use "ESP-IDF", the extensible official Espressif IoT Development Framework of Espressif. \
This is the official development framework for the ESP32 chip. It is targeted for C/C++ applications. This is the most powerful framework of the two and it contains a ton of excellent libraries so you can use all features of the ESP32 environment. It assumes you are at least an intermediate C Developer and it has a stiff learning curve.
2. Use the official "Arduino Core For ESP32" framework of Espressif.\
This is a hardware abstraction layer for Arduino IDE so you can target the ESP32 chip. The big advantage is that you can empower your existing knowledge of the Arduino IDE. The downside is that it is not that feature-rich compared to ESP-IDF. And the development pace is slower and not all features of ESP-IDF have been ported to Arduino.

It is important to know that both frameworks are stable and usable but they are still under significant development by Espressif, and major new releases are coming out on a regularly basis; I expect this to continue at least until 2018Q4.

After experimenting with both frameworks I decided to go with the ESP-IDF framework, more specifically V3.0 and higher. I always try to release libraries that are compatible with the last major release and eventually the master branch.

## Why would you need this starter kit?
The ESP-IDF framework (and its documentation) is very powerful and extensive.

But I found it difficult to get started quickly, for me being a seasoned full stack developer (backend/frontend) without much experience developing IoT solutions that use embedded systems as well. PS So being a Full Stack Developer doesn't mean you know everything there is, right?

More specifically, I could understand all the features of the ESP-IDF framework but I had a hard time gluing everything together, and develop real projects for real solutions using peripherals such as sensors ans GPS boards. For example, I wanted to start with projects controlling various sensors in a network, and then move on to more complex projects.

So I developed over time these extra components, including many working projects targeting a complete set of peripherals/sensors that are typically used in IoT projects.

And I thought now was a good time to release everything I learned so far to the ESP32 community so everyone can benefit from this work.

## What are the requirements of the ESP32 Starter Kit
1. A working installation of the Espressif ESP-IDF V3 development framework (http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
2. A C language editor or the Eclipse IDE CDT.

## What is in the Starter Kit?
### Working Projects.
Firstly the Starter Kit includes various working projects that you can run instantly (opposed to snippets that you have to glue together yourself).

These projects:
- Give insights in how to actually use the official ESP-IDF framework efficiently.
- Include a ton of best coding practices and best configuration practices.
- Demonstrate how to use the new ESP-IDF components of this Starter Kit, such as RGB LED strips and meteo sensors (see next section).

Let's highlight a few projects that demonstrate how to use the core ESP-IDF framework.
- Battery wearer.
- Button basics.
- GPIO basics.
- GPIO scanner.
- I2C scanner.
- LEDC basics.
- SPIFFS basics.
- Timer basics.
- UART basics.
- Wifi device scanner.
- Wifi SSID cloner.
- Wifi SSID scanner.
- Wifi SSID spammer.

Let's highlight a few projects that demonstrate how to use the extra components of the ESP32 Starter Kit.
- MJD Components (this project demonstrates best practices when using ESP-IDF and example code for all non-peripheral components such as linked lists, ESP chip interfaces, Wifi, networking, MQTT, ...).
- AM2320 meteo sensor.
- BH1750 light intensity sensor.
- BME280 meteo sensor.
- BMP280 meteo sensor.
- DHT11 temperature sensor.
- GPS Ublox NEO-M8N module.
- HC-SR501 PIR human infrared sensor
- KY-032 infrared obstacle avoidance sensor.
- RGB LED strips.
- ZS-042 DS1302 RTC realtime clock.

### Extra ESP-IDF Components
Secondly, I noticed that many coding patterns came back again and again in the first projects that I developed for the ESP32.

So after a while I started putting those coding patterns in separate libraries, as any competent developer would do. The ESP-IDF is an extensible framework so these libraries are implemented as new ESP-IDF components which can be injected easily in any ESP-IDF based project.

The components can roughly be divided in 3 groups:
1. Related to programmming in the C language (which has its own quirks as all other programming languages). Example: linked lists.
2. Related to the ESP32 environment and the specifics of embedded systems. Some examples: an easy Wifi component, the SPIFFS file system. They make those ESP-IDF features much easier to use.
3. Related to the peripherals that you wire up to the ESP32 chip or ESP32 module. Some examples: RGB LED's, temperature sensors, GPS boards, RTC clocks, PIR sensors, and obstacle sensors. The component abstracts the complexity of the sensor, and make it much easier to use.

Let's highlight a few.
 
#### C Language
- Linked lists using the Linux Kernel implementation.
- Manage strings.
- Manage date & time.
- Manage BCD (binary-coded-decimal).

#### ESP32 General
- Logging.
- Deep sleep.

#### Networking
- Synchronizing the datetime (SNTP).
- Resolve hostnames using DNS.
- Get current IP address.
- Check if Internet is available.

#### Wifi
- Manage Wifi connections.

#### MQTT
- Manage MQTT publish/subscribe.

#### Peripherals - Devices
- GPS Ublox NEO-M8N module.
- ZS-042 DS1302 Real Time Clock.

#### Peripherals - RGB LED's
This component supports several RGB LED packages. It comes with the essential documentation such as data sheets, schematics, and instructions on how to wire them to your development board.

- RGB LED packages WS2812, WS2812B, WS2813xs from the manufacturer Worldsemi http://www.world-semi.com/solution/list-4-1.html 
- Adafruit's Neopixels that use the aforementioned packages.

#### Peripherals - Sensors
These components come with the essential documentation such as data sheets, schematics, and instructions on how to wire them to your development board.

- AM2320 temperature sensor by Aosong.
- DHT11 temperature sensor by Aosong.
- BH1750FVI light sensor.
- Bosch BME280 meteo sensor.
- Bosch BMP280 meteo sensor.
- HC-SR501 PIR motion sensor.
- KY-032 Infrared obstacle avoidance sensor.

## How do you use the ESP32 Starter Kit?
The easiest way is to open a project directory that contains the features that you are interested in.

Read the instructions in the README for the hardware, wiring, and software setup. The wiring instructions of the components can be found in their respective component directory. The documentation typically documents the wiring for the Adafruit HUZZAH32 (a good ESP32 development board).

1. Verify that you have a working installation of the Espressif ESP-IDF V3 development framework (http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
2. A C language editor or the Eclipse IDE CDT.
3. Clone this Github repository.
4. `cd` into the directory of the project you want to explore.
5. Read the (wiring) instructions in the README of the project, and the README of all the extra components that are used in this project. the latter contains the wiring instructions if wiring is required.
6. Run `make flash monitor` to build and upload the example to your dev board and connect to it's serial terminal.




## FAQ
- The ESP32 Starter Kit gets you started quickly. If you need extra features that seem a good fit for the Starter Kit then please submit an issue. If the feature is very specific to your project then the best approach is to make your own bundle of ESP-IDF components with the functionality that you want. The Starter Kit is not designed to implement all conceivable features of any ESP32 project.

## Known Issues

## What Is Next
Please share your experiences using this ESP32 Starter Kit with the ESP32 community.
