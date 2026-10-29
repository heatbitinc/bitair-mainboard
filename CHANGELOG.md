# Changelog

All dates are release dates in this repository. The differences from
upstream bitaxeGamma are listed in [NOTICE.md](NOTICE.md).

## V1.22 (2026-08-24): production

- 3.1 Removed FAN_PWM from GPIO35.
- 5.1 Added FAN_PWM back to the EMC2101.

## V1.11 (2026-07-31): internal, debugging only

- 1.1 X1 and X2 terminals moved to the bottom side.
- 1.2 CN1 pins 5, 7, 9 mirrored with 6, 8, 10.
- 1.3 CN1 replaced by B10B-PHDSS-LF-SN (vertical).
- 1.4 CN1 pins 5 and 7: added I2C for the AHT20 temperature sensor.
- 1.5 CN1 moved to the bottom side.
- 1.6 Fiducials removed.
- 3.1 Added FAN_PWM on GPIO35.
- 4.1 Added a 5.1 kΩ pull-down R41 (BM1370 RST).
- 4.2 Added 4.7 kΩ I2C pull-ups.
- 5.1 Removed FAN_PWM control from the EMC2101.
- 6.1 R29 = R30 = 4.7 Ω.
- 6.2 R20 = 2 MΩ, R26 = 220 kΩ.
- 6.3 L2 replaced by FXL1050-4R7-M.

## V1.00 (2026-07-10): internal, debugging only

- First Heatbit revision, based on bitaxeGamma 601 (upstream commit `f04c421`).
