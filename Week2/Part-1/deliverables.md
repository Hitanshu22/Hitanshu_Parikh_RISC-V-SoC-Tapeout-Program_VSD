# Week 2 – BabySoC Basics & Functional Modelling  
### Part 1: Conceptual Learning  

---

## Table of Contents
1. [What is a System-on-Chip (SoC)?](#1-what-is-a-system-on-chip-soc)  
2. [Major Building Blocks of an SoC](#2-major-building-blocks-of-an-soc)  
3. [Why BabySoC? A Learning-Friendly Model](#3-why-babysoc-a-learning-friendly-model)  
4. [Functional Modelling in the Design Flow](#4-functional-modelling-in-the-design-flow)  
5. [Key Takeaways](#5-key-takeaways)  
6. [Deliverable](#6-deliverable)  
7. [References](#7-references)  

---

## 1. What is a System-on-Chip (SoC)?  

A **System-on-Chip (SoC)** is an integrated circuit that places processor cores, memory, I/O interfaces, and control subsystems onto a **single silicon die**.  

Unlike traditional boards with separate chips, an SoC achieves:  
- Compact form factor  
- Reduced power consumption  
- Higher performance  
- Lower communication delay  

SoCs are present in **smartphones, IoT modules, routers, and automotive systems**. They represent the convergence of **hardware, firmware, and communication systems** into one device.  

---

## 2. Major Building Blocks of an SoC  

A typical SoC integrates the following components:  

### Processor / CPU Core  
- The control center of the chip.  
- Executes instructions and manages control signals.  
- Popular architectures include **RISC-V**, **ARM**, and **MIPS**.  
- Contains ALU, control unit, and registers.  

### Memory Subsystem  
- Stores both data and instructions.  
- **Volatile memory (SRAM/DRAM):** runtime use.  
- **Non-volatile memory (ROM/Flash):** permanent storage for firmware.  

### Peripherals  
- Provide interfaces for external communication.  
- Examples: **UART, SPI, I²C, Timers, GPIOs, ADC/DAC**.  

### Interconnect / Bus  
- Communication backbone between CPU, memory, and peripherals.  
- Standards include **AMBA (AHB/APB)** and **Wishbone**.  
- Manages data transfer, arbitration, and timing.  

### Clock and Reset Circuits  
- **Clock:** provides synchronous timing reference.  
- **Reset:** initializes modules into a known safe state.  

---

## 3. Why BabySoC? A Learning-Friendly Model  

The **BabySoC** is a scaled-down representation of a real SoC, used primarily for educational purposes.  

Advantages:  
- Demonstrates CPU–memory–peripheral communication.  
- Avoids the complexity of multi-core or deep pipelines.  
- Simplicity allows use of open-source tools such as **Icarus Verilog** and **GTKWave**.  
- Useful for studying reset, clock, and dataflow behavior.  

This makes BabySoC a **practical entry point** for SoC learning.  

---

## 4. Functional Modelling in the Design Flow  

**Functional Modelling** validates the **logical behavior** of an SoC before RTL or physical design.  

### Purpose  
- Verify design correctness at an early stage.  
- Detect functional or communication issues quickly.  
- Observe signals such as clock, reset, and data movement through waveforms.  

### Tools  
- **Icarus Verilog (iverilog):** compiles and simulates Verilog.  
- **GTKWave:** visualizes simulation results (`.vcd` files).  

### Workflow Example  
1. Compile BabySoC modules using `iverilog`.  
2. Run simulation and produce `.vcd` file.  
3. Open the file in `gtkwave` to examine signal activity.  

---

## 5. Key Takeaways  

- An SoC integrates CPU, memory, peripherals, buses, and clock/reset into one chip.  
- BabySoC offers a simplified but realistic platform to study SoC-level interactions.  
- Functional modelling acts as a **bridge between theory and RTL design**, ensuring correctness before implementation.  
- Open-source EDA tools like **iverilog** and **gtkwave** provide effective early validation.  

---

## 6. Deliverable  

A markdown document containing:  
- Explanation of SoC fundamentals  
- Components of SoC  
- Why BabySoC is used as a teaching model  
- Role of functional modelling before RTL and physical design  

---

## 7. References  

1. Hemanth Kumar D M, *SFAL-VSD SoC Journey – Fundamentals of SoC Design*  
   [GitHub Link](https://github.com/hemanthkumardm/SFAL-VSD-SoC-Journey/tree/main/11.%20Fundamentals%20of%20SoC%20Design)  

2. VLSI System Design (VSD) Initiative – *BabySoC Modules and Simulation Framework*  

