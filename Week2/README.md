# Week 2 – BabySoC Basics & Functional Simulation

This repository hosts all notes, experiments, and outcomes for **Week 2** of the VSD SoC learning track, with emphasis on **BabySoC basics** and **functional simulation**.

---

## Index  

1. [Introduction](#1-introduction)  
2. [Section A: Theory & Concepts](#2-section-a-theory--concepts)  
3. [Section B: Practical Simulation](#3-section-b-practical-simulation)  
4. [Resources](#4-resources)  

---

## 1. Introduction  

The goal of Week 2 is to strengthen our **grasp of SoC design fundamentals** and perform **hands-on functional simulation** with the BabySoC model.  

Main learning outcomes include:  

- Break down the architecture of a System-on-Chip (SoC)  
- Study interaction between CPU, memory, and peripheral blocks  
- Use **Icarus Verilog** for simulation and **GTKWave** for waveform analysis  
- Record insights from signal behavior and timing diagrams  

The work is organized into **two major sections**: theory + lab exercises.  

---

## 2. Part-1: Theory & Concepts  

**Aim:** Develop conceptual clarity on SoC design with BabySoC.  

**Topics Covered:**  
- SoC definition and relevance in modern electronics  
- Common SoC blocks: CPU core, memory, buses, peripherals, clock/reset circuitry  
- Why BabySoC is used as a learning-friendly abstraction  
- Importance of functional modelling before moving into RTL and physical design  
- Conceptual notes & diagrams  

**Outcome:** A markdown document with summarized theory, illustrations, and explanations.  

📂 [Go to Theory Notes](./Part-1/Deliverables.md)  

---

## 3. Part-2: Practical Simulation  

**Aim:** Run BabySoC simulations and analyze functional behavior.  

**Workflow:**  

- Compile BabySoC Verilog sources with **Icarus Verilog**  
- Generate `.vcd` files for waveform inspection  
- Verify reset sequence, clock operation, and signal transactions between CPU, memory, and peripherals  
- Capture GTKWave screenshots with annotated observations  
- Collect console logs and results for documentation  

**Outputs:**  

- Log files from simulation  
- Waveform screenshots + analysis notes  
- README with detailed observations  

📂 [Go to Lab Work](./Part-2/README.md)  

---

## 4. Resources  

1. Hemanth Kumar D M – *SFAL-VSD SoC Journey: Basics of SoC Design*  
   🔗 [GitHub Link](https://github.com/hemanthkumardm/SFAL-VSD-SoC-Journey)  

2. Icarus Verilog Docs – [http://iverilog.icarus.com](http://iverilog.icarus.com)  
3. GTKWave Guide – [http://gtkwave.sourceforge.net](http://gtkwave.sourceforge.net)  

