# CANsus revision log

This revision history was reconstructed by comparing the supplied **KiCad v10-v16 schematic and PCB files**. The entries below document changes that are directly visible in the source: component/connector selection, net names and pin mappings, board outline, routing, and mounting features.

**Date note:** the dates shown are file-modification timestamps stored in the supplied KiCad export archive. They are useful for chronology, but they are not asserted to be formal release dates.

**Intent note:** the design files record *what changed*, not necessarily *why*. Where design intent is not explicitly encoded, this log avoids assigning a rationale.

## Summary

| Revision | Archive PCB timestamp | Edge.Cuts envelope | Main observed change |
|---|---|---:|---|
| v10 | 2024-06-05 | 76.20 × 50.80 mm | CAN-only baseline with 18 WAGO 250-202 terminal blocks |
| v11 | 2024-08-14 | 57.15 × 50.80 mm | Connector-family change to 2601-3102; terminal count reduced to 12 |
| v12 | 2024-08-16 | 63.50 × 33.02 mm | Terminal count reduced to 10; much shorter board |
| v13 | 2024-10-08 | 93.98 × 40.64 mm | Added 12 V/GND, four auxiliary signals, dual RJ45, bulk capacitor, LED/resistor |
| v14 | 2025-01-07 | 86.00 × 53.00 mm | Major connector/mechanical redesign; 2601-1104/1102 blocks, new RJ45s, SMD support parts |
| v15 | 2025-01-09 | 73.25 × 52.94 mm | Removed one auxiliary block and compacted board width |
| v16 | 2025-01-26 | 73.25 × 52.94 mm | Reduced auxiliary interface from four signals to two; repurposed J5 for power |

## v10 — CAN-only baseline

**Observed hardware**

- 18 × WAGO 250-202 two-position terminal footprints, J1-J18.
- Four mounting holes.
- Only two named electrical nets: `CAN_HI` and `CAN_LO`.
- Approximate board envelope: **76.20 × 50.80 mm**.
- Routed with 0.25 mm copper tracks in the supplied PCB.

This is the earliest KiCad snapshot in the supplied design history and matches the `CANsus Board v10` text visible on the earlier physical-board photo.

## v11 — connector-family and density change

**Changes from v10**

- Replaced the 250-202 connector family with **WAGO 2601-3102** footprints.
- Reduced the terminal population from **18 to 12** connector footprints.
- Mounting-hole footprints are represented as **#4-40 UNC** hardware in the PCB.
- Narrowed the board envelope from 76.20 mm to **57.15 mm** while retaining the 50.80 mm height.
- Electrical scope remained CAN-only: `CAN_HI` and `CAN_LO`.

## v12 — further CAN-only compaction

**Changes from v11**

- Reduced the 2601-3102 terminal population from **12 to 10**.
- Retained four #4-40 mounting holes.
- Continued to expose only `CAN_HI` and `CAN_LO`.
- Changed the board envelope to approximately **63.50 × 33.02 mm**, substantially reducing height relative to v11.

## v13 — major functional expansion

v13 is the first supplied revision that expands CANsus beyond a CAN-only distribution board.

**Added electrical functions**

- `12V`
- `GND`
- `SIGNAL_1`
- `SIGNAL_2`
- `SIGNAL_3`
- `SIGNAL_4`

**Added hardware**

- Two **SS-7188-NF RJ45** connectors, J11 and J12.
- Bulk polarized capacitor C1 between 12 V and GND.
- Through-hole LED D1 and resistor R1 as a status/power indicator circuit.
- Additional 2601-3102 terminal blocks for power and auxiliary-signal distribution.

**RJ45 mapping in v13**

| Pin | Signal |
|---:|---|
| 1 | SIGNAL_4 |
| 2 | GND |
| 3 | SIGNAL_3 |
| 4 | 12 V |
| 5 | CAN_LO |
| 6 | SIGNAL_2 |
| 7 | CAN_HI |
| 8 | SIGNAL_1 |

**Layout changes**

- Board envelope increased to approximately **93.98 × 40.64 mm** to accommodate the expanded interface.
- 12 V and GND routing uses **1.5 mm traces** in the supplied layout; CAN and signal routing remains primarily 0.25 mm.

