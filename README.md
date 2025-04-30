# EspSynth
## ESP32-S3 Modular Digital Synthesizer

## Project Goal

An open-source project to design and build a highly flexible, expandable, and powerful digital modular synthesizer utilizing the capabilities of multiple networked ESP32-S3 microcontrollers.

## Key Features

* **Truly Modular Architecture:** Each core function (Oscillator, Filter, FX, etc.) runs on its own dedicated ESP32-S3 module.
* **High-Quality Audio:** Leverages I2S TDM (Time-Division Multiplexing) for efficient multi-channel digital audio routing between modules.
* **Powerful Processing:** Utilizes the dual-core performance and DSP capabilities of the ESP32-S3.
* **Flexible Virtual Patching:** A central controller manages audio and modulation routing via a user-friendly interface, configuring the I2S TDM paths.
* **Per-Module Configuration & Display:** Most modules feature a local OLED display (SSD1306) and encoder, allowing configuration (like setting unique I2C addresses) and status feedback directly on the module.
* **External Control:** Planned support for OSC (Open Sound Control) and MIDI via USB OTG and/or Wi-Fi.
* **Open Source:** Hardware schematics (KiCad planned), firmware (ESP-IDF based), and documentation will be available under permissive licenses.

## Architecture Overview

The system consists of several types of interconnected modules:

1.  **Central Controller:** The brain of the system. Handles the main user interface (color display, pots, buttons), manages the virtual patch matrix, communicates with all modules via a multiplexed I2C control bus, and handles external OSC/MIDI communication.
2.  **Processing Modules (Oscillator, Filter, Effects, LFO, Mixer):** Dedicated ESP32-S3 modules performing specific DSP tasks. They receive/send audio via I2S TDM and are configured via the main I2C bus. Each features a local OLED display and encoder for address setup and status.
3.  **I/O Modules:**
    * **ADC Input Module:** Digitizes external audio signals (using PCM1808) and places them onto the I2S TDM bus.
    * **DAC Output Module:** Receives the final mix via I2S TDM, generates the master audio clocks (MCLK, BCLK, WS) for the entire system, and outputs analog audio (using UDA1334A).

## Technology Stack

* **Microcontroller:** Espressif ESP32-S3 (primarily DevKitC-1-N32R8V and N8R2 variants)
* **Framework:** Espressif IoT Development Framework (ESP-IDF) with FreeRTOS
* **Audio Transport:** I2S TDM
* **Control Transport:** I2C (multiplexed main bus + local display buses)
* **Peripherals:** SSD1336 (Color OLED), SSD1306 (Monochrome OLED), Rotary Encoders, PCM1808 (ADC), UDA1334A (DAC), TCA9548A (I2C Mux)
* **Connectivity:** Wi-Fi (for OSC), USB OTG (for MIDI/OSC)

## Project Status

*Work in Progress* - Currently in the detailed design and early prototyping phase.

## Contributing

*(Optional: Add contribution guidelines later)*
We welcome collaboration! Feel free to open issues for questions, suggestions, or bug reports.

*(Optional: Add links to Wiki, schematics folder, etc. later)*
