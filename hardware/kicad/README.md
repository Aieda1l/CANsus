# KiCad source notes

The files in this directory are the **browsable v15 KiCad source snapshot** that was originally committed to the repository. A separate supplied export set containing v10-v16 was compared to build the source-derived [revision log](../../REVISION_LOG.md).

## Tool version

The supplied schematic and PCB files report **KiCad 8.0** generators.

## Files kept here

- `CAN_board.kicad_pro` — project settings
- `CAN_board.kicad_sch` — schematic
- `CAN_board.kicad_pcb` — PCB layout
- `fp-lib-table` — project footprint-library table
- `sym-lib-table` — project symbol-library table

Generated/local-state material such as `.history`, KiCad backups, `fp-info-cache`, and `.kicad_prl` is intentionally not committed.

## v15 snapshot architecture

This source snapshot contains:

- four 2601-1104 CAN distribution blocks (J1-J4)
- one 2601-1104 auxiliary block (J5) carrying SIGNAL_1-SIGNAL_4
- one 2601-1102 power block (J7) carrying 12 V/GND
- two RJ45 connectors carrying 12 V, GND, SIGNAL_1-SIGNAL_4, CAN_HI, and CAN_LO
- bulk capacitor C1
- 0603 LED D1
- 1206 resistor R1
- two #4-40 mounting holes

The later v16 export keeps the same board envelope and physical component count, but removes SIGNAL_3/SIGNAL_4 from the interface and repurposes part of J5 for 12 V/GND. See [REVISION_LOG.md](../../REVISION_LOG.md).

## Portability caveat

Some PCB 3D-model references point to absolute paths on the original designer's workstation, including local model paths for the RJ45, capacitor, and mechanical hardware. Those missing model paths do **not** change the copper or schematic source, but KiCad's 3D viewer may show missing models on another machine.

The schematic symbols and PCB footprints used by the design are embedded in the `.kicad_sch` and `.kicad_pcb` files, so the electrical/layout source remains inspectable even if an external library path is unavailable.

## Revision-label caveat

The historical folder names provide the most useful revision sequence. The PCB title blocks lag behind that sequence: v10-v13 carry a v10 title and v14-v16 carry a v14 title. The repository preserves the source as supplied rather than silently rewriting the title blocks.
