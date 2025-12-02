# 3. State Model — AUT-3

## 3.1 Voxel Grid

The volumetric medium in each cube is abstracted as a voxel grid:

- Dimensions: `Nx × Ny × Nz`
- Coordinates `(x, y, z)` are integer indices
- Voxel size/resolution is implementation-dependent

The voxel grid is a conceptual representation; the underlying medium may be continuous, but control and reconstruction operate at voxel granularity.

## 3.2 Voxel State Vector

Each voxel has a state vector:

`S(x, y, z) ∈ ℝ^K`

Components correspond to optical properties such as:

- Absorption at specific wavelengths
- Phase delay
- Refractive index shift
- Fluorescence components
- Derived numerical features

The dimension `K` is chosen per implementation.

## 3.3 Functional Channels via Dense Wavelength Division Multiplexing (DWDM)

AUT-3 uses **Dense Wavelength Division Multiplexing (DWDM)** to assign stable functional roles to different spectral bands.  
This solves the classical occlusion problem in volumetric optical systems.

### **Spectral Role Allocation**

| Spectral Band | Function | Rationale |
|---------------|----------|-----------|
| **Red / Infrared (≈700–1600 nm)** | **Static Storage (OS, files, long-term layers)** | Long absorption lengths + low scattering → ideal for reaching deep layers without disturbing upper RAM or compute regions. |
| **Green / Visible (≈520–580 nm)** | **Active RAM (variables, working state)** | Stronger absorption + shorter penetration → ideal for mid-depth dynamic updates. |
| **Blue / UV (≈350–480 nm)** | **Compute / Logic (tensor weights, transient compute fields)** | High-energy, shallow-interaction band suited for fast transient computation. |

### **Occlusion Avoidance**

DWDM ensures that:

- **Storage-layer wavelengths (Red/IR)** pass *through* RAM and Compute regions because those layers do not significantly absorb in the Red/IR band.
- **RAM wavelengths (Green)** operate in a middle band that does not interfere with storage or compute channels.
- **Compute wavelengths (Blue/UV)** operate at shallow depth and do not disturb deep storage layers.

This allows **independent addressing of layered behaviors** without voxel shadowing or inter-layer signal blocking.

## 3.4 State Evolution

Voxel state evolves through:

- Write operations (DWDM-targeted updates)
- Compute-field interactions
- Natural drift and relaxation (material-dependent)

Firmware ensures refresh where required.

## 3.5 Observability

Probe lasers operate in a **non-conflicting wavelength band**, ensuring readout does not disturb stored DWDM channels.

## 3.6 Logical Addressing

Logical addressing maps structured data (fields, tensors) to voxel subsets.  
DWDM bands ensure channel separation independent of physical voxel adjacency.
