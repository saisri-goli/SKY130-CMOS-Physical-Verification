
# 01. Ubuntu Environment Setup

## Index

1. [Ubuntu Installation and Version Checking](#1-ubuntu-installation-and-version-checking)
2. [Additional Packages Installation](#2-additional-packages-installation)
3. [VLSI Tools Installation](#3-vlsi-tools-installation)
4. [Git Cloning – Open_PDK and SKY130A](#4-git-cloning--open_pdk-and-sky130a)

---

## 1. Ubuntu Installation and Version Checking
## 1. Ubuntu Installation and Version Checking

### 1.1 Introduction to Ubuntu

Ubuntu is a free and open-source Linux-based operating system widely used for software development, programming and engineering applications. Unlike Windows, which is a proprietary operating system, Ubuntu provides a flexible Linux environment with powerful command-line utilities and package management support.

For this project, Ubuntu was selected because several open-source VLSI design and physical verification tools, such as Xschem, Magic, Netgen and Ngspice, are supported in the Linux environment.

### 1.2 Virtual Machine Setup using Oracle VirtualBox

Oracle VirtualBox is a virtualization software that allows multiple operating systems to run on a single physical computer.

A Virtual Machine (VM) provides an isolated computing environment with allocated RAM, processor cores and virtual storage. In this project, Ubuntu was installed as a **Guest Operating System** inside Oracle VirtualBox, while Windows acts as the **Host Operating System**.

This setup enables us to work with Linux-based VLSI tools without replacing the existing Windows operating system.

### 1.3 Ubuntu Version and System Verification

After installing Ubuntu inside Oracle VirtualBox, the operating system version and system configuration were verified using the following terminal commands.

**1. Checking Ubuntu Version**

```bash
lsb_release -a
```

This command displays the Linux distribution information, including the Ubuntu version, release number and codename.

**2. Checking Kernel Version**

```bash
uname -r
```

Displays the currently running Linux kernel version. The kernel acts as an interface between the operating system and the computer hardware.

**3. Checking System Architecture**

```bash
uname -m
```

Displays the processor architecture of the system. The output `x86_64` indicates a 64-bit system architecture.

**4. Checking Disk Space**

```bash
df -h /
```

Displays the disk space usage of the root filesystem (`/`). The `-h` option presents the storage values in a human-readable format (GB, MB).

### Verification Results

The following system configuration was observed:

| Parameter | Verified Output |
|---|---|
| Operating System | Ubuntu 24.04.5 LTS |
| Release | 24.04 |
| Codename | Noble |
| Kernel Version | 7.0.0-42-generic |
| Architecture | x86_64 |
| Root Filesystem | 74 GB |
| Available Storage | 26 GB |

**Figure 1: Ubuntu version and system configuration verification using terminal commands.**
<img width="1217" height="437" alt="ubuntu version" src="https://github.com/user-attachments/assets/a8070d70-a4ec-4b6a-9e52-a5f28953b56c" />


## 2. Additional Packages Installation
## 2. Additional Packages Installation

Before installing the open-source VLSI tools, essential development packages and build utilities were installed in Ubuntu. These packages provide the compilers, build automation and parsing utilities required for compiling and configuring the tools from source.

### 2.1 Package Installation and Version Verification

The following packages were installed and their versions were verified using terminal commands.

**1. Git**

```bash
git --version
```
Git is a distributed version control system used to clone repositories, manage source code and track project changes.

**Verified Version:** 2.43.0

**2. GCC (GNU Compiler Collection)**

```bash
gcc --version
```
GCC is a compiler used to compile C programs and source code. It is required when building several open-source EDA tools.

**Verified Version:** 13.3.0

**3. GNU Make**

```bash
make --version
```
GNU Make is a build automation utility that executes instructions defined in Makefiles to compile and build software projects.

**Verified Version:** 4.3

**4. Flex (Fast Lexical Analyzer)**

```bash
flex --version
```
Flex is a lexical analyzer generator used to generate scanners that recognize patterns in input text. It is commonly required during software compilation.

**Verified Version:** 2.6.4

**5. Bison**

```bash
bison --version
```
Bison is a parser generator used to convert grammar specifications into parsers. It is often used along with Flex while building software tools.

**Verified Version:** 3.8.2

**6. pkg-config**

```bash
pkg-config --version
```
pkg-config is a utility that provides information about installed libraries, including compiler and linker flags required during software compilation.

**Verified Version:** 1.8.1

### Verification Results

All the above development utilities were checked successfully using their respective version commands.

**Figure 2: Version verification of installed development packages in Ubuntu.**
<img width="1221" height="782" alt="packages" src="https://github.com/user-attachments/assets/bd3e1467-a482-4296-8bad-370a3e81d626" />


## 3. VLSI Tools Installation
## 3. VLSI Tools Installation

### Introduction

To perform CMOS schematic design, circuit simulation, layout creation and physical verification using the SKY130 PDK, the required open-source VLSI tools were installed in Ubuntu.

The following tools were installed from their respective source repositories.

### 3.1 Magic – VLSI Layout Tool

Magic is an open-source VLSI layout editor used for creating and editing integrated circuit layouts. It also provides built-in Design Rule Checking (DRC) and layout extraction capabilities.

**Installation Steps:**

Clone the Magic source repository:

```bash
git clone https://github.com/RTimothyEdwards/magic.git
```

Navigate to the downloaded directory and configure the source:

```bash
cd magic
./configure
```

Compile and install Magic:

```bash
make -j$(nproc)
sudo make install
cd ..
```

**Official Documentation:** [Magic VLSI](http://opencircuitdesign.com/magic/)

### 3.2 Netgen – LVS Verification Tool

Netgen is an open-source netlist comparison tool used for Layout Versus Schematic (LVS) verification. It compares the extracted layout netlist with the schematic netlist to check whether both designs are electrically equivalent.

**Installation Steps:**

Clone the Netgen source repository:

```bash
git clone https://github.com/RTimothyEdwards/netgen.git
```

Navigate to the Netgen directory and configure:

```bash
cd netgen
./configure
```

Compile and install Netgen:

```bash
make -j$(nproc)
sudo make install
cd ..
```

**Official Documentation:** [Netgen](http://opencircuitdesign.com/netgen/)

### 3.3 Xschem – Schematic Capture Tool

Xschem is an open-source schematic capture program used to create and edit electronic circuit schematics. It supports hierarchical circuit design and generates SPICE netlists for circuit simulation.

**Installation Steps:**

Clone the Xschem source repository:

```bash
git clone https://github.com/StefanSchippers/xschem.git
```

Navigate to the Xschem directory and configure:

```bash
cd xschem
./configure
```

Compile and install Xschem:

```bash
make -j$(nproc)
sudo make install
cd ..
```

**Official Documentation:** [Xschem](https://xschem.sourceforge.io/)

### 3.4 Ngspice – Circuit Simulation Tool

Ngspice is an open-source SPICE-based circuit simulator used for analyzing the electrical behavior of electronic circuits. It supports DC, AC and transient simulations and is used to verify circuit functionality.

**Installation Steps:**

Download the Ngspice source archive:

```bash
wget https://sourceforge.net/projects/ngspice/files/ng-spice-rework/37/ngspice-37.tar.gz
```

Extract the downloaded archive:

```bash
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
```

Create a separate build directory:

```bash
mkdir release
cd release
```

Configure Ngspice with X11 and Readline support:

```bash
../configure --with-x --with-readline=yes --disable-debug
```

Compile and install Ngspice:

```bash
make -j$(nproc)
sudo make install
cd ../..
```

**Official Documentation:** [Ngspice](https://ngspice.sourceforge.io/)

### 3.5 Xterm – Terminal Emulator

Xterm is a terminal emulator for the X Window System. It provides a terminal window for executing commands and is useful for displaying simulation-related terminal windows and graphical output.

**Installation Steps:**

Update the Ubuntu package lists:

```bash
sudo apt-get update
```

Install Xterm:

```bash
sudo apt-get install -y xterm
```

**Official Documentation:** [Xterm](https://invisible-island.net/xterm/)

### 3.6 VLSI Tools Installation Verification

After completing the installation, all five tools were checked to ensure that they were accessible from the Ubuntu terminal.

The following commands were used for verification:

```bash
magic -v
netgen -v
xschem --version
ngspice --version
xterm -version
```

All five tools were verified successfully.

**Figure 3: Combined verification of installed VLSI tools – Magic, Netgen, Xschem, Ngspice and Xterm.**
<img width="1546" height="761" alt="VLSI TOOLS" src="https://github.com/user-attachments/assets/77a50c1b-53f6-43cc-b3f5-6278d59d1f22" />


## 4. Git Cloning – Open_PDK - SKY130A
## 4. Git Cloning – Open_PDK and SKY130A

### 4.1 Introduction to SKY130 PDK

SKY130 is an open-source 130 nm CMOS Process Design Kit (PDK) developed by SkyWater Technology in collaboration with Google. It provides the technology files, device models, design rules and standard cell libraries required for designing and verifying CMOS integrated circuits.

A Process Design Kit (PDK) acts as an interface between the semiconductor fabrication technology and electronic design automation (EDA) tools.

### 4.2 Open_PDK

Open_PDK is an open-source project that provides the necessary technology files and configurations to use supported semiconductor processes, including SKY130, with open-source EDA tools such as Magic, Netgen and Ngspice.

### 4.3 Installation and Configuration

The Open_PDK repository was cloned using Git to obtain the required process technology files.

**Step 1: Clone the Open_PDK repository**

```bash
git clone https://github.com/RTimothyEdwards/open_pdks.git
```

**Step 2: Navigate to the cloned directory**

```bash
cd open_pdks
```

**Step 3: Configure the build for SKY130 PDK**

```bash
./configure --enable-sky130-pdk
```

This enables the SKY130 process during configuration.

**Step 4: Compile and install**

```bash
make -j$(nproc)
sudo make install
```

The build process prepares and installs the configured PDK files for use with the supported EDA tools.

### 4.4 Repository Cloning Verification

After cloning the repository, the directory structure was checked to verify that the required source files and SKY130-related directories were available.

**Figure 4: Verification of successfully cloned Open_PDK and SKY130 repository paths.**
<img width="1177" height="557" alt="sky" src="https://github.com/user-attachments/assets/ed8b8ff7-09ac-45c7-a37a-a81e0f05d565" />


### Conclusion

The Ubuntu environment was successfully prepared with the required development packages, open-source VLSI tools and SKY130 PDK. This setup provides the foundation for CMOS inverter schematic design, simulation, layout creation, DRC and LVS verification.
