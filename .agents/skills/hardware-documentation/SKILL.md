---
name: hardware-documentation
description: Standards and templates for documenting hardware components, microcontrollers, circuits, pinouts, and sensors.
---

# Hardware Documentation Skill

Use this skill whenever working on hardware projects, embedded systems, robotics, IoT devices, microcontrollers (ESP32, Arduino, STM32, Raspberry Pi, etc.), sensors, actuators, or PCB design.

## Purpose
Hardware systems require exact, unambiguous specifications to avoid component damage, wiring mistakes, or logic-level mismatches. Every hardware project or physical device must have a dedicated `.md` file following the standard template.

## When to Create a Hardware Document
* A new microcontroller or SBC is introduced.
* Peripheral hardware (sensors, displays, motors, relays, radios) is added.
* Wiring harnesses, pinout assignments, or power distribution change.
* New firmware drivers are developed targeting specific hardware registers or buses.

## Documentation Requirements
Every hardware document must capture:
1. **System & Board Overview**: Processor model, operating voltage ($3.3\text{V}$ vs $5\text{V}$), clock frequency, flash/RAM, power source.
2. **Pinout & Wiring Map**: A comprehensive table linking microcontroller GPIOs to peripheral pins, including bus type (I2C, SPI, UART, PWM, ADC, GPIO) and pull-up/pull-down requirements.
3. **Power Budget**: Current draw under idle vs. peak loads, voltage regulator ratings, thermal notes.
4. **Communication Protocols**: I2C addresses (hex), SPI modes and clock frequencies, baud rates for UART.
5. **Bill of Materials (BOM)**: Part numbers, suppliers, and ratings.
6. **Datasheets & References**: Stored or referenced in `.agents/wiki/raw/`.

## Reusable Template
Use the template located at:
`.agents/skills/hardware-documentation/templates/HARDWARE_TEMPLATE.md`
Save project-specific hardware docs in `.agents/wiki/pages/` or in the project's root `docs/hardware/`.
