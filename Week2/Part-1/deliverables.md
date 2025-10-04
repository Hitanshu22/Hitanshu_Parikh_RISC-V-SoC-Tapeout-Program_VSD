# 🚀 Week 2 – BabySoC Basics & Functional Modelling  

### 📘 **Part 1: Conceptual Learning**  

---

## 📑 Contents  
1. [🔎 What is a System-on-Chip (SoC)?](#1-what-is-a-system-on-chip-soc)  
2. [🧩 Major Building Blocks of an SoC](#2-major-building-blocks-of-an-soc)  
3. [🎓 Why BabySoC? A Learning-Friendly Model](#3-why-babysoc-a-learning-friendly-model)  
4. [⚙️ Functional Modelling in Design Flow](#4-functional-modelling-in-design-flow)  
5. [📝 Key Takeaways](#5-key-takeaways)  
6. [📂 Deliverable](#deliverable)  
7. [🔗 References](#references)  

---

## 1. 🔎 What is a System-on-Chip (SoC)?  

A **System-on-Chip (SoC)** is a **single silicon chip** that integrates:  
- 🖥️ **Processor core**  
- 🗄️ **Memory modules**  
- 🔌 **I/O interfaces & peripherals**  
- ⚡ **Control & communication subsystems**  

Unlike conventional systems spread across multiple chips, an SoC delivers:  
✅ Compact design  
✅ Higher performance  
✅ Lower power usage  
✅ Faster interconnects  

SoCs power everyday tech: **smartphones, IoT devices, automotive ECUs, and edge processors.**

---

## 2. 🧩 Major Building Blocks of an SoC  

Think of an SoC as a **mini-city on silicon**, where each block has a role:

### 🧠 Processor / CPU Core  
- Acts as the **central brain**.  
- Executes instructions and manages control.  
- Architectures: **RISC-V**, **ARM**, **MIPS**.  
- Contains ALU + Control Unit + Registers.  

### 💾 Memory Subsystem  
- Stores **instructions** and **data**.  
- **Volatile (SRAM/DRAM):** temporary, runtime use.  
- **Non-volatile (ROM/Flash):** permanent storage for boot + firmware.  

### 🔗 Interconnect / Bus  
- The **highway system** of the chip.  
- Links CPU ↔ Memory ↔ Peripherals.  
- Standards: **AMBA (AHB/APB)**, **Wishbone**.  
- Handles arbitration & bandwidth distribution.  

### 📡 Peripherals  
- Interfaces with the outside world.  
- Examples: **UART, SPI, I²C, GPIO, ADC/DAC, Timers**.  

### ⏱️ Clock & Reset  
- **Clock:** defines the rhythm for synchronous operation.  
- **Reset:** ensures safe startup state.  

---

## 3. 🎓 Why BabySoC? A Learning-Friendly Model  

The **BabySoC** is a **scaled-down SoC** for education, not complexity.  

✨ Benefits:  
- Visualizes **CPU ↔ Memory ↔ Peripheral interaction**.  
- Strips away multi-core/pipeline overhead.  
- Simple enough to simulate with **Icarus Verilog + GTKWave**.  
- Great for experimenting with **clocks, resets, and bus communication**.  

👉 It’s the **training wheels** for mastering real-world SoCs.  

---

## 4. ⚙️ Functional Modelling in Design Flow  

**Functional Modelling** = the step before RTL implementation & physical design.  
It ensures the design behaves logically **before heavy synthesis.**  

### 🎯 Why it matters:  
- ✅ Early bug detection in architecture  
- ✅ Logical validation of block behavior  
- ✅ Clock + Reset + Dataflow waveform checks  
- ✅ Builds confidence for downstream RTL/PD stages  

### 🛠️ Tools & Workflow  
1. **Icarus Verilog (iverilog):** compile + simulate  
2. **GTKWave:** view waveforms (`.vcd` dumps)  
3. Inspect signal activity → reset, clock ticks, CPU-memory transactions  

---

## 5. 📝 Key Takeaways  

- A System-on-Chip = **CPU + Memory + Peripherals + Bus + Clock/Reset** on one chip.  
- BabySoC = **simplified playground** to understand how modules talk.  
- Functional modelling = **bridge from concept → RTL**.  
- Tools: **iverilog + gtkwave** = 💯 open-source simulation toolkit.  

---

## 📂 Deliverable  

📌 Markdown write-up must include:  
- ✅ SoC fundamentals explanation  
- ✅ Block-wise description  
- ✅ Why BabySoC is chosen  
- ✅ Role of functional modelling in design cycle  

---

## 🔗 References  

1. Hemanth Kumar D M – *SFAL-VSD SoC Journey: Fundamentals of SoC Design*  
   🔗 [GitHub Link](https://github.com/hemanthkumardm/SFAL-VSD-SoC-Journey/tree/main/11.%20Fundamentals%20of%20SoC%20Design)  

2. VLSI System Design (VSD) – *BabySoC modules & simulation framework*  

3. Docs:  
   - 📘 [Icarus Verilog](http://iverilog.icarus.com)  
   - 📘 [GTKWave](http://gtkwave.sourceforge.net)  

