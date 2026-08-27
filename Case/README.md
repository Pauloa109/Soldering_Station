# Case

This directory contains mechanical files associated with the Soldering Station V2.

## Files

| File | Format | Purpose |
|---|---|---|
| `PCB.step` | STEP | 3D representation of the PCB |
| `CE3PRO_Right Expander Simplified.3mf` | 3MF | 3D-printable/model file |

## PCB STEP model

`PCB.step` is a STEP-format mechanical model of the PCB.

STEP is useful for:

- checking PCB-to-enclosure clearance;
- importing the board into mechanical CAD;
- designing mounting points;
- checking connector and component interference;
- creating enclosure assemblies;
- producing mechanical drawings/renders.

The file identifies the main assembly as `PCB`/`Board` and contains a detailed CAD representation.

### Recommended workflow

1. Import `PCB.step` into your CAD software.
2. Confirm the model units.
3. Check the board outline and mounting-hole positions.
4. Check connector and component heights.
5. Place the PCB in the enclosure.
6. Verify clearance around hot and high-power components.
7. Verify access to connectors, controls, and service points.
8. Only then finalise the enclosure geometry.

## 3MF model

`CE3PRO_Right Expander Simplified.3mf` is a 3MF model.

3MF is intended for modern additive-manufacturing workflows and can be opened by compatible slicers/CAD applications.

Before printing:

- confirm the model orientation;
- verify dimensions against the physical PCB;
- check wall thickness;
- check mounting-hole sizes;
- check clearances around connectors;
- check ventilation requirements;
- check the material's temperature rating.

## Enclosure design considerations

A soldering station contains a high-temperature heat source. The enclosure should therefore be designed around:

### Thermal management

Provide sufficient separation between the heater/power components and temperature-sensitive plastic parts.

Do not assume that a plastic material is suitable merely because it is printable. The operating temperature of the enclosure and the expected heat-soak conditions must be considered.

### Electrical safety

If the station contains hazardous voltage, the enclosure must prevent accidental contact and maintain the required creepage and clearance distances.

Cable exits and connector openings should not allow users to touch hazardous conductors.

### Mechanical serviceability

Leave adequate access for:

- PCB installation/removal;
- connectors;
- fasteners;
- programming/debugging;
- fuse replacement;
- inspection of the power stage.

## Fit validation

The supplied mechanical files should be treated as the current reference geometry, but the physical assembly should still be validated.

Recommended checks:

- [ ] PCB outline matches the manufactured board.
- [ ] Mounting holes align.
- [ ] Screw/fastener heads have adequate clearance.
- [ ] Connectors are reachable after enclosure assembly.
- [ ] Display openings align with the display.
- [ ] Buttons/controls can be operated without interference.
- [ ] Ventilation openings are unobstructed.
- [ ] High-temperature areas are separated from the enclosure material.
- [ ] No conductive hardware can unintentionally contact electrical circuitry.

## Source CAD

The supplied archive contains exported/portable mechanical formats but does not contain the original native enclosure CAD project.

If the enclosure is maintained in a specific CAD application, consider adding the native source files in a separate directory and keeping the STEP/3MF files as exchange/manufacturing outputs.

## Printing

The correct print parameters depend on the selected material and the final mechanical design.

At minimum, validate:

- dimensional accuracy;
- layer adhesion;
- screw-hole tolerances;
- heat resistance;
- structural rigidity;
- deformation near heat sources.

Do not print or use a part near a hot element unless its material and design have been verified for the expected temperature.
