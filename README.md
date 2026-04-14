# 6T SRAM Memory Cell Design with Sense Amplifier (180 nm CMOS)

## Overview

This project presents the design, simulation, analysis, and layout implementation of a 6T SRAM (Static Random Access Memory) cell using 180 nm CMOS technology. Along with the SRAM cell, supporting circuits including a Sense Amplifier and Precharge Circuitry were designed to enable realistic read operations.

The project covers circuit-level simulation (LTspice) and physical layout design (Microwind), along with detailed evaluation of stability, power, delay, and area.

---

## Objectives

- Design a 6T SRAM cell with proper transistor sizing
- Implement Sense Amplifier and Precharge circuitry
- Analyze Hold, Read, and Write operations
- Evaluate Static Noise Margin (SNM) using butterfly curves
- Measure power consumption and delay
- Perform layout design with DRC verification
- Optimize design for area and performance trade-offs

---

## SRAM Architecture

The 6T SRAM cell consists of:

- 2 Cross-coupled CMOS inverters (4 transistors)
- 2 Access transistors controlled by Word Line (WL)

**Supporting Circuits** (used exclusively for read operation):

- **Sense Amplifier** — detects small bitline voltage differences
- **Precharge Circuit** — charges bitlines to VDD before read

**Key Nodes:**

| Node | Description |
|------|-------------|
| Q, Q̅ | Storage nodes |
| Bit, Bit̅ | Bitlines |
| WL | Word Line (access control) |

---

## Tools Used

| Tool | Purpose |
|------|---------|
| LTspice | Circuit simulation and waveform analysis |
| Microwind | Layout design and DRC verification |
| Excel | SNM butterfly curve analysis |

---

## SRAM Operations

### Write Operation

- Write = HIGH, WL = HIGH
- Data is forced onto bitline
- Cross-coupled inverters update the stored value

### Hold Operation

- Write = LOW, WL = LOW
- Cell is isolated from bitlines
- Stored value is retained via feedback

### Read Operation

- Write = LOW, WL = HIGH
- Bitlines precharged to VDD
- Stored data slightly perturbs the bitline
- Sense amplifier detects the output

---

## Simulation Details

- **Technology Node:** 180 nm CMOS
- **Supply Voltage (VDD):** 1.8 V
- **Simulation Tool:** LTspice

---

## Transistor Sizing

Proper sizing is critical for SRAM stability and performance.

### W/L Values Used

| Transistor | W (nm) | L (nm) | Role |
|------------|--------|--------|------|
| Pull-up PMOS | 325 | 180 | Load |
| Access NMOS | 500 | 180 | Read/Write |
| Pull-down NMOS | 1000 | 180 | Stability |

### Cell Ratio (CR)

```
CR = W_pull-down / W_access = 1000 / 500 = 2
```

A high cell ratio ensures a strong pull-down path, which improves read stability and results in a higher read SNM.

### Pull-up Ratio (PR)

```
PR = W_access / W_pull-up = 500 / 325 ≈ 1.54
```

This ratio ensures easier write operations and improves write ability.

---

## Performance Parameters

### Static Noise Margin (SNM)

| Type | Value |
|------|-------|
| Hold SNM | ~0.24 V |
| Read SNM | ~0.18 – 0.22 V |

Extracted using the butterfly curve method in Excel.

- **Hold SNM:** Indicates maximum stability when the cell is idle
- **Read SNM:** Indicates stability during read (reduced due to bitline interaction)

### Power Consumption

- **Average Power:** ~57.1 µW
- Includes dynamic and parasitic effects

### Delay

| Parameter | Value |
|-----------|-------|
| Write Delay | ~10.46 ns |
| Read Delay | ~0.93 ns |

**Observations:**
- Read is significantly faster than write
- Write delay is the limiting performance factor
- Power consumption is within expected range for 180 nm technology

---

## Layout Design (Microwind)

The physical layout was implemented using 180 nm CMOS design rules with the following considerations:

- Symmetrical layout for device matching
- Diffusion sharing used for area reduction
- Proper placement of N-well contacts and substrate contacts

### Layout Area

| Dimension | Value |
|-----------|-------|
| Width | 5.100 µm |
| Height | 3.150 µm |
| Total Area | ~16.07 µm² |

This falls within the expected range for a 6T SRAM cell at 180 nm.

### DRC Verification

All Design Rule Check (DRC) errors were resolved. Issues addressed include:

- N-well enclosure violations
- Minimum spacing constraint violations

The final layout is fabrication-compliant.

---

## Design Trade-offs

### Stability vs. Write Speed

A high cell ratio (CR = 2) improves read stability. However, stronger pull-down NMOS makes writing harder, resulting in a higher write delay (~10.46 ns).

### Read Speed vs. Read Stability

Strong pull-down NMOS enables fast read (~0.93 ns), but bitline interaction during read reduces stability, leading to a lower read SNM (~0.18 – 0.22 V).

### Power and Area vs. Layout Realism

A compact layout (~16.07 µm²) was achieved using diffusion sharing. However, layout parasitics increase effective power consumption (~44.7 µW), creating a trade-off between area efficiency and realistic performance.

### Initialization vs. Circuit Simplicity

An initial transient glitch (~0.6 V) arises due to undefined startup conditions. This can be removed using initialization or precharge circuits, but doing so introduces additional layout complexity.

---

## Conclusion

A complete 6T SRAM memory cell with sense amplifier and precharge circuitry was successfully designed and analyzed using 180 nm CMOS technology.

- Achieved ~0.24 V hold SNM, ensuring good stability
- Demonstrated fast read performance (~0.93 ns) and moderate write performance
- Obtained realistic power consumption (~57 µW)
- Implemented a DRC-compliant layout with optimized area (~16.07 µm²)

The project highlights key VLSI design trade-offs between stability, speed, power, and area, and provides a strong foundation in SRAM design and physical implementation.
