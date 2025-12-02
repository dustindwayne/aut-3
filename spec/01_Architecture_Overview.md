# 1. Architecture Overview — AUT-3

AUT-3 is a complete computing architecture in which the entire machine—
compute, memory, cache, GPU, and storage—is implemented inside a unified
three-dimensional photonic medium. The architecture eliminates the classical
CPU/GPU/RAM/VRAM/SSD hierarchy. All operations occur optically within a
volumetric compute–memory substrate defined by wavelength-selective behavior.

A minimal digital shell is used only for:
- driving lasers and emitters
- photodiode readout
- safety interlocks
- I/O with external systems

The digital shell does not act as a CPU. No workload execution occurs outside the photonic volume.

---

## 1.1 Core Principles

1. **Unified Substrate**  
   AUT-3 merges compute, memory, cache, and long-term storage into one
   volumetric optical medium.

2. **DWDM Functional Separation**  
   Dense Wavelength Division Multiplexing gives each wavelength band a
   functional role:
   - Red/IR → Deep Storage
   - Green → RAM / Working Memory
   - Blue/UV → Compute / Logic

3. **Femtosecond Compute Operation (<100 fs)**  
   Compute pulses occur faster than lattice relaxation, enabling nonlinear
   operations without thermal deformation.

4. **3D Volumetric Readout**  
   State is reconstructed through tomographic imaging using multi-band
   photodiodes and probe-beam scanning.

5. **Closed-Loop Wavelength Locking**  
   Thermal drift causes refractive-index shifts; AUT-3 compensates by dynamically
   retuning emitter wavelengths.

6. **Optional Z-Selective Gating**  
   Physical or electro-optical gating layers allow depth-restricted writes when
   additional safety or separation is desired.

7. **Mesh Scaling**  
   Multiple AUT-3 nodes can be tiled into a volumetric compute fabric.

---

## 1.2 AUT-3 as a Total System Replacement

AUT-3 replaces:

- CPU execution units  
- GPU shader/tensor cores  
- RAM and VRAM  
- L1/L2/L3 cache  
- SSD/HDD/NVM storage  

All of these become optical state at different wavelengths and depths within the
same medium.

---

## 1.3 Elimination of Data Movement

In conventional computers, performance is limited by:

- CPU ↔ RAM transfer
- GPU ↔ VRAM transfer
- CPU ↔ GPU PCIe transfer
- RAM ↔ SSD transfer

AUT-3 eliminates this entirely:
**data never moves; computation moves to the data via optical fields.**

---

## 1.4 Execution Model Summary

- Compute occurs via Blue/UV pulses interacting with voxel state.
- RAM values reside in Green working-depth layers.
- Long-term data occupies Red/IR deep layers.
- The digital shell issues optical operations but does not compute.

---

## 1.5 Summary Statement

AUT-3 is not a processor or memory device.  
AUT-3 *is the computer*.

All compute and memory roles arise from wavelength-selective interaction of
optical fields with a volumetric medium.  
No classical architecture elements remain.
