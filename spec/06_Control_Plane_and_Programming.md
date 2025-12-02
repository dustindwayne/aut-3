# 6. Control Plane and Programming Model — AUT-3

The control plane orchestrates optical operations but does not execute computation.
All compute occurs inside the photonic medium.

---

# 6.1 Responsibilities

The control plane:

- configures DWDM emitters
- sequences Blue/UV compute pulses
- schedules Red/IR and Green writes
- coordinates tomographic readouts
- maintains wavelength-locking
- handles Z-gating activation (optional)
- performs safety checks and I/O

It is a **digital shell**, not a CPU.

---

# 6.2 Closed-Loop Wavelength Locking

Refractive-index drift shifts the absorption peaks of the medium.  
AUT-3 compensates with Closed-Loop Wavelength Locking:

1. Photodiodes measure Δλ drift.  
2. Controller computes required compensation.  
3. Emitters retune their wavelength by +Δλ or -Δλ.  
4. Storage/RAM/Compute channels remain aligned.

This eliminates the need for aggressive cooling.

---

# 6.3 Programming Paradigm

AUT-3 programs consist of:

- region selections  
- field exposures  
- pulse trains  
- wavelength masks  
- temporal sequences  

Programs resemble **optical kernels**, not instruction streams.

---

## 6.3.1 Region Masks

Regions may be:

- voxel subsets  
- slices  
- volumetric blocks  
- tensor-shaped areas  

---

## 6.3.2 Pulse Kernels

A pulse kernel defines:

- wavelength  
- pulse width  
- repetition rate  
- spatial mode  
- intensity  
- compute function  

---

## 6.3.3 Scheduling

Operations are ordered:

- block-level  
- region-level  
- global synchronization points  

There is no program counter.

---

# 6.4 Readout Programming

3D read operations:

- trigger probe beams  
- capture projections  
- reconstruct voxel state  
- provide digital export for diagnostics or persistence  

---

# 6.5 Integration With Digital Systems

AUT-3 appears externally as:

- a single compute unit  
- accepting optical-kernel descriptions  
- emitting digital readouts  

It does not expose CPU- or GPU-like programming models.

---

# 6.6 Summary

Programming AUT-3 means orchestrating:

- wavelengths  
- fields  
- regions  
- pulses  

The control plane is purely orchestration.  
The medium performs the computation.