## v14 — major architecture and packaging redesign

v14 substantially reorganizes the connector layout while retaining the expanded v13 signal set.

**Changes from v13**

- Replaced the many 2601-3102 terminal blocks with:
  - 6 × **WAGO 2601-1104** four-position blocks.
  - 1 × **WAGO 2601-1102** two-position block.
- Replaced the SS-7188-NF RJ45 footprints with **R-RJ45R08P-B000** connectors.
- Changed C1 to the `VT1C102M1010` footprint/value used in the later revisions.
- Migrated D1 from a through-hole LED footprint to **0603 SMD**.
- Migrated R1 from a through-hole resistor footprint to **1206 SMD**.
- Reduced mounting holes from **four to two** #4-40 holes.
- Board envelope became approximately **86.00 × 53.00 mm**.

**Functional grouping**

- J1-J4 provide repeated CAN_HI / CAN_LO distribution.
- J5 and J6 each duplicate SIGNAL_1-SIGNAL_4.
- J7 provides 12 V and GND.
- Both RJ45 connectors carry 12 V, GND, four auxiliary signals, CAN_HI, and CAN_LO.

**RJ45 mapping in v14**

| Pin | Signal |
|---:|---|
| 1 | 12 V |
| 2 | GND |
| 3 | SIGNAL_1 |
| 4 | SIGNAL_2 |
| 5 | SIGNAL_3 |
| 6 | SIGNAL_4 |
| 7 | CAN_HI |
| 8 | CAN_LO |

## v15 — compacted four-signal layout

**Changes from v14**

- Removed J6, one of the two duplicated 2601-1104 auxiliary-signal blocks.
- Retained J5 for SIGNAL_1-SIGNAL_4.
- Retained four 2601-1104 CAN distribution blocks, the 2601-1102 12 V/GND block, and both RJ45 connectors.
- Reduced board width from **86.00 mm to 73.25 mm**, approximately **14.8% narrower**.
- Board height remained essentially unchanged at about 52.94 mm.
- The PCB logo footprint changed to a half-size variant.
- Routing was substantially reworked; the net set and RJ45 pinout remained the same as v14.

The schematic/PCB PDF exports currently stored in `docs/` correspond to this four-auxiliary-signal architecture.

## v16 — simplified auxiliary interface

v16 keeps the v15 mechanical envelope and component count but changes the electrical assignment of the auxiliary interface.

**Changes from v15**

- Removed the named nets `SIGNAL_3` and `SIGNAL_4`.
- RJ1/RJ2 pins 5 and 6 changed from SIGNAL_3 / SIGNAL_4 to **unconnected**.
- J5 was repurposed:
  - pins 1/2: SIGNAL_1
  - pins 3/4: SIGNAL_2
  - pins 5/6: 12 V
  - pins 7/8: GND
- J7 remains a dedicated 12 V/GND connector.
- CAN distribution on J1-J4 remains unchanged.
- Board envelope remains approximately **73.25 × 52.94 mm**.
- Routing was adjusted to support the new net assignment.
- 12 V/GND continue to use 1.5 mm routing for the main distribution paths; CAN and auxiliary signal traces are 0.25 mm in the supplied PCB.

**v16 RJ45 mapping**

| Pin | Signal |
|---:|---|
| 1 | 12 V |
| 2 | GND |
| 3 | SIGNAL_1 |
| 4 | SIGNAL_2 |
| 5 | NC |
| 6 | NC |
| 7 | CAN_HI |
| 8 | CAN_LO |

## Revision-label notes

The project contains multiple forms of version labeling:

- The historical KiCad export folders are named **v10 through v16**. This log uses those folder names as the revision sequence.
- PCB title blocks are not consistently updated: v10-v13 still show `CANSus Board v10`, while v14-v16 show `CANSus Board v14`.
- The physical-photo filenames use a separate `Version 1` / `Version 5` naming scheme. The earlier photo visibly shows v10 silkscreen, so those photo names are treated as media labels rather than electrical revision numbers.

Keeping those distinctions explicit avoids rewriting the historical source or assigning unsupported mappings between the naming schemes.
