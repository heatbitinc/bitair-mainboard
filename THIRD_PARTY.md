# Third-party material

The CERN-OHL-S-2.0 licence of this repository covers the design work of the
bitaxe project and of Heatbit Inc. The files listed below come from component
vendors or library services. They remain under their original terms and are
included only so the 3D view of the board is complete. They are not needed to
manufacture the PCB.

## KiCad standard libraries

Footprints and 3D models referenced as `${KICAD*_3DMODEL_DIR}/...` and
footprints from the standard KiCad libraries (`Capacitor_SMD`,
`Resistor_SMD`, `Package_TO_SOT_SMD`, ...) are not stored in this repository.
They are distributed with KiCad under CC-BY-SA 4.0 with the KiCad library
exception.

## 3D models stored in this repository

| File | Used by | Origin | Notes |
|------|---------|--------|-------|
| `3d/bm1370.step` | U8 BM1370 | Heatbit | Generated in KiCad / Open CASCADE |
| `3d/Heatsink.STEP` | U8 (heatsink) | Heatbit | Heatsink used in the Bitair purifier |
| `3d/Coilcraft-SLC1175.STEP` | L1 | Coilcraft, via upstream bitaxe | Vendor model |
| `3d/ESP32-S3-WROOM-1-N8R2--3DModel-STEP-56544.STEP` | U4 | Espressif model, via upstream bitaxe | Vendor model |
| `3d/TPS546D24ARVFR.step` | U2 | Texas Instruments, via upstream bitaxe | Vendor model |
| `3d/TSOT-23-5_RIT.step` | U3 | via upstream bitaxe | Vendor model |
| `3d/oscillator3.2x2.5.step` | U7 | ECS (ECS-327KE), via upstream bitaxe | Vendor model |
| `3d/KMS231GPLFS.stp` | SW1, SW2 | C&K, exported from CADENAS PARTsolutions | Vendor model, check the redistribution terms |
| `3dshapes/*.step` (9 files) | C19, C20, C66, C67, CN1, L2, Q1, Q2, U1, MT1–MT4, D1, D2, X1, X2 | LCSC / EasyEDA, converted with easyeda2kicad | Library-service models, check the redistribution terms |

## Libraries

- `bitaxe.kicad_sym`, `bitaxe.pretty`: from the upstream bitaxe project
  (CERN-OHL-S-2.0).
- `bitair.kicad_sym`, `bitair.pretty`: added by Heatbit. Most parts
  were imported from LCSC/EasyEDA with easyeda2kicad and then edited.
- `Heatbit.kicad_sym`, `Heatbit.pretty`: added by Heatbit.

## Silicon

The BM1370 ASIC is a proprietary Bitmain part. Its datasheet is not public,
and the footprint and pinout come from the bitaxe project.
