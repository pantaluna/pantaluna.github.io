# ESP32 MJD Starter Kit
## Introduction
Do you also want to create innovative IoT projects that use the ESP32 chip, or ESP32-based modules, of the innovative company Espressif? Well, I did and still do and I hope you do too.

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

## Why would you need this ESP32 MJD Starter Kit?
The ESP-IDF framework (and its documentation) is very powerful and extensive.

But I found it difficult to get started quickly, for me being a seasoned full stack developer (backend/frontend) without much experience developing IoT solutions that use embedded systems as well. PS So being a Full Stack Developer doesn't mean you know everything there is, right?

More specifically, I could understand all the features of the ESP-IDF framework but I had a hard time gluing everything together, and develop real projects for real solutions using peripherals such as sensors and GPS boards and LED strips. For example, I wanted to start with projects controlling various sensors in a network, and then move on to more complex projects.

So I developed over time these extra components, including many working projects targeting a complete set of peripherals/sensors that are typically used in IoT projects.

And I thought now was a good time to release everything I learned so far to the ESP32 community so everyone can benefit from this work.

## What are the requirements of the ESP32 MJD Starter Kit?
1. A working installation of the Espressif ESP-IDF V3 development framework (instructions @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
2. A C language editor or the Eclipse IDE CDT (instructions also @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).

## What is in the ESP32 MJD Starter Kit?
### Working Projects.
Firstly the Starter Kit includes various working projects that you can run instantly (opposed to snippets that you have to glue together yourself).

These projects:
- Give insights in how to actually use the official ESP-IDF framework efficiently.
- Include a ton of best coding practices and best configuration practices.
- Demonstrate how to use the new ESP-IDF components of this Starter Kit, such as RGB LED strips and meteo sensors (see next section).

Let's highlight a few projects that demonstrate how to use the core ESP-IDF framework.
- `my_battery_wearer` Demonstrates how to consume plenty of CPU and so test the longevity of the LiFePo4 battery.
- `my_button_basics` Demonstrates how to interface with buttons (switches).
- `my_gpio_basics` Demonstrates how to interact with GPIO pins of the development board.
- `my_gpio_scanner` Demonstrates how to scan all GPIO pins and discover their function.
- `my_i2c_scanner` Demonstrates how to scan all slave devices on the I2C pins, and identify their I2C slave address. This is handy when working with new I2C slave devices.
- `my_ledc_basics` Demonstrates how to use the standard ESP-IDF LEDC driver.
- `my_spiffs_basics` Demonstrates how to use the standard ESP-IDF SPIFFS file system driver.
- `my_timer_basics` Demonstrates how to use the standard ESP-IDF Timer driver.
- `my_uart_basics` Demonstrates how to use the standard ESP-IDF UART driver.
- `my_wifi_device_scanner` Demonstrates how to scan all Wifi channels and discover the devices.
- `my_wifi_ssid_cloner` Demonstrates how to clone existing Access Points.
- `my_wifi_ssid_scanner` Demonstrates how to scan all Wifi channels and discover the Access Points.
- `my_wifi_ssid_spammer` Demonstrates how to create additional Access Points in the area.

Let's highlight a few projects that demonstrate how to use the extra components of the ESP32 Starter Kit.
- `mjd_components` Demonstrates best practices when using ESP-IDF and example code for all extra non-peripheral components such as linked lists, ESP chip interfaces, Wifi, networking, MQTT, ....
- `my_am2320_temperature_sensor_using_lib` Demonstrates how to read data from the AM2320 meteo sensor.
- `my_bh1750fvi_lightsensor_using_lib` Demonstrates how to read data from the BH1750 light intensity sensor.
- `my_bme280_sensor_using_lib` Demonstrates how to read data from the BME280 meteo sensor.
- `my_bmp280_sensor_using_lib` Demonstrates how to read data from the BMP280 meteo sensor.
- `my_dht11_temperature_sensor_using_lib` Demonstrates how to read data from the DHT11 temperature sensor.
- `my_hcsr501_pir_sensor_using_lib` Demonstrates how to read data from the HC-SR501 PIR human infrared sensor.
- `my_ky032_obstacle_sensor_using_lib` Demonstrates how to read data from the KY-032 infrared obstacle avoidance sensor.
- `my_ledrgb_using_lib` Demonstrates how to control RGB LED strips (such as the Adafruit Neopixels).
- `my_neom8n_gps_using_lib` Demonstrates how to get GPS data from the GPS Ublox NEO-M8N module.
- `my_zs042_clock_using_lib` Demonstrates how to get/set data from the ZS-042 DS1302 RTC realtime clock.

### Extra ESP-IDF Components
Secondly, I noticed that many coding patterns came back again and again in the first projects that I developed for the ESP32.

So after a while I started putting those coding patterns in separate libraries, as any competent developer would do. The ESP-IDF is an extensible framework so these libraries are implemented as new ESP-IDF components which can be injected easily in any ESP-IDF based project (a big plus).

The components can roughly be divided in 3 groups:
1. Related to programmming in the C language (which has its own quirks as all other programming languages). Example: linked lists.
2. Related to the ESP32 environment and the specifics of embedded systems. Some examples: an easy Wifi component, the SPIFFS file system. They make those ESP-IDF features much easier to use.
3. Related to the peripherals that you wire up to the ESP32 chip or ESP32 module. Some examples: RGB LED's, temperature sensors, GPS boards, RTC clocks, PIR sensors, and obstacle sensors. The component abstracts the complexity of the sensor, and make it much easier to use.

This is the list of new components:
- `mjd` The base component which contains general purpose functions.
- `mjd_am2320` Component for the AM2320 meteo sensor.
- `mjd_bh1750fvi` Component for theBH1750 light intensity sensor.
- `mjd_bme280` Component for the BME280 meteo sensor.
- `mjd_bmp280` Component for the BMP280 meteo sensor.
- `mjd_dht11` Component for the DHT11 temperature sensor.
- `mjd_hcsr501` Component for the HC-SR501 PIR human infrared sensor.
- `mjd_ky032` Component for the KY-032 infrared obstacle avoidance sensor.
- `mjd_ledrgb` Component for controlling various RGB LED strips (such as the Adafruit Neopixels).
- `mjd_list` Component that implement the Linked Lists as used in the Linux Kernel.
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
This component supports several RGB LED packages. It comes with the essential documentation such as data sheets, schematics, and instructions on how to wire them to your development board.

- RGB LED packages WS2812, WS2812B, WS2813xs from the manufacturer Worldsemi http://www.world-semi.com/solution/list-4-1.html 
- Adafruit's Neopixels that use the aforementioned packages.

#### ESP32 Peripherals - Sensors
These components come with the essential documentation such as data sheets, schematics, and instructions on how to wire them to your development board.

- AM2320 temperature sensor by Aosong.
- DHT11 temperature sensor by Aosong.
- BH1750FVI light sensor.
- Bosch BME280 meteo sensor.
- Bosch BMP280 meteo sensor.
- HC-SR501 PIR motion sensor.
- KY-032 Infrared obstacle avoidance sensor.

## How do you use the ESP32 MJD Starter Kit?
The easiest way is to open a project directory that contains the features that you are interested in.

Read the instructions in the README for the hardware, wiring, and software setup. The wiring instructions of the components can be found in their respective component directory. The documentation typically documents the wiring for the Adafruit HUZZAH32 (a good ESP32 development board).

1. A working installation of the Espressif ESP-IDF V3 development framework (instructions @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
2. A C language editor or the Eclipse IDE CDT (instructions @ http://esp-idf.readthedocs.io/en/latest/get-started/index.html).
3. Clone this Github repository. `git clone https://github.com/pantaluna/esp32-mjd-starter-kit.git`
4. `cd` into the directory of the project you want to explore.
5. Read the instructions in the README of the project, and the README of all the extra components that are used in this project. the latter contains the wiring instructions if wiring is required.
6. Run `make flash monitor` to build and upload the example to your dev board and connect to it's serial terminal.

## FAQ
- The ESP32 Starter Kit gets you started quickly. If you need extra features that seem a good fit for the Starter Kit then please submit an issue. If the feature is very specific to your project then the best approach is to make your own bundle of ESP-IDF components with the functionality that you want. The Starter Kit is not designed to implement all conceivable features of any ESP32 project.
- What does "MJD" stands for? It is an acronym adn it is used in the C language to make identifiers unique. This approach ensures that you can use these new ESP-IDF components in any other C project.
 
## Known Issues

## What Is Next
Please share your experiences using this ESP32 MJD Starter Kit with the ESP32 community.
