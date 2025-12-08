---
title: "Optimized Deployment of Large Mixture-of-Experts (MoE) Models on Heterogeneous Analog–Digital AI Accelerators"
---

## Overview
This project develops an **efficient deployment framework** for large Mixture-of-Experts (MoE) models on **heterogeneous Analog–Digital AI accelerators**.  
Such systems combine **analog in-memory computing** with traditional **digital compute units**, enabling extremely high throughput but requiring specialized model optimization techniques.

The goal is to take advantage of analog efficiency while maintaining digital precision when needed, all with **theoretical guarantees** on performance.

---

## Key Contributions

### 🔹 1. Hybrid Execution Strategy  
Introduced a method that allocates MoE experts between:
- **Analog crossbar arrays** (for highly parallel, low-energy computation), and  
- **Digital compute units** (for precision-critical paths).

This hybrid scheme balances speed, energy efficiency, and accuracy.

### 🔹 2. In-Memory Computation for Experts  
Applied analog in-memory computing to store and process selected experts, reducing:
- Data movement  
- Latency  
- Energy consumption  

while preserving key routing characteristics.

### 🔹 3. Low-Bit Expert Computation with Theory  
Developed a low-bit computation method for digital experts with:
- Bounded approximation error  
- Preserved MoE decision consistency  
- Theoretical robustness guarantees  

### 🔹 4. Integrated Analog–Digital Optimization  
Combined analog and digital pathways into a unified optimization framework with formal performance guarantees.

### 🔹 5. Experimental Validation  
Early experimental results show:
- Strong inference speedups  
- Meaningful reduction in power use  
- Minimal impact on predictive accuracy  

(You can provide actual numbers, and I will update them.)

---

## Results Summary

- Efficient allocation of experts across analog–digital hardware  
- Lower compute cost while preserving performance  
- First theoretical analysis for heterogeneous MoE deployment  

---

## Status  
Completed the theoretical analysis.  
Experimentation phase is **ongoing**.

---

## Related Work
This project extends prior contributions on:
- Sparse MoE training theory  
- MoE expert pruning  
- Mixed-precision deployment for digital accelerators  

---

## Related Links
(Add links as available)

- Manuscript (coming soon)  
- Related ICML papers  
