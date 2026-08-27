# Hardware

The Soldering Station V2 hardware is organised into two boards:

- **Control Board**
- **Power Board**

The repository snapshot supplied for documentation contains Windows shortcuts to the original CAD projects. The native schematic/PCB source files are not included in this archive.

## Directory structure

```text
Hardware/
├── Control Board/
│   └── Soldering_Station_V2.lnk
├── Power Board/
│   └── Soldering_Station_Power_Board.lnk
└── README.md
```

## Control Board

The Control Board contains the station's control electronics.

The distributed file is:

```text
Control Board/Soldering_Station_V2.lnk
```

This is a Windows shortcut and therefore does not contain the PCB/schematic project itself. The shortcut points to the original project on the developer's Windows filesystem.

### Recommended documentation to add with the native project

When the original CAD project is added to the repository, document:

- MCU and part number;
- clock configuration;
- power rails;
- programming/debug connector;
- display/interface;
- buttons/encoders;
- temperature-sensor input;
- heater-control output;
- status indicators;
- communication interfaces;
- connector pinouts;
- test points;
- board dimensions;
- mounting-hole dimensions.

## Power Board

The Power Board is represented by:

```text
Power Board/Soldering_Station_Power_Board.lnk
```

The native source is not included in the supplied archive.

Because this board is associated with the power path of the soldering station, its documentation should explicitly specify:

- input voltage range;
- maximum input current;
- heater/load voltage;
- heater/load current;
- switching device;
- gate/base drive;
- protection circuitry;
- fuse/protection requirements;
- grounding/earthing;
- thermal requirements;
- connector ratings;
- PCB creepage and clearance;
- enclosure requirements.

These values should be taken directly from the schematic and component datasheets rather than guessed.

## Board-to-board architecture

The intended project organisation suggests a split between low-power control electronics and the power stage:

```text
                CONTROL BOARD
        ┌──────────────────────────┐
        │ MCU                      │
        │                           │
        │ User interface            │
        │ Temperature measurement   │
        │ Control algorithm         │
        │                           │
        └────────────┬─────────────┘
                     │
                     │ control + feedback
                     │
        ┌────────────▼─────────────┐
        │       POWER BOARD        │
        │                           │
        │ Power input               │
        │ Heater switching          │
        │ Protection                │
        └────────────┬─────────────┘
                     │
                     ▼
                  HEATER
```

This is a conceptual representation only. Connector names, pin numbers, signal levels, and power ratings must be verified against the actual schematics.

## Design review checklist

Before assembling or powering the station, verify:

- [ ] Supply voltage matches the power-board design.
- [ ] All connectors are rated for their intended voltage/current.
- [ ] Heater current is within the switching-device and PCB limits.
- [ ] Temperature sensing fails safely if the sensor is disconnected.
- [ ] The control firmware has an over-temperature shutdown.
- [ ] The power stage has appropriate current/thermal protection.
- [ ] PCB creepage and clearance are appropriate for the actual voltage.
- [ ] Protective earth/grounding requirements have been addressed where applicable.
- [ ] The enclosure prevents accidental contact with hazardous voltages.
- [ ] The heater cannot remain permanently energised after a control fault.

## Reproducibility

For the hardware directory to be fully reproducible, the repository should contain the native CAD files rather than only shortcuts.

A recommended structure is:

```text
Hardware/
├── Control Board/
│   ├── Schematic/
│   ├── PCB/
│   ├── Libraries/
│   └── Manufacturing/
└── Power Board/
    ├── Schematic/
    ├── PCB/
    ├── Libraries/
    └── Manufacturing/
```

The exact structure can be adapted to the CAD tool used by the project.

## Important note about `.lnk` files

Windows shortcuts can contain absolute paths such as:

```text
C:\Users\...\Documents\...
```

Such paths are specific to the original computer and normally will not work for another contributor.

For collaboration, store the actual project files in Git and use relative paths for project dependencies whenever the CAD tool supports them.
