# 2. Physical Architecture — AUT-3

AUT-3 consists of:
- a volumetric optical medium (the compute–memory substrate)
- a 2D multi-wavelength write plane
- a 3D tomographic read array
- DWDM-capable emitter stacks
- multi-band photodiode sensors
- optional Z-gating layers
- minimal digital control electronics

---

## 2.1 Volumetric Medium

A solid or semi-solid optical material with:
- nonlinear response to Blue/UV pulses
- moderate absorption in Green wavelengths
- long absorption length in Red/IR
- fast relaxation time compatible with femtosecond compute

Candidate families:
- photorefractive crystals
- doped sol-gels
- volumetric chalcogenides
- engineered polymer-glass hybrids

---

## 2.2 2D Multi-Wavelength Write Plane

A high-resolution emitter grid:

- projects Red/Green/Blue/UV wavelengths  
- modulates intensity, pulse width, and temporal sequencing  
- focuses energy at specific depths via wavelength-dependent absorption  
- generates femtosecond compute pulses (<100 fs)  

This plane performs:
- storage writes (Red/IR)
- RAM updates (Green)
- compute injections (Blue/UV)

---

## 2.3 3D Read Subsystem (Tomographic Array)

The read system uses:
- multi-band photodiode arrays (regular, APD, or SPAD)
- volumetric probe beams
- multi-angle sampling
- depth-selective reconstruction

The tomographic solver reconstructs the full 3D voxel state vector field.

---

## 2.4 DWDM Spectral Layering

The architecture relies on **Dense Wavelength Division Multiplexing** to give
each spectral band a functional role:

- Red/IR → deep storage  
- Green → RAM  
- Blue/UV → compute  

These channels operate independently and do not occlude each other.

---

## 2.5 Optional Z-Selective Gating Layers

Z-gating layers are:
- electrically switchable transparent/opaque films  
- replaceable physical separators  
- nonlinear gating layers activated only during writes  

They provide:
- depth-specific write protection  
- safety against accidental deep overwrite  
- redundancy for harsh environments  

DWDM removes the *requirement* for Z-gating.  
Z-gating remains optional for enhanced separation.

---

## 2.6 Digital Shell

A minimal digital layer manages:
- laser drivers  
- pulse shaping  
- photodiode ADC  
- safety interlocks  
- external I/O  

It does not execute compute kernels.

---

## 2.7 Node Packaging

Nodes may be packaged:
- singly as standalone cubes  
- in 1D chains  
- in 2D arrays  
- in 3D meshes  

Nodes can share timing references, wavelength-locking telemetry, and readout coordination.

