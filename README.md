# CANsus

**CANsus** — short for **CAN sustain / CAN sustainability** — is a CAN and auxiliary power/signal distribution board from Newport Robotics Group (Team 948). The goal is to make robot wiring easier to service, expand, and keep organized.

The current source snapshot is the supplied `CANSus Board v15` KiCad project. Its PCB title block identifies the design as **“CANSus Board v14”**, so this repository preserves that numbering discrepancy rather than guessing which label is authoritative.

![CANsus v5 assembled](photos/cansus-v5-assembled.jpg)

## What is on the current schematic

The supplied KiCad schematic contains:

- CAN high / CAN low distribution
- 12 V and GND distribution
- four auxiliary signal nets (`SIGNAL_1` through `SIGNAL_4`)
- five WAGO 2601-1104 four-position connectors
- one WAGO 2601-1102 two-position connector
- two RJ45 connectors
- a bulk capacitor, LED, and 1206 resistor footprint
- two #4-40 mounting holes

The resistor value is not specified in the supplied schematic, so the BOM leaves it as `R` rather than inventing a value.

## Repository layout

```text
.
├── README.md
├── REVISION_LOG.md
├── bom/
│   └── BOM.csv
├── docs/
│   ├── cansus-board-layout.pdf
│   └── cansus-schematic.pdf
├── hardware/
│   └── kicad/
│       ├── CAN_board.kicad_pcb
│       ├── CAN_board.kicad_pro
│       ├── CAN_board.kicad_sch
│       ├── fp-lib-table
│       ├── sym-lib-table
│       └── README.md
└── photos/
    ├── cansus-v1.jpg
    ├── cansus-v5-assembled.jpg
    └── cansus-v5-render.jpg
```

## Quick links

- [KiCad source](hardware/kicad/)
- [Schematic PDF](docs/cansus-schematic.pdf)
- [Board-layout PDF](docs/cansus-board-layout.pdf)
- [BOM](bom/BOM.csv)
- [Revision log](REVISION_LOG.md)

## Photos

### v5 assembled hardware

![CANsus v5 assembled hardware](photos/cansus-v5-assembled.jpg)

### v5 enclosure/render

![CANsus v5 render](photos/cansus-v5-render.jpg)

### v1 supplied photo

![CANsus v1 supplied photo](photos/cansus-v1.jpg)

## KiCad notes

The source files report **KiCad 8.0**. The schematic symbols and PCB footprints are embedded in the project files, but some 3D-model references in the PCB use machine-local absolute paths from the original workstation. See [hardware/kicad/README.md](hardware/kicad/README.md) for the portability notes.

## Revision numbering

The supplied assets use more than one numbering scheme: photo filenames use “Version 1” / “Version 5”, while the KiCad archive is named “v15” and the PCB title block says “v14”. [REVISION_LOG.md](REVISION_LOG.md) records what can be verified from the supplied artifacts and marks unknown v2-v4/v6 history explicitly instead of fabricating it.

## License

No license was supplied with the project, so this repository does **not** assign one. Add a hardware/documentation license when the team has chosen one.
