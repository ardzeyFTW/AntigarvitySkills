# Hardware Specification: [Device / Subsystem Name]

- **Document Version**: v1.0.0
- **Last Updated**: [YYYY-MM-DD]
- **Status**: [Draft / In-Testing / Verified / Deprecated]
- **Target Microcontroller / Platform**: [e.g., ESP32-WROOM-32 / Raspberry Pi Pico / STM32F401]

---

## 1. System Overview
* **Primary Function**: [Brief description of what this hardware module does]
* **Operating Logic Level**: [3.3V / 5.0V / Mixed]
* **Operating Temperature Range**: [e.g., -20°C to 85°C]
* **Form Factor / Dimensions**: [e.g., Custom PCB 50x30mm]

---

## 2. Power Specifications & Budget

| Rail / Line | Voltage | Idle Current | Peak Current | Source / Regulator | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `V_IN` | 5.0V - 12.0V | 10 mA | 1.5 A | USB / External DC Jack | Main input |
| `3V3` | 3.3V ± 2% | 45 mA | 500 mA | AMS1117-3.3 LDO | Logic supply |
| `5V_PERIPH` | 5.0V | 100 mA | 1.2 A | Buck converter | Motor / Relay power |

> [!WARNING]
> [Highlight any strict electrical constraints, e.g., "Do not power motors directly from the 3.3V microcontroller rail!"]

---

## 3. Pinout & GPIO Mapping Table

| MCU Pin / GPIO | Pin Function | Target Peripheral | Peripheral Pin | Bus / Signal | Pull-up / Resistor | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `GPIO 21` | SDA | BME280 Sensor | SDA | I2C | 4.7kΩ to 3.3V | Primary I2C bus |
| `GPIO 22` | SCL | BME280 Sensor | SCL | I2C | 4.7kΩ to 3.3V | Primary I2C bus |
| `GPIO 18` | SCK | ST7789 Display | SCL/CLK | SPI | None | 40 MHz max SPI |
| `GPIO 23` | MOSI | ST7789 Display | SDA/MOSI | SPI | None | Hardware SPI |
| `GPIO 4` | Output | Status LED | Anode | Digital Out | 330Ω in series | Active HIGH |
| `GPIO 34` | ADC1_CH6 | Battery Voltage | Voltage Divider | Analog In | 100kΩ / 100kΩ | Input only pin |

---

## 4. Bus & Protocol Configurations

### I2C Bus Configuration
- **Bus Speed**: [100 kHz (Standard) / 400 kHz (Fast Mode)]
- **Active Devices on Bus**:
  - `0x76`: BME280 Temperature / Humidity / Pressure sensor
  - `0x3C`: SSD1306 OLED Display (Optional)

### SPI Bus Configuration
- **SPI Mode**: [Mode 0 (CPOL=0, CPHA=0) / Mode 3]
- **Clock Frequency**: [e.g., 20 MHz]
- **Chip Select (CS) Pins**:
  - Display: `GPIO 5`
  - SD Card: `GPIO 15`

### UART / Serial
- **Baud Rate**: [e.g., 115200]
- **Data Bits / Parity / Stop**: [8N1]
- **Pins**: TX = `GPIO 1`, RX = `GPIO 3`

---

## 5. Bill of Materials (BOM)

| Item # | Part Name | Description / Value | Package / Footprint | Quantity | Part Number / Link |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | ESP32-DevKitC | ESP32 MCU Board | 38-pin DIP | 1 | ESP32-WROOM-32D |
| 2 | BME280 Module | Environmental Sensor | Breakout Board | 1 | Adafruit #2652 |
| 3 | Resistor | 4.7kΩ 5% | 0805 SMD or Through-hole | 2 | RC0805JR-074K7L |
| 4 | Ceramic Cap | 100nF 50V | 0805 SMD | 3 | Decoupling caps |

---

## 6. Schematics & Wiring Diagrams
- Schematic source files: `docs/hardware/schematics/`
- Rendered block diagram or circuit image:
```
       +-----------------------+
       |   ESP32 Microcontroller|
       |                       |
       |  GPIO 21 (SDA) -------> BME280 (SDA) [4.7k pull-up]
       |  GPIO 22 (SCL) -------> BME280 (SCL) [4.7k pull-up]
       |  3.3V          -------> VCC
       |  GND           -------> GND
       +-----------------------+
```

---

## 7. Known Quirks, Errata & Troubleshooting
- [e.g., GPIO 0, 2, 12, 15 are strapping pins; must not be pulled low during boot.]
- [e.g., ADC2 cannot be used when Wi-Fi is active on ESP32.]
