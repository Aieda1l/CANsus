# KiCad source notes

These files are the cleaned core of the supplied `CANSus Board v15` archive.

## Tool version

Both the schematic and PCB report **KiCad 8.0** generators.

## Files kept here

- `CAN_board.kicad_pro` — project settings
- `CAN_board.kicad_sch` — schematic
- `CAN_board.kicad_pcb` — PCB layout
- `fp-lib-table` — project footprint-library table from the supplied archive
- `sym-lib-table` — project symbol-library table from the supplied archive

Generated/local-state material such as `.history`, KiCad backups, `fp-info-cache`, and `.kicad_prl` is intentionally not committed.

## Portability caveat

The PCB contains some 3D-model references that point to absolute paths on the original designer's workstation, including local paths for the RJ45, capacitor, and one screw model. Those missing 3D models do **not** change the copper/schematic source, but KiCad's 3D viewer may show missing models on another machine.

The schematic symbols and PCB footprints used in the design are embedded in the `.kicad_sch` and `.kicad_pcb` files, so the electrical/layout source remains inspectable even if an external library path is unavailable.

## Source-label caveat

The archive name says `v15`, but the PCB title block says `CANSus Board v14`. The source is preserved as supplied; this repository does not silently rewrite the design revision.
