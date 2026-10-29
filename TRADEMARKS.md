# Trademarks

"Heatbit", "Bitair" and the Heatbit logo are trademarks of Heatbit Inc.

The CERN-OHL-S-2.0 licence covers the design files in this repository. It does
**not** grant any right to use the Heatbit trademarks.

The design files contain the Heatbit logo and name on the copper and
silkscreen layers. They are kept there so that the published source matches
the boards Heatbit manufactures.

**If you manufacture or distribute boards made from this design, you must:**

- remove the Heatbit logo and the Heatbit/Bitair name from the board (see
  "Removing the branding" below);
- not present your product as made, endorsed or supported by Heatbit Inc.

**What you may do:**

- state factually that your board is "based on the Heatbit Bitair Mainboard
  design";
- refer to Heatbit products by name when describing compatibility, for
  example "replacement mainboard for the Heatbit Bitair air purifier", as long
  as this does not suggest an endorsement.

## Removing the branding

In `bitair-mainboard.kicad_pcb`:

1. Delete the six footprints with the value `LOGO` (reference `G***`): three
   on F.Cu and three on B.Cu.
2. Replace the silkscreen texts `HEATBIT BITAIR MainBoard V1.22` (top) and
   `HEATBIT Bitair MainBoard V1.22` (bottom) with your own name.
3. Refill the zones (press B) and run DRC.

## Bitaxe

Bitaxe is a trademark of bitaxeorg. This board is based on bitaxeGamma (see
[NOTICE.md](NOTICE.md)), but it is not an official Bitaxe product and is not
endorsed by bitaxeorg.
