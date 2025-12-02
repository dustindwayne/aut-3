# 3. State Model — AUT-3

AUT-3 represents all computation and memory as optical state stored inside a
volumetric grid of voxels. Each voxel contains a multi-component vector:

`S(x, y, z) ∈ ℝ^K`

Components represent:
- wavelength-specific absorption  
- phase response  
- refractive index modification  
- nonlinear interaction terms  
- computed or stored values  

---

## 3.1 DWDM-Based Functional Channels

The AUT-3 medium separates functionality by **wavelength**, not hardware:

| Band           | Function            | Characteristics                                   |
|----------------|----------------------|---------------------------------------------------|
| **Red/IR**     | Storage              | Deep penetration; stable; minimal scattering      |
| **Green**      | RAM / Working Memory | Moderate depth; rewritable; mid-level interaction |
| **Blue/UV**    | Compute              | Shallow; nonlinear; high-energy femtosecond ops   |

The DWDM bands allow independent addressing of deep, mid, and shallow layers
without mutual occlusion.

---

## 3.2 Occlusion-Free Depth Access

Red/IR wavelengths pass through Green and Blue without disturbing them.
Green operates in a mid-band and does not touch Red/IR layers.
Blue/UV interacts only at shallow depth.

This eliminates the need for physical blockers for most use cases.

---

## 3.3 Optional Z-Gating Variant

Although DWDM solves depth-selective interaction, AUT-3 includes optional
Z-gating mechanisms:

- switchable transparency films  
- replaceable separators  
- nonlinear gating layers  
- write-limiter barriers  

These provide additional safety or redundancy for high-energy environments.

---

## 3.4 State Evolution

Voxel state evolves through:
- DWDM-targeted writes  
- femtosecond compute pulses  
- field propagation  
- natural relaxation (material-dependent)  

The digital shell schedules field events but does not compute.

---

## 3.5 Readout Fields

A 3D read laser array acquires:
- multi-angle projections  
- multi-wavelength absorption samples  
- phase/delay information  

Reconstruction yields the full state vector field across the volume.

---

## 3.6 Logical Data Mapping

Since storage, RAM, and compute are all spectral roles in the same volume:

- logical variables map to Green-layer voxels  
- tensors map to volumetric regions in Blue/UV  
- long-term structures map to Red/IR regions  
- ephemeral compute caches exist as Blue shallow fields  

This eliminates all device boundaries.
