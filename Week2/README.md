![Week2-1](https://github.com/user-attachments/assets/92b17ae6-7f95-4b9e-95b4-3e0b9291bf05)![Week2-3](https://github.com/user-attachments/assets/3c475515-4a15-4e08-b9a8-abc604a03b1c)![Week2-2](https://github.com/user-attachments/assets/10b6c0af-58f8-4774-a120-da3da0e43f70)# Week 2 – Fundamentals of BabySoC & Functional Modelling  

## Overview
The semiconductor industry continually strives for higher integration, efficiency, and performance. A **System-on-Chip (SoC)** embodies this evolution by combining multiple essential computing components into a single integrated circuit (IC).  

Unlike traditional designs that rely on multiple discrete chips interconnected via a PCB, an SoC integrates the **CPU, memory, peripherals, and interconnects** on a single chip. This reduces size, power consumption, and cost while improving performance. SoCs power modern devices ranging from smartphones and IoT gadgets to advanced computing platforms.  

This document introduces SoC fundamentals, the educational **BabySoC** model, and the significance of **functional modelling** in the SoC design process.  

---

## Understanding a System-on-Chip (SoC)  
A **System-on-Chip** consolidates all critical computing modules into a single silicon die.  

### Advantages of SoCs
- **Compact design**: Reduces board space by replacing multiple ICs.  
- **High performance**: On-chip communication is faster than off-chip interconnects.  
- **Energy efficiency**: Optimized integration minimizes power consumption.  
- **Cost-effective**: Fewer components translate to lower manufacturing costs.  
- **Flexible scaling**: Base architectures can be adapted for diverse applications.  

SoCs are particularly crucial in **resource-constrained environments** such as embedded systems and mobile devices.  

---

## Key Components of a Typical SoC  

### 1. Central Processing Unit (CPU)
- Functions as the **brain** of the SoC.  
- Executes instructions, controls system flow, and performs computations.  
- Can be general-purpose (ARM, RISC-V) or specialized (DSP, custom accelerators).  

### 2. Memory
- **Volatile (SRAM, DRAM)**: Temporary storage for program execution and data.  
- **Non-volatile (Flash, ROM)**: Permanent storage for firmware and configurations.  
- Supports **instruction memory** for programs and **data memory** for runtime operations.  

### 3. Peripherals
- Facilitate interaction between the SoC and external environment.  
- Typical peripherals include:  
  - **GPIO (General Purpose Input/Output)**  
  - **Communication interfaces**: UART, I2C, SPI  
  - **Timers and counters**  
  - **Interrupt controllers**  

### 4. Interconnect (Bus/Fabric)
- Acts as the **communication backbone** between CPU, memory, and peripherals.  
- Needs to handle high bandwidth with minimal latency.  
- Examples include **AMBA buses** (AXI, AHB, APB).  

---

## Why Learn with BabySoC?
The **BabySoC** is an educational, simplified SoC designed to help students grasp core concepts without the complexity of full-scale industrial SoCs.  

**Highlights of BabySoC:**
- Minimalistic CPU core for basic instruction execution.  
- Compact memory modules for easier understanding.  
- A limited set of peripherals, focusing on essentials.  
- Lightweight interconnect for simplified signal flow.  

**Benefits for learners:**
- Grasp **fundamental SoC architecture** without distraction.  
- Trace and analyze signals through simulation tools.  
- Understand inter-module communication and control.  
- Gain confidence before tackling complex RTL or physical designs.  

---

## Functional Modelling in SoC Design
SoC development follows several stages:  

1. **Specification** – Define the desired functionality.  
2. **Functional Modelling** – Abstract-level simulation and verification.  
3. **RTL Design** – Cycle-accurate hardware description in Verilog/VHDL.  
4. **Synthesis & Physical Design** – Convert RTL into gate-level netlists and layouts.  
5. **Fabrication & Post-Silicon Testing** – Manufacture and validate the chip.  

### Importance of Functional Modelling
- **Early validation**: Test architecture feasibility before RTL.  
- **Design exploration**: Adjust memory sizes, bus widths, and instruction flows.  
- **Simplified debugging**: Easier identification of logic issues at high-level.  
- **Resource efficiency**: Reduces design rework, saving time and cost.  

**Common tools for simulation:**
- **Icarus Verilog** – Open-source Verilog simulator.  
- **GTKWave** – Signal waveform viewer for visual analysis.  

Functional modelling allows students to observe CPU-memory-peripheral interactions and verify BabySoC behavior before moving to RTL or synthesis.  

---

## 🛠 Setting Up BabySoC

### Clone the Project
```bash
cd ~/VLSI
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC
```

🔄 Convert TLV to Verilog
RVMYTH uses TL-Verilog (.tlv) and needs conversion to Verilog.
Steps:

# Install tools
```bash
sudo apt update
sudo apt install python3-venv python3-pip

# Set up virtual environment
python3 -m venv sp_env
source sp_env/bin/activate

# Install SandPiper-SaaS
pip install pyyaml click sandpiper-saas
# Convert TLV to Verilog
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```
Output: rvmyth.v in src/module/.

---

### 🧪 Running Simulation

#### 🔹 Pre-Synthesis Simulation
```bash
mkdir -p output/pre_synth_sim

iverilog -o output/pre_synth_sim/pre_synth_sim.out \
  -DPRE_SYNTH_SIM \
  -I src/include -I src/module \
  src/module/testbench.v

cd output/pre_synth_sim
./pre_synth_sim.out
```

#### 📊 View Waveforms
Run:
```bash
gtkwave output/pre_synth_sim/pre_synth_sim.vcd
```

#### Output Waveform
![Week2-1](https://github.com/user-attachments/assets/596c6623-3ed5-4b40-924a-e1b306bd90b8)
![Week2-2](https://github.com/user-attachments/assets/947ac378-25dc-4404-b966-37aad113d606)
![Week2-3](https://github.com/user-attachments/assets/ab33c02f-0b1e-4984-93fc-bff44b7a64ee)

### 🧠 How the CPU Works

- The CPU runs a fixed program to:
  - Count numbers.
  - Store results in r17.
  - Create waveforms for DAC.
  - Loop indefinitely.

### BabySoC CPU Instruction Sequence

The BabySoC executes a simple loop-based program that drives the DAC (`r17`). The sequence is as follows:

| Instruction            | Operation Description                                         |
|-------------------------|---------------------------------------------------------------|
| `ADDI r9, r0, 1`       | Initialize **step size** → `r9 = 1`                            |
| `ADDI r10, r0, 43`     | Set **loop limit** → `r10 = 43`                               |
| `ADDI r11, r0, 0`      | Initialize **counter** → `r11 = 0`                            |
| `ADDI r17, r0, 0`      | Initialize **DAC input** → `r17 = 0`                          |
| `ADD r17, r17, r11`    | Accumulate counter value into DAC register                    |
| `ADDI r11, r11, 1`     | Increment counter (`r11 = r11 + 1`)                           |
| `BNE r11, r10, -4`     | Loop until counter reaches loop limit (`r11 = 43`)            |
| `ADD r17, r17, r11`    | Add counter again to DAC register                             |
| `SUB r17, r17, r11`    | Subtract counter from DAC register                            |
| `SUB r11, r11, r9`     | Decrement counter (`r11 = r11 - 1`)                           |
| `BNE r11, r9, -4`      | Loop until counter reduces to step size (`r11 = 1`)           |
| `SUB r17, r17, r11`    | Adjust DAC register with final subtraction                    |
| `BEQ r0, r0, ...`      | Infinite loop (halts program by continuously branching)        |

#### Program Phases
  - Ramp Up: r11 = 0 to 42, r17 sums to 903, steady increase.
  - Peak: r11 = 43, r17 = 946, maximum value.
  - Oscillation: r11 = 43 to 1, r17 = 903 ± r11, up-and-down pattern.
  - Final: r11 = 1, r17 adjusted, holds steady.
  - Flow: Instructions → CPU → r17 → DAC → Analog Output.

### 📈 DAC Output

Converts r17 to voltage using:

#### Scaling:
$$
V_{OUT} = \frac{r_{17}}{1023} \times V_{REF\_SPAN} \quad (\text{with } V_{REF\_SPAN} = 1.0\ \text{V})
$$

Example voltages:
- r17 = 903, Vout = 0.882 V.
- r17 = 946, Vout = 0.925 V.

In GTKWave, set OUT to Analog Step for visualization.

---

## Conclusion  
Modern electronic devices rely heavily on SoCs because of their compactness, performance, and efficiency. Understanding their architecture and design flow is essential for anyone entering the semiconductor and VLSI domains.  

The **BabySoC** model provides a beginner-friendly platform to learn these concepts. It abstracts the overwhelming complexity of industrial SoCs into a minimal, manageable design while still teaching the **fundamentals of CPU, memory, interconnect, and peripherals**.  

Through **functional modelling** with simulation tools like Icarus Verilog and GTKWave, students gain early exposure to the design process, validate their understanding, and prepare themselves for advanced stages such as RTL design and physical implementation.  

In summary, BabySoC bridges the gap between theory and practice, laying the foundation for becoming proficient in **SoC design and VLSI engineering**.  

---
