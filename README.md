# RF Sentinel

RF Sentinel is a low-cost RF activity monitoring and anomaly-detection project. Its goal is to observe radio-frequency activity, establish a baseline for the environment, and flag unusual changes for review.

> **Project status:** The repository currently contains a project description only. The components and workflow below are a planning checklist, not claims that these features are already implemented.

## What the project is intended to do

- Capture RF energy or spectrum measurements over a chosen frequency range.
- Record time-stamped observations so activity can be compared over time.
- Visualize activity and highlight readings that differ from a baseline.
- Keep the design affordable and modular, with room to use more capable hardware where needed.

RF monitoring reveals signal activity, not necessarily the content or identity of a transmitter. Results depend on the receiver, antenna, local environment, and applicable radio regulations.

## What is needed

### Hardware

- **RF receiver:** An SDR (software-defined radio) supported by the selected software. Entry-level USB SDR hardware can be used for receive-only experiments; wider frequency coverage or better dynamic range may require a higher-spec device.
- **Antenna:** An antenna suitable for the frequencies being observed. One antenna will not perform equally well across every band.
- **Computer:** A laptop, desktop, or single-board computer with a USB port and enough storage for captured measurements.
- **Optional accessories:** USB extension cable, antenna adapters, filters, and a low-noise amplifier, chosen for the intended band and local signal conditions.

### Software

- Operating system and SDR driver supported by the receiver.
- SDR capture and tuning software or libraries compatible with the device.
- Analysis code for cleaning measurements, extracting features, and identifying outliers.
- A way to store time-stamped measurements (for example, CSV or a small database).
- Optional dashboard or plotting tool for reviewing spectrum and anomaly history.

Specific package names and installation commands should be added once the receiver and implementation language are selected.

### Data and configuration

- Frequency range(s), sampling rate, gain, and scan interval appropriate to the receiver and use case.
- Baseline observations collected in the target environment.
- A defined anomaly rule or model, with thresholds that can be tuned to reduce false alerts.
- Storage limits and retention policy for captured data.

## Suggested workflow

1. Choose a receiver and the frequency range to monitor.
2. Install its driver and verify that ordinary receive measurements work.
3. Capture a short sample and save it with timestamps and configuration details.
4. Build a baseline from representative observations.
5. Compare new observations with the baseline and flag deviations.
6. Review flagged events and tune thresholds before relying on alerts.

## Safety and responsible use

Use receive-only equipment unless you are specifically authorized to transmit. Follow local spectrum, privacy, and recording laws. Do not attempt to decode private communications or interfere with radio services. Check the receiver's frequency limits and local rules before operating.

## Current repository state

The repository is being set up. Add the implementation, supported receiver models, tested software versions, setup instructions, and example output as those are established.
