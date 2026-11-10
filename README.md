# SKY130 CMOS Inverter – Design and Physical Verification

A complete hands-on implementation of a CMOS inverter using the **SkyWater SKY130 PDK** and open-source VLSI tools. This project covers the complete flow, starting from Ubuntu environment setup and schematic design to physical layout creation, circuit extraction, DRC and LVS verification.

---

## Project Overview

The objective of this project is to understand and implement the CMOS design flow using open-source Electronic Design Automation (EDA) tools.

A CMOS inverter was designed using Xschem, simulated using Ngspice, and physically implemented using Magic. The final layout was verified using Design Rule Checking (DRC) and Layout Versus Schematic (LVS) verification.

## Tools and Technologies Used

| Tool / Technology | Purpose |
|---|---|
| Ubuntu 24.04.5 LTS | Linux development environment |
| Oracle VirtualBox | Virtualization platform |
| SKY130 PDK | 130 nm CMOS technology library |
| Xschem | Schematic design |
| Ngspice | Circuit simulation |
| Magic | Physical layout design and DRC |
| Netgen | LVS verification |
| Xterm | Terminal emulator |
| Git & GitHub | Version control and documentation |

---

## Project Workflow

The complete CMOS inverter implementation follows these stages:

1. **Environment Setup:** Installed Ubuntu inside Oracle VirtualBox and configured the required development packages and open-source VLSI tools.
2. **Schematic Design:** Created the CMOS inverter schematic using Xschem with SKY130 PMOS and NMOS transistor models.
3. **Circuit Simulation:** Created a testbench and performed transient simulation using Ngspice to verify inverter switching behaviour.
4. **Physical Layout Design:** Imported the schematic-generated SPICE netlist into Magic and created the physical layout by arranging transistors and establishing metal connections.
5. **Circuit Extraction:** Extracted the electrical connectivity from the completed layout and generated a SPICE netlist.
6. **Physical Verification:** Performed DRC using Magic and LVS comparison using Netgen to verify the physical layout against the original schematic.

---

## Repository Structure

The repository is organized into four chapters for easy navigation and step-by-step understanding.

| Folder | Description |
|---|---|
| `01_Ubuntu_Setup/` | Ubuntu installation, package installation, VLSI tools setup and SKY130 PDK cloning |
| `02_Xschem/` | CMOS inverter schematic, testbench creation and waveform simulation |
| `03_Magic/` | Inverter layout creation, transistor configuration, metal connections, extraction and DRC |
| `04_Netgen/` | Layout Versus Schematic (LVS) verification |

## Documentation Index

### Chapter 1 – Ubuntu Setup
Covers the development environment preparation and installation of the required VLSI tools.

[Explore Ubuntu Setup →](01_Ubuntu_Setup/README.md)

### Chapter 2 – Xschem: Schematic Design and Simulation
Explains CMOS inverter schematic creation, symbol generation, testbench configuration and transient waveform analysis.

[Explore Xschem →](02_Xschem/README.md)

### Chapter 3 – Magic: Layout Design and DRC
Covers SPICE netlist import, PMOS and NMOS arrangement, parameter configuration, metal connections, circuit extraction and DRC verification.

[Explore Magic →](03_Magic/README.md)

### Chapter 4 – Netgen: LVS Verification
Explains the comparison of schematic and extracted layout netlists and the final LVS verification results.

[Explore Netgen →](04_Netgen/README.md)

---

## Final Verification Results

The CMOS inverter successfully completed the physical verification stages.

| Verification | Tool | Result |
|---|---|---|
| Schematic simulation | Xschem + Ngspice | Inverter switching verified |
| Design Rule Checking | Magic | 0 DRC errors |
| Circuit extraction | Magic | Completed |
| SPICE netlist generation | Magic | Completed |
| Layout Versus Schematic | Netgen | Circuits match uniquely |

### DRC Verification

The Magic console reported:

```text
Total DRC errors found: 0
```

This indicates that no design rule violations were detected in the checked layout.

### LVS Verification

The Netgen comparison reported:

```text
Final result:
Circuits match uniquely.

LVS Done.
```

Both the schematic and extracted layout contained:
- 1 PMOS transistor
- 1 NMOS transistor
- 4 electrical nets

The unique match confirms that the extracted layout netlist matches the schematic netlist under the configured LVS comparison rules.

---

## Learning Outcomes

Through this project, I gained practical experience in:

- Understanding the open-source SKY130 CMOS design flow.
- Working with Linux and Ubuntu environments.
- Designing CMOS schematics using Xschem.
- Performing transient circuit simulations using Ngspice.
- Creating physical layouts using Magic.
- Understanding transistor placement and metal-layer connections.
- Performing circuit extraction and SPICE netlist generation.
- Identifying and resolving DRC violations.
- Understanding and performing LVS verification using Netgen.
- Maintaining technical documentation using Git and GitHub.

---

## Acknowledgement

This project was carried out as part of the **Sri Krishiv VSD training program**, with the objective of gaining practical exposure to open-source VLSI design and physical verification workflows.

---

**Project Domain:** VLSI – CMOS Design and Physical Verification

**Technology Node:** SKY130 – 130 nm CMOS

**Design Implemented:** CMOS Inverter

**Tools:** Xschem | Ngspice | Magic | Netgen

