# RF Sentinel

**RF Sentinel** is a portable, low-cost wireless activity monitoring project built around an **ESP32-S3**. It scans nearby Wi-Fi networks and Bluetooth Low Energy (BLE) devices, saves observations to a microSD card as CSV, and lets the user compare activity from before and after a chosen event or period.

> **Project status:** The hardware is partially assembled and testing is pending. This README describes the confirmed project design and intended behavior; it does not claim validated detection accuracy or completed testing.

## Project goals

- Observe nearby Wi-Fi and BLE activity using the ESP32-S3.
- Record scan observations locally for later review.
- Establish a **BEFORE** baseline, collect an **AFTER** scan, and use **COMPARE** to highlight changes such as newly observed devices.
- Provide a simple, portable interface through an OLED display and physical buttons.

RF Sentinel is intended as a wireless-environment monitoring aid. A change in scan results may warrant investigation, but it does not establish that a device is hidden, unauthorized, or malicious.

## Confirmed hardware

- ESP32-S3 development board
- OLED display
- Physical buttons
- MicroSD card and compatible reader/interface

No dedicated wideband RF receiver or external RF detector is part of the confirmed current design. The current scope is Wi-Fi and BLE activity that the ESP32-S3 can observe.

## Intended operation

1. **BEFORE:** Scan the environment and save a baseline.
2. **AFTER:** Scan again at the later time or after the event.
3. **COMPARE:** Compare the two sets of observations and show changes.
4. **CSV logging:** Store scan records on the microSD card for offline review.

Depending on what the ESP32-S3 scan APIs expose, records may include available identifiers, signal strength (RSSI), and timestamps. Exact CSV columns and display behavior should be documented after implementation and testing confirm them.

## What is needed

### Hardware

- ESP32-S3 development board
- OLED display compatible with the chosen interface (for example, I²C or SPI)
- Buttons for menu and mode selection
- MicroSD card module or board interface, plus a microSD card
- Connecting wires, a stable power source, and any adapters required by the selected board
- Optional enclosure for portable use

Pin assignments, voltage levels, and wiring depend on the specific ESP32-S3 board and peripheral modules; confirm them against the relevant board/module documentation before connecting hardware.

### Software and tools

- A development environment that supports the ESP32-S3, such as Arduino IDE or ESP-IDF (choose one for the project)
- ESP32-S3 board support package and USB/serial drivers as required by the computer
- Wi-Fi scanning and BLE scanning APIs/libraries compatible with the chosen framework
- OLED display library compatible with the display controller and bus
- SD or FAT filesystem support for writing CSV files
- USB data cable and a computer for building, flashing, and serial debugging

The exact framework versions, library names, and installation steps remain to be confirmed by the implementation.

### Data and testing

- A microSD card formatted in a filesystem supported by the selected SD library
- A repeatable scan procedure and a clear definition of what counts as a “new” or changed observation
- Test runs in a controlled environment to check Wi-Fi/BLE scans, display controls, CSV integrity, and BEFORE/AFTER comparison
- Validation of practical limitations such as scan duration, missed or rotating identifiers, signal-strength variation, and false alerts

## Current status and next steps

- [x] Project concept and core hardware identified
- [x] BEFORE / AFTER / COMPARE workflow defined
- [x] CSV logging identified as a feature
- [ ] Complete hardware assembly
- [ ] Confirm board pinout, display type, and SD interface
- [ ] Implement and verify Wi-Fi and BLE scans
- [ ] Implement OLED/button menus and CSV logging
- [ ] Test and document the comparison rules and limitations

## Responsible use

Use RF Sentinel only where you have permission to monitor the environment. Follow applicable radio, privacy, and data-protection rules. The project records observable wireless metadata; it is not intended to intercept or decode private communications, transmit RF signals, or interfere with wireless services.

## Future scope

Possible future work includes clearer anomaly scoring, improved summaries, and optional dedicated RF sensing hardware. These are not part of the confirmed current prototype.
