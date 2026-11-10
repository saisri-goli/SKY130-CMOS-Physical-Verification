
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

## 3. VLSI Tools Installation

## 4. Git Cloning – Open_PDK and SKY130A
