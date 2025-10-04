# Week 2 – BabySoC Fundamentals & Functional Modelling  
## Part 2: Practical Functional Modelling

---

## Table of Contents
1. [Reset Verification](#1-reset-verification)  
2. [Clock Operation](#2-clock-operation)  
3. [Inter-Module Data Movement](#3-inter-module-data-movement)  
4. [Simulation Process and Logs](#4-simulation-process-and-logs)  
5. [Final Remarks](#5-final-remarks)  

---

## 1. Reset Verification

### Probed Signals
reset, clk, cpu_out, cpu_to_mem, mem_out, mem_to_cpu, mem_to_periph, periph_out, periph_to_cpu

yaml
Copy code

### GTKWave Output  
<img width="1204" height="771" alt="reset_verification" src="https://github.com/user-attachments/assets/9caca34b-14bf-4f93-af44-065d6c6cad09" />

### Notes  
When the reset line is asserted (`reset = 1`), every module drives its output to `0` while the clock keeps toggling. This validates the reset logic for CPU, Memory, and Peripheral subsystems.

---

## 2. Clock Operation

### Probed Signals
clk, cpu_out, cpu_to_mem

yaml
Copy code

### GTKWave Output  
<img width="1204" height="771" alt="clock_operation" src="https://github.com/user-attachments/assets/744533f4-23d7-4e8d-a4b8-6c4c03dd518e" />

### Notes  
The clock oscillates at a stable rate. The CPU output (`cpu_out`) increments synchronously on each rising edge, indicating correct sequential behavior tied to the clock.

---

## 3. Inter-Module Data Movement

### Probed Signals
cpu_to_mem, mem_out, mem_to_cpu, mem_to_periph, periph_out, periph_to_cpu

perl
Copy code

### GTKWave Output  
<img width="1204" height="771" alt="data_movement" src="https://github.com/user-attachments/assets/10c8731d-0613-4a9b-a690-5ee3081a92b0" />

### Notes  
- CPU transmits values towards Memory (`cpu_to_mem`).  
- Memory increments the received value by 1 and forwards (`mem_out`, `mem_to_cpu`).  
- Peripheral receives from Memory, adds 2, and sends results (`periph_out`, `periph_to_cpu`).  

This verifies correct sequential propagation of information across all components.

---

## 4. Simulation Process and Logs

### Commands Executed
```bash
# Compile BabySoC modules
iverilog -o baby_soc_tb.vvp baby_soc_tb.v cpu.v memory.v peripheral.v baby_soc.v
bash
Copy code
# Run simulation
vvp baby_soc_tb.vvp
Simulation Output
Trace file generated: baby_soc.vcd

## 5. Final Remarks
Observations
Reset ensures all subsystems initialize safely with zeroed outputs.

Clock synchronizes operations, driving predictable increments in CPU behavior.

Data traverses the CPU → Memory → Peripheral path accurately, demonstrating functional correctness.

## Conclusion
This modelling activity provides strong evidence of reliable BabySoC operation. Reset, clock synchronization, and dataflow are verified through waveform analysis, highlighting fundamental SoC design concepts. The exercise reinforces confidence in reading simulation traces and builds the foundation for further RTL design and verification tasks.
