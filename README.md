# RF Sentinel

**RF Sentinel** is a student research prototype exploring passive, non-camera sensing of changes in ambient **4G/5G cellular RF signals**. The research goal is to study whether measured changes can correspond to movement or environmental changes in controlled spaces.

> **Status:** The supplied project material says the cellular RF sensing research and high-level architecture are complete. Hardware sourcing and integration are in progress. A compatible 4G/5G RF module and antenna remain the key sourcing blocker; controlled RF sampling and performance validation are pending. No sensing accuracy, detection range, or validated movement-detection performance is claimed.

## Project concept

The proposed measurement flow is:

`Ambient cellular RF → compatible RF front-end / modem / SDR → measurements or samples → analysis and comparison`

An **ESP32 controller** is planned for supported peripheral control, OLED status, and logging. The external RF hardware is essential: an ESP32 alone is not a general-purpose 4G/5G receiver. Depending on the selected RF hardware, data acquisition or signal processing may require its vendor software or a host computer.

The research aims to explore changes in RF observations under controlled conditions. A measured difference alone does not prove movement or identify its cause.

## Proposed system components

| Component | Intended role | Status / detail to confirm |
| --- | --- | --- |
| ESP32 controller | Peripheral control, OLED, logging, and prototype interface | Architecture defined; exact model and interfaces not specified |
| 4G/5G RF front-end, modem, or SDR | Provides access to cellular RF measurements or samples | Not yet sourced; key dependency |
| Cellular antenna | Receives target bands | Must match the selected receiver and bands; not yet sourced |
| OLED display | Local status and available results | Listed; exact model/interface unspecified |
| Power circuitry | Provides stable power to controller and RF hardware | Ratings depend on selected components |
| RF cables and adapters | Connect antenna and receiver | Connector and coax types depend on selected hardware |

The exact cellular bands, bandwidth, sample format, receiver interface, and pin assignments remain undecided until the RF module is selected. The final circuit diagram is pending and must be verified against component documentation.

## Software and tools

The supplied project references identify these tools as selected or possible:

- **Arduino IDE 2** for developing, compiling, and uploading ESP32 firmware.
- **ESP-IDF or Arduino C/C++** for controller firmware, OLED, interfaces, and logging; the final framework choice remains to be recorded.
- **Vendor SDK/API** for the selected RF module or modem.
- **GNU Radio or SoapySDR** as possible SDR integration tools, depending on the selected hardware.
- **Python: NumPy, SciPy, Pandas, and Matplotlib** for planned data handling, signal-feature analysis, and plots.
- **Cirkit Designer** for circuit planning and wiring validation.

These are project workflow references, not confirmation that the acquisition or analysis software has been implemented and tested.

## Proposed workflow

1. Select a compatible RF module, modem, or SDR based on the measurements needed, supported bands, interface, cost, and availability.
2. Select a matching cellular antenna, RF connectors, cables, and suitable power supply.
3. Confirm what measurements or samples the chosen hardware exposes and how the ESP32 or a host computer communicates with it.
4. Complete and verify the circuit design using the selected components' documentation.
5. Implement acquisition, status display, and logging for the available measurement path.
6. Record a labeled baseline under controlled conditions.
7. Introduce one documented environmental change and collect another observation using the same configuration where possible.
8. Compare the recorded data, repeat trials, and report observed differences with their limitations.

The system should report connection, acquisition, or storage errors as errors; missing data should not be treated as a detection.

## Current progress

- [x] Research area identified: cellular RF sensing and 5G Integrated Sensing and Communication (ISAC)
- [x] High-level ESP32 + RF hardware + antenna + OLED architecture defined
- [x] Arduino IDE and Cirkit Designer selected in project references
- [ ] Source a compatible 4G/5G RF module or SDR and antenna
- [ ] Confirm RF bands, exposed measurements, interfaces, connectors, and power requirements
- [ ] Complete and verify the final circuit
- [ ] Integrate hardware and implement acquisition and logging
- [ ] Collect controlled baseline and changed-condition observations
- [ ] Evaluate repeatability and sensing performance

## Earlier concept in the proposal

An earlier mini-project proposal describes a different, simpler design using an **ESP32 and AD8307 RF detector** for analog signal-strength thresholding, with an OLED, LEDs, buzzer, and a proposed dashboard. It includes example thresholds, estimated component costs, and circuit pin suggestions. These are proposal details only: the later project report identifies the research direction as 4G/5G cellular RF sensing with a compatible external RF front-end/modem/SDR, and says the RF hardware has not yet been sourced. Do not treat the AD8307 design, its pinout, threshold examples, dashboard, or budget as the confirmed current build.

The later project report also mentions an ESP32-S3 Wi-Fi/BLE scanning concept in other project notes. That is distinct from the cellular RF sensing objective documented in the supplied project slides and report; this README follows the supplied 4G/5G research direction.

## Limitations and responsible use

- The RF receiver and antenna determine which signals and measurements are accessible.
- A modem may expose only limited network metrics; an SDR's frequency coverage, bandwidth, and software support depend on the specific model.
- RF changes may have multiple causes. Controlled, repeated experiments are needed before relating them to movement or environmental changes.
- This research prototype is not a validated security, surveillance, or safety device and cannot identify a person or prove that a transmission is unauthorized.
- Use authorized RF sources and follow applicable radio, privacy, and data-protection rules. Do not transmit or interfere with radio services.

## Reference tools

- [Arduino IDE 2](https://docs.arduino.cc/software/ide/)
- [GNU Radio](https://www.gnuradio.org/)
- [SoapySDR](https://github.com/pothosware/SoapySDR)
- [NumPy](https://numpy.org/)
- [SciPy](https://scipy.org/)
- [Pandas](https://pandas.pydata.org/)
- [Matplotlib](https://matplotlib.org/)
- [Cirkit Designer project workspace](https://app.cirkitdesigner.com/project/a3692bd9-b74a-498f-81d4-1cef88412a6e)

The supplied report does not provide complete citations for specific cellular RF sensing or 5G ISAC research papers. Add verified papers once selected and reviewed.
