# CYD ESP32-2032S028R Home Assistant IoT Device

This repository contains the necessary files and documentation for an IoT device built around the **CYD ESP32-2032S028R board**, integrated with **Home Assistant** using **ESPHome**, and housed in a custom-designed **3D-printed enclosure**.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Hardware](#hardware)
- [Software/Firmware](#softwarefirmware)
- [3D Printed Enclosure](#3d-printed-enclosure)
- [Installation & Setup](#installation--setup)
    - [ESPHome Firmware Flashing](#esphome-firmware-flashing)
    - [Home Assistant Integration](#home-assistant-integration)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Project Overview

This project provides a complete solution for deploying a custom IoT device with a display, leveraging the popular CYD ESP32-2032S028R board. It demonstrates a full workflow from firmware development with ESPHome, seamless integration with Home Assistant for automation and control, to the creation of a functional and aesthetically pleasing 3D-printed enclosure.

## Features

* **Customizable Display:** Utilize the 2.8-inch display of the CYD board to show various sensor data, time, weather, or Home Assistant entity states.
* **Home Assistant Integration:** Deep integration with Home Assistant via ESPHome, allowing for easy control, automation, and data visualization.
* **ESPHome Flexibility:** Leverage ESPHome's easy YAML configuration for rapid development and over-the-air (OTA) updates.
* **Modular Design:** The project focuses on modularity, making it easy to adapt to different use cases or expand with additional sensors.
* **3D Printable Enclosure:** A robust and well-fitting enclosure designed specifically for the CYD ESP32-2032S028R board, available for anyone to print.

## Hardware

The core of this project is the **CYD ESP32-2032S028R** board.

* **Board:** CYD ESP32-2032S028R (2.8-inch 320x240 LCD, ESP32-WROOM-32)
* **(Optional) Sensors:** (List any specific sensors you've integrated, e.g., DHT11 for temperature/humidity, LDR for light, etc. If none, you can omit this or mention future expansion.)
* **3D Printer:** Creality Ender 3v2 (for printing the enclosure)

## Software/Firmware

* **ESPHome:** Used to create custom firmware for the ESP32, providing a user-friendly way to configure and manage the device.
    * The ESPHome configuration files (`.yaml`) for this project are located in the `esphome/` directory.
* **Home Assistant:** The central home automation platform that integrates with the ESP32 device for control and monitoring.
* **FreeCAD:** Used for designing the 3D printable enclosure.
    * The FreeCAD design files (`.FCStd`) are located in the `3d_model/` directory.
* **PrusaSlicer:** Used for slicing the 3D model into G-code for printing.

## 3D Printed Enclosure

A custom enclosure was designed in FreeCAD and printed on a Creality Ender 3v2. The design ensures a snug fit for the CYD ESP32-2032S028R board, protecting it while providing a polished look.

* **Design Files:** The FreeCAD design files (`.FCStd`) can be found in the `3d_model/` directory.
* **Printable Files:** The `.stl` files ready for slicing are also available in the `3d_model/` directory.
* **Thingiverse Link:** The 3D model is publicly available on Thingiverse: [https://www.thingiverse.com/thing:7047135](https://www.thingiverse.com/thing:7047135)

*(Optional: Add a picture of the 3D printed enclosure here)*

*(Remember to create an `images` folder and place your photo there)*

## Installation & Setup

### ESPHome Firmware Flashing

1.  **Install ESPHome:** If you haven't already, install ESPHome. You can do this via `pip`:
    ```bash
    pip install esphome
    ```
    Or, if you run Home Assistant OS, you can install the ESPHome add-on directly from the Add-on Store.

2.  **Clone this repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```

3.  **Edit `esphome/cyd_esp32_display.yaml`:**
    * Open the `esphome/cyd_esp32_display.yaml` file.
    * **Crucially, modify the `wifi:` section** with your Wi-Fi SSID and password:
        ```yaml
        wifi:
          ssid: "YOUR_WIFI_SSID"
          password: "YOUR_WIFI_PASSWORD"
        ```
    * (Optional: Adjust other parameters like `device_name` if you wish.)

4.  **Flash the firmware:**
    * Connect your CYD ESP32-2032S028R board to your computer via USB.
    * Navigate to the `esphome/` directory within your cloned repository.
    * Run the ESPHome command to flash the device. Replace `cyd_esp32_display.yaml` with your actual YAML file name if different.
        ```bash
        esphome run cyd_esp32_display.yaml
        ```
    * Follow the on-screen prompts. ESPHome will compile the firmware and then attempt to flash it.

### Home Assistant Integration

Once the ESP32 board is successfully flashed and connected to your network, Home Assistant should automatically discover it.

1.  **Automatic Discovery:** Go to your Home Assistant UI. You should see a new "Discovered" device notification. Click on it and follow the steps to add the ESPHome device.
2.  **Manual Integration (if not discovered):**
    * Go to **Settings** -> **Devices & Services**.
    * Click on **+ Add Integration**.
    * Search for "ESPHome" and select it.
    * Enter the IP address of your ESP32 device (you can find this in your router's connected devices list or in the ESPHome logs during flashing).
    * Follow the prompts to complete the setup.

## Usage

Once integrated, your CYD ESP32-2032S028R device will appear in Home Assistant as an ESPHome device. You can then:

* Create **Lovelace Dashboards** to display information on the device's screen.
* Set up **Automations** based on inputs from the device (e.g., if you add a button).
* Send commands to the device from Home Assistant (e.g., to change display content).

Refer to the ESPHome documentation for detailed information on how to configure display components and other functionalities:
* [ESPHome Display Component](https://esphome.io/components/display/index.html)

## Contributing

Contributions are welcome! If you have suggestions for improvements, new features, or bug fixes, please feel free to:

1.  Fork this repository.
2.  Create a new branch (`git checkout -b feature/your-feature`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'Add some feature'`).
5.  Push to the branch (`git push origin feature/your-feature`).
6.  Open a Pull Request.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

* The **ESPHome** community for providing such an excellent framework.
* **Home Assistant** for being the cornerstone of home automation.
* **FreeCAD** and **PrusaSlicer** for the powerful open-source 3D design and slicing tools.
* **Creality** for the reliable Ender 3v2 3D printer.
* **CYD** for the versatile ESP32-2032S028R board.
