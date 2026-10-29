# Building PCBs

> Based on `building.md` from the bitaxe project (bitaxeorg). Heatbit
> updated it for KiCad 10 and this board.

Ready-made fabrication files for V1.22 are in `OUTPUTS/`. Regenerate them
only if you change the design.

To get PCBs made, you usually need to give the manufacturer:

- Gerbers
- Drill files

If you want a shop to assemble the boards for you, you also need:

- Bill of materials (BOM)
- Centroid / pick-and-place file (XY)

The PCB has 4 layers (F.Cu, In1.Cu, In2.Cu, B.Cu) and parts on both sides.

## Generating Gerbers and drill files

### KiCad GUI

1. Open `bitair-mainboard.kicad_pro` in KiCad 10 and open the PCB editor.
2. Press **B** to refill all zones, then run **Inspect → Design Rules Checker**.
3. Choose **File → Fabrication Outputs → Gerbers (.gbr)…**. Include these
   layers: F.Cu, In1.Cu, In2.Cu, B.Cu, F.Paste, B.Paste, F.Silkscreen,
   B.Silkscreen, F.Mask, B.Mask, Edge.Cuts.
4. In the same dialog, click **Generate Drill Files…** and generate the
   drill files as your PCB house specifies.

The paste layers (`-F_Paste.gbr`, `-B_Paste.gbr`) are only needed to order
stencils. Paste Gerbers are not needed to manufacture the PCB itself.

### Command line (kicad-cli)

```sh
kicad-cli pcb export gerbers \
  --layers F.Cu,In1.Cu,In2.Cu,B.Cu,F.Paste,B.Paste,F.Silkscreen,B.Silkscreen,F.Mask,B.Mask,Edge.Cuts \
  --output "OUTPUTS/HB Bitair MainBoard V1.22 GBR/" bitair-mainboard.kicad_pcb
kicad-cli pcb export drill --output "OUTPUTS/HB Bitair MainBoard V1.22 GBR/" bitair-mainboard.kicad_pcb
```

## Generating assembly files

- **BOM:** the schematic fields `LCSC`, `Manufacturer`, `MPN`, `Alt MPN` and
  `DigiKey` hold the part numbers. Export them from the schematic editor with
  **Tools → Edit Symbol Fields Table** or
  `kicad-cli sch export bom bitair-mainboard.kicad_sch`.
- **Pick-and-place:** in the PCB editor choose **File → Fabrication Outputs →
  Component Placement (.pos)**, or run `kicad-cli pcb export pos`.
- **Schematic PDF:**
  `kicad-cli sch export pdf --output "OUTPUTS/Assembly/Circuit Diagram/HB Bitair MainBoard V1.22 SCH.pdf" bitair-mainboard.kicad_sch`
