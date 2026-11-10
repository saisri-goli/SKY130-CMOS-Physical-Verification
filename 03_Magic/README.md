# 03. Magic – CMOS Inverter Layout and Physical Verification

## Index

1. [Introduction to Magic](#1-introduction-to-magic)
2. [Creating CMOS Inverter Layout](#2-creating-cmos-inverter-layout)
3. [Connecting the Components](#3-connecting-the-components)
4. [Extraction, SPICE Generation and DRC Verification](#4-extraction-spice-generation-and-drc-verification)
5. [Conclusion](#5-conclusion)

---

## 1. Introduction to Magic

Magic is an open-source VLSI layout editor used for designing and verifying integrated circuit layouts. It provides features such as layout editing, Design Rule Checking (DRC), circuit extraction and SPICE netlist generation.

In this project, Magic was used to create the physical layout of the CMOS inverter designed earlier using Xschem.

The inverter schematic netlist generated from Xschem (`inverter.spice`) was used as the reference for creating the corresponding physical layout.

## 2. Creating CMOS Inverter Layout

### 2.1 Importing the SPICE Netlist

The SPICE netlist generated from Xschem was imported into Magic to create the initial inverter layout.

The imported netlist contains the transistor instances and their connectivity information, which serves as the starting point for layout creation.

**Image 1: Initial CMOS inverter layout after importing the SPICE netlist into Magic.**
<img width="1603" height="892" alt="magic_inv" src="https://github.com/user-attachments/assets/c0d32653-7765-4b82-822a-9d1ddd9b9616" />


### 2.2 Arranging the Components

After importing the SPICE netlist, the PMOS and NMOS transistor layouts were arranged properly to form the CMOS inverter structure.

The following Magic editing operations were used:

- **Key `i`:** Used to select the required transistor instance.
- **Key `m`:** Used to move the selected component.
- **Key `s`:** Used to select the required pins.

The components were positioned carefully to maintain proper alignment and make the subsequent metal connections easier.

**Image 2: Arrangement and positioning of PMOS and NMOS components in Magic.**
<img width="436" height="647" alt="placed well" src="https://github.com/user-attachments/assets/614233df-1ffd-475a-85ca-cc9a683db7cd" />

### 2.3 PMOS Parameter Configuration

The PMOS transistor properties were configured using the property window.

- Press `Ctrl + P` to open the properties of the selected component.
- The top guard ring value was set to `100`.
- Source parameter was set to `+40`.
- Drain parameter was set to `-40`.

**Image 3: PMOS parameter configuration in Magic.**
<img width="1301" height="867" alt="PFET_PARAM" src="https://github.com/user-attachments/assets/14d8f2cb-3b88-46e0-8fa6-c75a9f163a88" />


### 2.4 NMOS Parameter Configuration

Similarly, the NMOS transistor properties were configured using `Ctrl + P`.

- The bottom guard ring value was set to `100`.
- Source parameter was set to `+40`.
- Drain parameter was set to `-40`.

**Image 4: NMOS parameter configuration in Magic.**
<img width="1267" height="857" alt="NFET_PARAM" src="https://github.com/user-attachments/assets/cfbaae13-dbce-4b19-95eb-69f2464a8e85" />


## 3. Connecting the Components

After arranging the transistors and configuring their parameters, the required electrical connections were created using appropriate metal layers.

This was one of the most challenging stages of the layout design because the connections had to be made carefully while satisfying the design rules.

**Connection Procedure:**

1. The left mouse button was used to start drawing the required rectangular connection.
2. The right mouse button was used to complete the rectangular connection.
3. The middle mouse button was used to select the required metal layer.
4. The rectangular connection was created using the selected metal layer.

The appropriate metal layers were used to connect the transistor terminals and establish the required electrical paths.

The connections were adjusted and checked repeatedly to eliminate layout design rule violations.

**Image 5: Complete CMOS inverter layout with zero DRC errors.**
<img width="726" height="793" alt="layout_done" src="https://github.com/user-attachments/assets/c8c9236b-cb58-46e8-b453-548a7823ebca" />


## 4. Extraction, SPICE Generation and DRC Verification

After completing the layout and electrical connections, extraction and physical verification were performed using the Magic console.

### 4.1 Circuit Extraction

Circuit extraction is the process of identifying the electrical components and their interconnections from the physical layout.

The following commands were executed in the Magic console:

```tcl
extract do local
extract all
```

**Command Explanation:**

- `extract do local` – Configures local extraction behaviour.
- `extract all` – Extracts the circuit information from the complete layout, including devices and their electrical connectivity.

**Image 6: Circuit extraction commands and their output in Magic.**
<img width="1221" height="276" alt="extract" src="https://github.com/user-attachments/assets/99286d07-41be-4cd9-959f-d4e47cef15da" />


### 4.2 SPICE Netlist Generation

After extraction, the layout information was converted into a SPICE-compatible netlist.

The following commands were used:

```tcl
ext2spice lvs
ext2spice
```

**Command Explanation:**

- `ext2spice lvs` – Configures SPICE extraction in an LVS-compatible format.
- `ext2spice` – Generates the SPICE netlist from the extracted layout.

The generated netlist can subsequently be compared with the schematic netlist using Netgen for Layout Versus Schematic (LVS) verification.

**Image 7: Ext2spice commands and generated SPICE netlist output.**
<img width="236" height="63" alt="ext2spice" src="https://github.com/user-attachments/assets/839f2a05-4edd-41de-aadd-b6ecb7a1f812" />


### 4.3 Design Rule Checking (DRC)

Design Rule Checking (DRC) is a physical verification process used to identify violations of the fabrication rules defined by the selected technology.

It checks whether the layout satisfies constraints such as minimum spacing, minimum width and other geometric requirements.

The following commands were executed in the Magic console:

```tcl
drc check
drc count
drc why
```

**Command Explanation:**

- `drc check` – Performs a design rule check on the layout and identifies violations.
- `drc count` – Displays the total number of DRC errors found.
- `drc why` – Explains the reason for a DRC violation at the selected location, when a violation exists.

**DRC Verification Result:**

The layout was checked successfully, and the Magic console displayed:

```text
Total DRC errors found: 0
```

A DRC count of zero indicates that no design rule violations were detected in the checked layout.

**Image 8: Final DRC verification output showing zero errors in Magic.**
<img width="471" height="263" alt="drc_check" src="https://github.com/user-attachments/assets/e112bcfc-006b-409e-abc8-098006f16791" />


## 5. Conclusion

The CMOS inverter physical layout was successfully created using Magic with the SKY130 technology. The PMOS and NMOS components were arranged, their parameters were configured and the required metal connections were established.

Circuit extraction and SPICE netlist generation were performed to prepare the layout for LVS verification. Finally, Design Rule Checking was completed successfully, with **zero DRC errors**, confirming that no design rule violations were detected in the layout.
