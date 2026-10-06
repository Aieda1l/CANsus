# PDF export notes

The PDFs in this directory are reference exports supplied with the project.

- `cansus-schematic.pdf` shows the four-auxiliary-signal architecture used by the v14/v15 design family: 12 V, GND, SIGNAL_1-SIGNAL_4, CAN_HI, CAN_LO, dual RJ45, and WAGO distribution blocks.
- `cansus-board-layout.pdf` is the accompanying PCB-layout export.

The later v16 KiCad source changes the auxiliary interface by removing SIGNAL_3 and SIGNAL_4, so these PDFs should be treated as **v14/v15-era reference exports**, not as a v16 electrical-interface definition.

For revision-by-revision differences, see [../REVISION_LOG.md](../REVISION_LOG.md).
