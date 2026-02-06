# mdc-power-p6
Modular Detector Controller Power 6V DC-DC Module

## Overview
12V input to 6V output DC-DC module, 3A nominal output, used as one of the `mdc-power-*` bias rails.
Designed for 2 MHz sync operation.

## Power Stage
- Controller: `LT8624S` (`U1`)
  - Silent Switcher 3 synchronous step-down regulator.
  - Ultralow EMI emissions and high efficiency at high switching frequency.
  - Constant-frequency current-mode control.
  - External sync capability.
- Inductor: `L1` = `2.2uH`
  - Uses the XGL4020 shielded power inductor family (see `docs/xgl4020.pdf`).
  - Shielded construction to reduce radiated EMI and coupling into sensitive nodes.
  - Very low DCR family to reduce copper loss and improve efficiency.
  - Low AC loss construction optimized for high-frequency switching.

## Files
- Schematic: `power_p6.pdf`
- Simulation: `sim/` (LTspice and LTpowerCAD files used for loop and transient checks)

## Interface
- Control pins: `EN` (enable) and `PG` / `~PGOOD` (power good).
- Connector: `LSHM-140-04.0-L-DV-A-N-K-TR` (Samtec LSHM series) mezzanine for power and control signals.
  - Common pinout is shared across the 16V, -16V, 6V, and 3.3V variants.
  - Unused output rails are tied to GND on the specific module variant.
