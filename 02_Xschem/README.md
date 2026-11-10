# 02. Xschem – CMOS Inverter Design and Simulation

## Index

1. [Introduction and Xterm Integration](#1-introduction-and-xterm-integration)
2. [CMOS Inverter Schematic](#2-cmos-inverter-schematic)
3. [Inverter Testbench](#3-inverter-testbench)
4. [Output Waveform](#4-output-waveform)

---

## 1. Introduction and Xterm Integration

Xschem is an open-source schematic capture tool used to design and edit electronic circuits. It allows users to create circuit schematics using components from technology-specific libraries and generate SPICE netlists for simulation.

In this project, Xschem was used to design a CMOS inverter using the SKY130 PDK.

**Role of Xterm:**

Xterm is a terminal emulator used to execute commands and display simulation logs and outputs. It works alongside Xschem by providing a terminal environment for launching and monitoring circuit simulations using Ngspice.

**Tools involved:**
- Xschem – Schematic design and testbench creation.
- Ngspice – Circuit simulation.
- Xterm – Terminal access and simulation output monitoring.

## 2. CMOS Inverter Schematic

An initial schematic named `inverter.sch` was created by placing components from the `sky130_fd_pr` library.

The CMOS inverter consists of one PMOS transistor and one NMOS transistor connected in a complementary configuration.

**Transistor Details:**

- **PMOS (XM2):** `sky130_fd_pr__pfet_01v8`
  - Width (W) = 3 µm
  - Length (L) = 0.18 µm
  - Number of fingers (nf) = 3

- **NMOS (XM1):** `sky130_fd_pr__nfet_01v8`
  - Width (W) = 4.5 µm
  - Length (L) = 0.18 µm
  - Number of fingers (nf) = 3

**Input and Output Pin Labels:**

The following pins were defined in the schematic:

- `in` – Input signal - Ipin.sym
- `out` – Output signal - Opin.sym
- `vdd` – Positive supply voltage - iopin.sym
- `vss` – Ground reference iopin.sym

**Image 1: CMOS inverter schematic designed using Xschem and SKY130 PDK.**
<img width="1590" height="847" alt="schematic" src="https://github.com/user-attachments/assets/91be5e66-ee8a-4a79-8639-663596df0ea3" />


---

## 3. Inverter Testbench

After completing the CMOS inverter schematic, it was converted into a reusable symbol and instantiated in a separate testbench named `inverter_tb.sch`.

The testbench was created to provide input signals and power supply connections to verify the inverter functionality.

**Components Used:**

1. **CMOS Inverter Symbol:** The previously designed inverter schematic was converted into a symbol and inserted into the testbench.
2. **DC Voltage Source:** A supply voltage of 1.8 V was connected to the VDD terminal.
3. **Input Voltage Source:** A time-varying input source was connected to the inverter input to observe its switching behaviour.
4. **Ground (GND):** A common ground reference was connected to the circuit.

**Simulation Control Directives:**

The simulation control statements were added to perform transient analysis and plot the input and output voltages.

```spice
.control
tran 1n 1u
plot V(in) V(out)
.endc
```

**Explanation:**

- `tran 1n 1u` – Performs transient analysis with a time step of 1 ns for a total simulation duration of 1 µs.
- `plot V(in) V(out)` – Displays the input and output voltage waveforms.
- `.control` and `.endc` – Define the simulation control block.

**Image 2: CMOS inverter testbench created using Xschem with supply, input source and simulation control connections.**
<img width="1373" height="783" alt="inv_tb" src="https://github.com/user-attachments/assets/232b9a23-359b-4b2f-9d1c-1ba68ac4f81b" />

---

## 4. Output Waveform

After configuring the testbench, transient simulation was performed using Ngspice. The input and output voltage waveforms were plotted to verify the CMOS inverter operation.

**Waveform Description:**

The waveform contains two signals:

- **Input Voltage – V(in) (Red):** Represents the voltage applied at the inverter input. It varies from 0 V to 1.8 V.
- **Output Voltage – V(out) (Blue):** Represents the voltage obtained at the inverter output. It changes in the opposite direction to the input.

**Graph Axes:**

- **X-axis – Time (µs):** Represents the simulation time in microseconds, ranging from 0 to 1 µs.
- **Y-axis – Voltage (V):** Represents the input and output voltage levels, ranging from approximately 0 V to 1.8 V.

**Working Principle:**

A CMOS inverter produces an output that is logically complementary to its input.

- When the input is LOW (0 V), the PMOS transistor turns ON and the NMOS transistor turns OFF, making the output HIGH (approximately 1.8 V).
- When the input is HIGH (1.8 V), the PMOS transistor turns OFF and the NMOS transistor turns ON, making the output LOW (approximately 0 V).

In the obtained waveform, the output initially remains HIGH. As the input voltage increases, the output switches from HIGH to LOW, demonstrating the inverter's switching behaviour.

**Image 3: Transient input and output waveforms of the CMOS inverter simulated using Ngspice.**
<img width="1328" height="866" alt="output_waveforms" src="https://github.com/user-attachments/assets/c98cc3c8-45e4-457e-9202-cfef50cf332f" />

---

## Conclusion

The CMOS inverter was successfully designed using Xschem with the SKY130 PDK. A separate testbench was created by converting the inverter schematic into a symbol and connecting the required supply and input sources. Transient simulation using Ngspice verified the complementary switching behaviour of the CMOS inverter.
