# esp32-weather-station-pcb
Hardware design and PCB manufacturing files for an ESP32-based Personal Weather Station. Features real-time I2C environmental monitoring (BME280) and OLED display.
# Personal Weather Station: PCB & Hardware Design

## About the Project
This repository contains the complete hardware design, schematic capture, and PCB manufacturing files for a modular **Personal Weather Station**. The system is designed to collect real-time environmental data (Temperature, Humidity, and Atmospheric Pressure) and provide instant visual feedback to the user.

**Academic Context:** Hardware design and validation project developed for the Applied Electronics Project (ELTi2220) course at the Federal University of Itajubá (UNIFEI) - Campus Itabira.  
*Collaborators:* Frederico Gomes, João Henrique de Menezes, and Rodrigo Vieira.

## Hardware Architecture
The board was designed with a strong focus on modularity, signal integrity, and manufacturing compliance. 

**Core Components:**
* **Microcontroller:** ESP32-WROOM-32E (Operates at 3.3V).
* **Power Management:** AMS1117-3.3V linear regulator. It steps down the 5V Micro-USB input to a stable 3.3V, supported by dedicated decoupling capacitors (10µF input / 22µF output) to handle Wi-Fi power spikes.
* **Environmental Sensor:** BME280 module via I2C (connected via female pin headers for easy replacement).
* **Display:** 0.96" OLED SSD1306 via I2C for real-time data visualization.
* **External Programming:**UART (TXD/RXD) interface implemented via a 1x06 PinHeader to optimize PCB costs by bypassing an onboard USB-to-Serial converter.

## Smart Feedback System
In addition to the OLED display, the board features a common-cathode **RGB LED** that provides immediate visual feedback regarding the ambient temperature:
* 🔵 **Blue:** Below 20°C (Cold)
* 🟢 **Green:** Between 20°C and 30°C (Comfortable)
* 🔴 **Red:** Above 30°C (Hot)
*(Note: Individual resistors were calculated to balance the forward voltage differences of each internal LED).*

## PCB Layout & Manufacturing
The PCB layout was optimized for size (48.69 x 42.82 mm) and stability.
* **Ground Plane:** A continuous copper ground pour was implemented across the board to enhance electrical stability and shield against high-frequency noise.
* **Validation:** The board passed a strict Design Rule Check (DRC) with a minimum clearance of 0.127 mm, ensuring it is 100% free of shorts and open circuits.
* **Fabrication:** The repository includes standard **Gerber and Drill (.drl) files** ready for manufacturing at standard PCB houses (e.g., JLCPCB).

## Technologies Used
* **KiCad EDA:** Schematic creation, PCB routing, and 3D visualization.
* **ESP32 Framework**
