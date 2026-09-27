# Edge AI-Enabled IoT-Based Cold Chain Monitoring System

## Overview

The **Edge AI-Enabled IoT-Based Cold Chain Monitoring System** is an IoT and embedded systems prototype designed for real-time monitoring of temperature-sensitive products during storage and transportation.

The system is built around an **ESP32-S3** microcontroller and integrates multiple sensing and communication modules to monitor critical parameters including **temperature, humidity, door status, GPS location, and electrical current**.

Sensor data is acquired and processed at the edge by the ESP32-S3. The system provides local alerts through a **buzzer and RGB LED** and supports wireless data transmission using **Bluetooth Low Energy (BLE)**.

The project demonstrates practical implementation of **IoT device integration, embedded programming, sensor interfacing, wireless communication, real-time monitoring, and hardware debugging**.

---

## Key Features

- Real-time temperature monitoring
- Real-time humidity monitoring
- Door-open/close detection
- GPS-based location tracking
- Electrical current monitoring
- BLE wireless communication
- Local audible alerts using a buzzer
- Visual status indication using RGB LED
- ESP32-S3-based edge processing
- Multi-sensor data acquisition
- Hardware-software integration
- Real-time system testing and debugging

---

## Problem Statement

Temperature-sensitive products such as pharmaceuticals, vaccines, biological materials, and perishable goods require controlled environmental conditions throughout storage and transportation.

A temperature excursion, unexpected door opening, power-related issue, or loss of location information can affect the condition of the transported product.

The objective of this project is to develop a compact IoT-based monitoring system capable of continuously collecting important environmental and operational parameters and providing immediate alerts when abnormal conditions occur.

---

## Proposed Solution

The system uses an **ESP32-S3** as the central controller.

Multiple sensors are connected to the ESP32-S3 to collect:

- Temperature
- Humidity
- Door status
- GPS location
- Electrical current

The ESP32-S3 processes the sensor data and performs the required monitoring logic.

The system then:

1. Acquires data from connected sensors.
2. Processes the readings on the ESP32-S3.
3. Checks monitored parameters against configured conditions.
4. Activates local alerts when required.
5. Transmits monitoring data using BLE.
6. Continuously repeats the monitoring cycle.

---

# System Architecture

```text
                    ┌──────────────────┐
                    │      DHT11       │
                    │ Temperature &    │
                    │    Humidity      │
                    └────────┬─────────┘
                             │
                             │
     ┌───────────────────────┼────────────────────────┐
     │                       │                        │
     ▼                       ▼                        ▼
┌─────────────┐       ┌─────────────┐         ┌─────────────┐
│ Reed Switch │       │   ACS712    │         │   NEO-6M    │
│ Door Status │       │   Current   │         │     GPS     │
└──────┬──────┘       │   Sensor    │         └──────┬──────┘
       │              └──────┬──────┘                │
       │                     │                        │
       └─────────────────────┼────────────────────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │      ESP32-S3        │
                  │   Main Controller    │
                  │   Edge Processing    │
                  └──────────┬──────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼
        ┌──────────┐    ┌──────────┐   ┌─────────────┐
        │  Buzzer  │    │ RGB LED  │   │     BLE     │
        │  Alert   │    │  Status  │   │Communication│
        └──────────┘    └──────────┘   └─────────────┘
