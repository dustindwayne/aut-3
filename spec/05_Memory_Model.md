# 5. Memory Model — AUT-3

AUT-3 eliminates the classical memory hierarchy.  
There is no RAM, VRAM, cache, or SSD.  
All "memory types" are spectral roles inside a single medium defined by DWDM.

Memory is **not a device**.  
Memory is **a wavelength**.

---

## 5.1 Spectral Memory Layers

| Spectral Band | Memory Role              | Behavior |
|---------------|---------------------------|----------|
| **Red/IR**    | Long-Term Storage         | Deep penetration, durable |
| **Green**     | RAM / Working Memory      | Fast rewrites, active region |
| **Blue/UV**   | Compute-Transient Storage | High-energy, volatile |

---

## 5.2 In-Place Memory

All memory is in-place.  
No movement, paging, or copying.

Logical data structures map directly onto regions of the volume:

- scalars → voxel or small cluster  
- matrices → slices  
- tensors → volumetric blocks  

---

## 5.3 Memory Consistency Model

Memory consistency arises from:

- optical sequencing  
- pulse ordering  
- wavelength-channel constraints  
- reconstruction stability  

There is no cache coherency protocol.

---

## 5.4 Long-Term Storage (Red/IR)

Red/IR wavelengths reach deep layers and do not interact with RAM or compute.

Used for:

- operating state  
- firmware  
- model weights  
- file-like structures  
- physical backups  

---

## 5.5 Working Memory (Green)

Green wavelengths:

- absorb at mid-depth  
- rewrite quickly  
- coexist with Blue/UV compute without interference  

This is the equivalent of RAM and VRAM.

---

## 5.6 Compute Transients (Blue/UV)

Compute operates at shallow depth.  
Blue/UV values are volatile and replaced frequently.

Equivalent to:

- registers  
- L1 cache  
- shader registers  
- tensor accumulation buffers  

---

## 5.7 Optional Z-Gating

Z-gating can enforce:

- write protection  
- deep-storage safety  
- compute isolation  

Used primarily for high-energy environments or redundancy requirements.

---

## 5.8 External Persistence

Even though AUT-3 holds long-term storage internally, external persistence may be used for:

- system bootstrapping  
- exchange formats  
- interoperability  

Persistence occurs through volumetric readout → digital encoding → storage.

---

## 5.9 Summary

Memory is:

- volumetric  
- wavelength-organized  
- in-place  
- unified with compute  
- massively parallel  

There are no classical memory devices.
