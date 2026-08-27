# Soldering Station V2

An open hardware/software project for a custom soldering station.

> **Project status:** Hardware and project structure are present in this repository. The firmware source and native CAD project files are not included in the supplied archive; only Windows shortcuts to the original development locations are present. Consequently, this documentation describes the files that are actually distributed here and clearly identifies information that must be supplied from the original development project.

## Repository contents

```text
Soldering_Station-staging/
├── Case/
│   ├── CE3PRO_Right Expander Simplified.3mf
│   ├── PCB.step
│   └── README.md
├── Firmware/
│   ├── Soldering_Station_V2.lnk
│   └── README.md
├── Hardware/
│   ├── Control Board/
│   │   └── Soldering_Station_V2.lnk
│   ├── Power Board/
│   │   └── Soldering_Station_Power_Board.lnk
│   └── README.md
└── README.md
```

## What is included

### Hardware

The `Hardware/` directory separates the electronics into:

- **Control Board** — the station's control electronics.
- **Power Board** — the power-handling electronics.

The supplied archive contains Windows shortcuts for the original hardware projects rather than the native PCB/project files themselves.

See [`Hardware/README.md`](Hardware/README.md).

### Case

The `Case/` directory contains:

- `PCB.step` — a STEP 3D model of the PCB assembly.
- `CE3PRO_Right Expander Simplified.3mf` — a 3MF model intended for 3D-printing/CAD workflows.

See [`Case/README.md`](Case/README.md).

### Firmware

The `Firmware/` directory contains a Windows shortcut named `Soldering_Station_V2.lnk` pointing to the original firmware development project.

See [`Firmware/README.md`](Firmware/README.md).

## Getting the complete development project

The current repository snapshot contains shortcuts pointing to files on the original Windows development machine. A `.lnk` file is **not** the project itself.

For a fully reproducible repository, replace the shortcuts with the actual project files, including:

- firmware source code and build configuration;
- control-board schematic and PCB files;
- power-board schematic and PCB files;
- libraries used by the CAD projects;
- generated manufacturing files, if they are intended to be distributed.

Do not commit machine-specific absolute paths as the only way of accessing the project.

## Hardware architecture

At a high level, the project is organised around two electronic boards:

```text
                    ┌─────────────────────┐
                    │   Control Board     │
                    │                     │
                    │ MCU / UI / sensing  │
                    │ control / interface │
                    └──────────┬──────────┘
                               │
                               │ control / feedback
                               │
                    ┌──────────▼──────────┐
                    │     Power Board     │
                    │                     │
                    │ power switching /   │
                    │ heater power path   │
                    └─────────────────────┘
```

The exact MCU, heater interface, temperature sensor, supply voltage, connector pinout, and control algorithm should be documented from the native schematic/firmware source before being treated as authoritative.

## 3D models

The STEP file can be imported into most mechanical CAD packages for enclosure integration and PCB fit checks.

The 3MF file can be opened by common 3D-printing software. Verify dimensions, orientation, clearances, and print settings before manufacturing.

## Development status and limitations

The supplied archive is suitable for documenting the project's current file organisation and for using the included mechanical models. It is **not yet a fully reproducible firmware/hardware development repository**, because the native source projects are referenced through Windows shortcuts.

### Recommended repository improvements

1. Replace all `.lnk` files with their actual source projects.
2. Add the exact MCU and toolchain version to the firmware README.
3. Add a complete board pinout.
4. Document the heater and temperature-sensing interface.
5. Document the power input and output ratings.
6. Add schematics and PCB source files.
7. Add manufacturing outputs when appropriate.
8. Add photographs/renders of the assembled station.
9. Add firmware flashing instructions.
10. Add a release/versioning scheme.

## Safety

A soldering station combines mains/high-energy power, a high-temperature heating element, and potentially exposed conductive parts. Treat the power circuitry as hazardous until its voltage, current, insulation, grounding, fusing, and enclosure requirements have been verified from the actual design.

**Do not use this documentation as a substitute for electrical safety validation.**

## License

No license file was included in the supplied archive. Until a license is added, the safest assumption is that the repository contents are **not automatically licensed for redistribution or modification**.

Add a `LICENSE` file if you want to define how the hardware, firmware, CAD files, and documentation may be used.
