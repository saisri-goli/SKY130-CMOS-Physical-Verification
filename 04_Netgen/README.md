# 04. Netgen – Layout Versus Schematic (LVS) Verification

## Index

1. [Introduction to Netgen](#1-introduction-to-netgen)
2. [LVS Verification](#2-lvs-verification)

---

## 1. Introduction to Netgen

Netgen is an open-source netlist comparison tool used for Layout Versus Schematic (LVS) verification in VLSI design.

LVS is an important physical verification step that checks whether the physical layout of a circuit matches its corresponding schematic in terms of electrical connectivity and device properties.

In this project, Netgen was used to compare:

- **Schematic Netlist:** Generated using Xschem (`inverter.spice`).
- **Layout Netlist:** Extracted from the CMOS inverter layout using Magic (`inverter.spice`).

The comparison ensures that the physical layout represents the same electrical circuit as the original schematic.

## 2. LVS Verification

### 2.1 Executing the LVS Command

The LVS comparison was performed from the Ubuntu terminal by navigating to the Netgen working directory.

```bash
cd ~/vlsi/cmos_inv/netgen
```

The following command was executed to compare the schematic and layout netlists:

```bash
netgen -batch lvs "../mag/inverter.spice inverter" "../xschem/inverter.spice inverter"
```

### 2.2 Command Explanation

- `netgen` – Launches the Netgen netlist comparison tool.
- `-batch` – Executes the comparison in batch mode without opening the graphical interface.
- `lvs` – Selects the Layout Versus Schematic comparison operation.
- `"../mag/inverter.spice inverter"` – Specifies the extracted layout netlist generated using Magic and the circuit name `inverter`.
- `"../xschem/inverter.spice inverter"` – Specifies the schematic netlist generated using Xschem and the circuit name `inverter`.

### 2.3 LVS Verification Results

After executing the command, Netgen compared the two netlists and displayed the comparison results.

The following observations were obtained:

- Both circuits contain **2 device instances**.
- Each circuit contains **1 PMOS transistor** (`sky130_fd_pr__pfet_01v8`).
- Each circuit contains **1 NMOS transistor** (`sky130_fd_pr__nfet_01v8`).
- Both circuits contain **4 electrical nets**.

### Final LVS Result

```text
Final result:
Circuits match uniquely.

LVS Done.
```

**Interpretation:**

The message `Circuits match uniquely` indicates that Netgen found a unique correspondence between the schematic and extracted layout circuits.

Both netlists contain the same number and types of devices and matching electrical connectivity. Therefore, the CMOS inverter layout successfully passed LVS verification.

**Image 1: Netgen LVS comparison output showing a successful unique match between the schematic and layout netlists.**
<img width="841" height="898" alt="lvs_done" src="https://github.com/user-attachments/assets/1208d4a4-dc8c-4514-9827-6af7b062fbe9" />

---

## Conclusion

The CMOS inverter layout was successfully compared with its original Xschem schematic using Netgen. Both circuits contained one PMOS, one NMOS and four electrical nets. The final result, **"Circuits match uniquely"**, confirms that the extracted layout netlist matches the schematic netlist.

With successful DRC verification in Magic and LVS verification in Netgen, the CMOS inverter design completed the physical verification flow.
