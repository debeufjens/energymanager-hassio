# EnergyManager

This repository provides a complete guide for installing and setting up EnergyManager, an energy consumption monitoring and optimization system developed by Jens De Beuf as part of a research project for my bachelors thesis. EnergyManager is deployed on Home Assistant, an open-source home automation platform running on Python.

The system is intended for use in caravans to provide a detailed overview of energy usage, enabling users to effectively manage and optimize their power consumption. With the use of "modules" as IOT devices the system can be easily expanded and adapted to the user's needs.

## Contents

-   [EnergyManager Installation Guide](#energymanager-installation-guide)
    -   [Contents](#contents)
    -   [Overview](#overview)
    -   [Requirements](#requirements)
    -   [Setup](#setup)
        -   [Installation of Raspberry Pi OS](#installation-of-raspberry-pi-os)
        -   [Configuring Access Point Mode](#configuring-access-point-mode)
        -   [Installation of Home Assistant](#installation-of-home-assistant)
        -   [Installation of ESPHome](#installation-of-esphome)
        -   [Configuring ESPHome](#configuring-esphome)
    -   [Installation of IoT Devices](#installation-of-iot-devices)
    -   [Dashboard Configuration](#dashboard-configuration)
    -   [Automations](#automations)

## Overview

The EnergyManager system monitors the energy consumption of various AC circuits within a caravan. It allows users to turn different circuits on and off, helping to save power on circuits that are not currently needed. The user-friendly interface of Home Assistant facilitates visualization of the devices, current measurements, and charts.

## Requirements

-   Raspberry Pi 4 (minimum 4G RAM)
-   2x ESP32 or ESP8266
-   433 MHz motion detector
-   433MHz receiver (e.g., HC-12)
-   4-way relay module (230v 10A)
-   38KHz infrared transmitter and receiver module
-   Jumper cables
-   4x ACS712 hall effect sensors (20A max)

## Setup

### Installation of Raspberry Pi OS

Raspberry Pi OS 64-bit should be installed on the Raspberry Pi, which will be followed by the installation of Home Assistant and related components.

### Configuring Access Point Mode

This ensures that we have our own Wi-Fi network to communicate with the modules and with the application. You can enable this mode step by step via [this guide](https://thepi.io/how-to-use-your-raspberry-pi-as-a-wireless-access-point/), ensuring that the passthrough of the Ethernet interface is also executed.

### Installation of Home Assistant

The method to be used for installing Home Assistant on a Raspberry Pi is "Supervised" because it supports add-ons, a crucial function needed in this project.

Follow the installation guide [here](https://community.home-assistant.io/t/guide-how-to-install-home-assistant-supervised-on-rpi4-with-raspios-64-bit-october-2022/480855).

### Installation of ESPHome

ESPHome will be used to manage the IoT devices. ESPHome is ideal for this application since it enables the configuration of IoT devices through YAML configuration files.

### Configuring ESPHome

After successful installation of the ESPHome Addon, devices can be added via the "+ New Device" button. You must first set the Wi-Fi SSID and password through the secrets.yaml so that the devices can connect to your Home Assistant installation.

## Installation of IoT Devices

The project includes the setup of a Power Module and an IR & RF module. The power module is responsible for all AC circuits, and the IR & RF module is for communication with various devices, such as an air conditioning unit and a motion detector.

For detailed installation and configuration guide, refer to the [original Dutch guide](https://github.com/debeufjens/energymanager-hassio/tree/main/instructions_dutch) .

## Dashboard Configuration

The dashboard is important for managing and viewing the entire system. Components can be added, edited, and configured using Home Assistant's Lovelace UI.

## Automations

Home Assistant provides an easy-to-use interface for creating automation scenarios. This can help automate processes based on set conditions.
