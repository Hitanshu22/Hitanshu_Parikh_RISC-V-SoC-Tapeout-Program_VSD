# Week 2 – BabySoC Fundamentals & Functional Modelling  
## Part 2: Hands-on Functional Modelling  

---

## Table of Contents
1. [Reset Behavior](#1-reset-behavior)
2. [Clock Operation](#2-clock-operation)
3. [Dataflow Between Modules](#3-dataflow-between-modules)
4. [Simulation Workflow & Logs](#4-simulation-workflow-&-logs)
5. [Observations and Conclusion](#5-observation-and-conclusion)

---

## 1. Reset Behavior

**Signals Monitored**

| Signal Name      | Description |
|-----------------|-------------|
| reset           | Reset input signal |
| clk             | System clock |
| cpu_to_mem      | Data from CPU to Memory |
| mem_to_cpu      | Data returned from Memory to CPU |
| mem_to_periph   | Data sent from Memory to Peripheral |
| periph_to_cpu   | Data returned from Peripheral to CPU |

**Waveform Snapshot**  

![Reset Operation](https://github.com/user-attachments/assets/9caca34b-14bf-4f93-af44-065d6c6cad09)

**Observation:**  
When `reset` is active, all modules initialize their outputs properly while the clock continues to toggle. This confirms correct reset behavior across CPU, Memory, and Peripheral modules.

---

## 2. Clock Operation

**Signals Monitored**

| Signal Name   | Description |
|---------------|-------------|
| clk           | System clock |
| cpu_to_mem    | Data from CPU to Memory |
| mem_to_cpu    | Data returned from Memory to CPU |

**Waveform Snapshot**  

![Clock Signal](https://github.com/user-attachments/assets/744533f4-23d7-4e8d-a4b8-6c4c03dd518e)

**Observation:**  
The clock toggles steadily. Data transfer between CPU and Memory occurs synchronously with the clock, verifying proper sequential operation.

---

## 3. Dataflow Between Modules

**Signals Monitored**

| Signal Name     | Description |
|-----------------|-------------|
| cpu_to_mem      | CPU → Memory |
| mem_to_cpu      | Memory → CPU |
| mem_to_periph   | Memory → Peripheral |
| periph_to_cpu   | Peripheral → CPU |

**Waveform Snapshot**  

![Dataflow](https://github.com/user-attachments/assets/10c8731d-0613-4a9b-a690-5ee3081a92b0)

**Observation:**  
- CPU sends data to Memory (`cpu_to_mem`).  
- Memory processes the data and returns it to CPU (`mem_to_cpu`).  
- Memory also sends data to Peripheral (`mem_to_periph`), which returns processed data to CPU (`periph_to_cpu`).  
- This confirms correct propagation and interaction between the functional modules.

---

## 4. Simulation Workflow & Logs

**Compilation Command**  
```bash
iverilog -o baby_soc_tb.vvp baby_soc_tb.v cpu.v memory.v peripheral.v baby_soc.v
```
### Run simulation
```
vvp baby_soc_tb.vvp
```

### Output: -
**Uploaded as** ***[baby_soc.vcd](baby_soc.vcd)***

## 5. Observation and Conclusion

**Observation: -**  
The BabySoC functional modelling correctly demonstrates the expected behavior of all modules. During reset, all outputs initialize to zero while the clock continues toggling. CPU, Memory, and Peripheral data propagate correctly, showing proper communication between modules. Waveform analysis confirms synchronous operation and accurate dataflow.  

**Conclusion: -**  
This hands-on exercise strengthens understanding of SoC fundamentals, prepares for more advanced RTL design and verification, and builds confidence in interpreting simulation waveforms for system-level debugging. It validates the BabySoC design workflow and ensures that CPU, Memory, and Peripheral modules function as intended.
