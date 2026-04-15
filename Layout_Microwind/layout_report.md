**SRAM Layout Design Report (Microwind – 180 nm)**

**Overview**

The physical layout of the 6T SRAM cell was implemented using Microwind (180 nm CMOS technology). The design follows a symmetrical structure to ensure proper matching between transistors and balanced operation.

**Transistor Sizing**
The same W/L ratios as the schematic were used to maintain consistency between simulation and layout
This ensures that performance parameters (SNM, delay, power) remain aligned with pre-layout results

**Layout Area**
Width: 5.100 µm
Height: 3.150 µm
Total Area: ≈ 16.07 µm²
Area optimization was achieved using:
Diffusion sharing
Compact transistor placement

**Power Consumption**
Post-layout power consumption:
≈ 44.723 µW
Slight variation from schematic results due to:
Parasitic capacitances
Interconnect effects

**DRC Verification**

All Design Rule Check (DRC) violations were identified and resolved.

Issues Faced:
N-well enclosure violations
Spacing issues between diffusion and wells
Fixes Applied:
Increased N-well enclosure around PMOS regions
Adjusted spacing according to λ-based design rules
Ensured proper placement of:
Well contacts
Substrate contacts

✔ Final layout is DRC-clean and fabrication compliant
