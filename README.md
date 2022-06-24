# OpenDTU

## Background
This project was started from [this](https://www.mikrocontroller.net/topic/525778) discussion (Mikrocontroller.net).
It was the goal to replace the original Hoymiles DTU (Telemetry Gateway) with their cloud access. With a lot of reverse engineering the Hoymiles protocol was decrypted and analyzed.


## Features for end users
* Uses ESP32 microcontroller and NRF24L01+
* Multi-Inverter support
* MQTT support
* Nice and fancy WebApp with visualization of current data
* Firmware upgrade using the web UI
* Default source supports up to 10 inverters
* Time zone support


## Features for developers
* The microcontroller part
    * Build with Arduino PlatformIO Framework for the ESP32
    * Uses [ESPAsyncWebserver](https://github.com/me-no-dev/ESPAsyncWebServer) and [Async MQTT client](https://github.com/marvinroger/async-mqtt-client)

* The WebApp part
    * Build with [Vue.js](https://vuejs.org)
    * Source is written in TypeScript

## Wiring up
### Schematic
![Schematic](docs/Wiring_ESP32_Schematic.png)

### Symbolic view
![Symbolic](docs/Wiring_ESP32_Symbol.png)

## Flashing and starting up
* Install [Visual Studio Code](https://code.visualstudio.com/download)
* In Visual Studio Code, install the [PlatformIO Extension](https://marketplace.visualstudio.com/items?itemName=platformio.platformio-ide)
* Download or clone this repository
* In Visual Studio Code, choose File --> Open Folder and select the previously downloaded source code. (You have to select the folder which contains the "platformio.ini" file)
* Adjust the COM port in the file "platformio.ini". It occurs twice:
    * upload_port
    * monitor_port
* Select the arrow button in the status bar (PlatformIO: Upload) to compile and upload the firmware. During the compilation, all required libraries are downloaded automatically.

## First configuration
* After the initial flashing of the microcontroller, a Access Point called "OpenDTU-*" is opened. The default password is "openDTU42".
* Use a web browser to open the address [http://192.168.4.1](http://192.168.4.1)
* Navigate to Settings --> Network Settings and enter your WiFi credentials
* Currently you have to look at your router to determine the IP of the newly connected device

## Building
* Building the WebApp
    * The WebApp can be build using yarn
    ```
    $ yarn install
    $ yarn build
    ```
    * The updated output is placed in the 'data' directory

* Building the microcontroller firmware
    * Visual Studio Code with the PlatformIO Extension is required for building