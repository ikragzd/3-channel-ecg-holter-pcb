# Portable 3-Channel ECG Holter Monitor PCB

A compact, 4-layer custom printed circuit board designed for continuous 24+ hour, 3-channel electrocardiogram data logging to a microSD card with on-demand Bluetooth Low Energy transfer.

> **Disclaimer:** This hardware is an open-source personal monitoring and engineering prototype. It is not a certified medical device and is not intended for clinical diagnosis. For electrical safety, ECG electrodes must be disconnected whenever the device is connected to USB for charging.

## Hardware Architecture
* **Analog Front-End:** Texas Instruments **ADS1293** 3-channel, 24-bit resolution biopotential AFE with hardware lead-off detection
* **Main Processor:** **ESP32 WROOM-32** module managing SPI communication, time-stamping, and user-triggered BLE transfer
* **Data Storage:** SPI **microSD** card slot with card-detect support for continuous raw waveform logging at 250 Hz or higher per channel
* **Real-Time Clock:** External **DS3231** class RTC ensuring accurate timestamps across battery cycles
* **Power & Charging:** **TP4056** protected LiPo battery charger, JST-PH 2.0 connector for 1000–2000mAh LiPo cells, reverse-polarity protection diode, and resistive voltage divider for low-battery monitoring
* **Programming Interface:** Onboard **CP2102 / CH340** USB-to-UART bridge for firmware flashing and serial debugging
* **Input Protection:** TVS ESD protection diodes and series current-limiting safety resistors across 4 to 5 ECG electrode inputs including RLD

## PCB Layout & Engineering Specifications
* **4-Layer Stackup & Star Grounding:** Dedicated analog and digital ground planes joined at a single star-ground point to prevent high-frequency noise from coupling into low-amplitude ECG traces.
* **RF & Analog Isolation:** Short, guarded analog traces near the electrode connector, with physical separation and a copper keep-out zone beneath the ESP32 internal antenna.
* **Mechanical & Reliability Targets:** Designed under 50 g total weight and 10 mm PCB thickness, featuring mounting holes, electrode cable strain relief, SPI/power test points, and conformal-coating compatibility targeting IP54 moisture resistance.

## Attribution
Derived from the open-source **ProtoCentral ADS1293 3-Channel ECG Breakout** hardware reference, licensed under Creative Commons Attribution-ShareAlike.
