# NOTICE

## Bitair Mainboard

Copyright (c) 2026 Heatbit Inc.

This hardware design is licensed under the **CERN Open Hardware Licence
Version 2 – Strongly Reciprocal (CERN-OHL-S-2.0)**. See [LICENSE](LICENSE).

You may redistribute and modify this source and make products using it under
the terms of the CERN-OHL-S v2 (https://ohwr.org/cern_ohl_s_v2.txt).

This source is distributed WITHOUT ANY EXPRESS OR IMPLIED WARRANTY, INCLUDING
OF MERCHANTABILITY, SATISFACTORY QUALITY AND FITNESS FOR A PARTICULAR PURPOSE.
Please see the CERN-OHL-S v2 for applicable conditions.

The licence does not grant any rights to the Heatbit trademarks. See
[TRADEMARKS.md](TRADEMARKS.md).

## Upstream work

This design is a modified version of **bitaxeGamma**:

- Project: bitaxeGamma, part of the open source bitaxe Bitcoin miner project
- Copyright: (c) 2024-2025 bitaxeorg
- Source: https://github.com/bitaxeorg/bitaxeGamma
- Upstream revision used: commit `f04c421` (2025-10-07, "Remove LCSC barrel jack from BOM"), board revision 601
- Upstream licence: CERN-OHL-S-2.0

The `bitaxe.kicad_sym` symbol library, the `bitaxe.pretty` footprint library,
the BM1370, ESP32 and power-stage circuits, `assembly.md` and `building.md`
come from the upstream project. Heatbit Inc. modified them as described below.

## Modifications by Heatbit Inc.

Heatbit Inc. adapted bitaxeGamma 601 into the mainboard of a Bitcoin-mining
air purifier. The changes compared with upstream `f04c421`:

**2026-07-10 — V1.00 (first internal revision, used for debugging only)**

- New board outline and layout that fit the Heatbit air purifier enclosure.
  The ASIC, core power stage and ESP32 placement were re-laid out.
- Power input: removed the 5 V barrel jack (J1, 54-00164). The board is now
  powered through the 10-pin connector CN1 (VBUS). A new step-down converter
  makes the 5 V rail (sheet `Power_15_5`): NDP1415QF controller (U1),
  HSBA3056 MOSFETs (Q1, Q2), inductor L2 (FEXL0660A-5R6M), fuse F1 (3 A),
  and input/output bulk capacitors C54, C55, C61, C63 and C64.
- Added the system connector CN1 to the purifier (JST S10B-PHDSS, right-angle):
  power input, fan, fan PWM, LED and GPIOs.
- Added VBUS voltage sensing on ESP32 GPIO6 (R94/R95 divider, D18 clamp, C104).
- Added the FAN line on CN1: ESP32 GPIO40 through the MOSFET level shifter Q3.
- J1 is reused as a 6-pin ESP32 UART/boot programming header (3V3, TX, RX,
  GND, IO0, EN).
- Removed: display header J3, fan connectors J6/J7, Tag-Connect J2, header J4,
  mounting holes H1–H8, C3, C15 and several test points. Added
  SMT standoffs MT1–MT4 (SMTSO3025CTJ) and ground terminals X1/X2 (T34069).
- Replaced buttons SW1/SW2 with C&K KMS2xxG.
- C19/C20 changed from 100 µF to 220 µF (Panasonic 6TPE220MAZB). Added
  C66/C67 220 µF. Added C65.
- Added voltage ratings to capacitor values and LCSC part numbers to all
  parts. Changed the R24 value (5.6k → 5.1k). R22/R23 now use the standard
  `Device:R` symbol.
- Added Heatbit libraries `Heatbit.kicad_sym` / `Heatbit.pretty` and
  `bitair.kicad_sym` / `bitair.pretty` (parts imported from
  LCSC/EasyEDA).
- Heatbit branding on copper and silkscreen.

**2026-07-31 — V1.11 (internal revision, used for debugging only)**

- X1/X2 terminals moved to the bottom side. CN1 moved to the bottom side and
  changed to the vertical B10B-PHDSS-LF-SN. CN1 pins 5/7/9 swapped with 6/8/10.
- CN1 pins 5 and 7: I2C for an AHT20 temperature/humidity sensor, with
  level shifters Q4/Q5 and I2C pull-ups R43/R44 (4.7 kΩ).
- Removed fiducials FID1–FID8 and C53.
- Added a 5.1 kΩ pull-down on the BM1370 reset (R41).
- Fan PWM moved from the EMC2101 to ESP32 GPIO35.
- R29 = R30 = 4.7 Ω (was 20 Ω), R20 = 2 MΩ (was 1.1 MΩ), R26 = 220 kΩ (was 100 kΩ).
- L2 replaced by FXL1050-4R7-M.

**2026-08-24 — V1.22 (production revision)**

- Fan PWM removed from GPIO35 and returned to the EMC2101.
- Removed test point TP6.

**2026-10 — preparation for open source release**

- Added NOTICE.md, TRADEMARKS.md, THIRD_PARTY.md and CHANGELOG.md, and
  rewrote README.md. Restored the attribution to the upstream project.
- Added copyright and licence comments to the schematic and PCB title blocks.
- Removed unused 3D models, unused Heatbit library symbols and footprints, and
  the unused `mining board maxi pro.kicad_sym` library.
- Normalised part-number fields in the schematic and regenerated the BOM.
- Converted the project to KiCad 10 format.
- Renamed the project files from `bitaxeGamma.*` to `bitair-mainboard.*`
  and the Heatbit library `bitaxeGamma` to `bitair`. The upstream `bitaxe`
  libraries keep their names.
