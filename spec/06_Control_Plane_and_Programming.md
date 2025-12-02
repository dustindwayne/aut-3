# 6. Control Plane and Programming Model — AUT-3

## 6.1 Control Responsibilities

The control plane coordinates:

- Emitter configuration
- Compute-field scheduling
- Tomographic readout
- Node-to-node communication
- Thermal and wavelength stability

## 6.2 Closed-Loop Wavelength Locking (Thermal Drift Compensation)

AUT-3 operates under conditions where:

- Optical power
- Local heating
- Refractive-index changes

can cause **spectral drift** in the medium.

To maintain deterministic addressing, AUT-3 uses **Closed-Loop Wavelength Locking**, defined as:

1. Sensors detect **local refractive index drift** via probe measurements.  
   (Example: storage channel absorption peak shifts from 1310 nm → 1312 nm)
2. Firmware computes the offset:  
   `Δλ = λ_actual - λ_nominal`
3. Emitters dynamically retune their wavelength by the same Δλ.  
   Example:  
   - Medium drifts **+2 nm**  
   - Laser retunes **+2 nm**
4. Operation continues without thermal failure or logical corruption.

This replaces aggressive cooling with **active wavelength tracking**, maintaining channel integrity during compute and write operations.

## 6.3 Operation Description

Each instruction describes:

- Region
- Channel mask (via DWDM)
- Field configuration
- Exposure duration
- Readout mode

## 6.4 Programming Abstractions

Can be exposed as tensor ops, field ops, or graph-based scheduling.

## 6.5 Synchronization and Consistency

Control firmware ensures non-overlapping writes and ordered reads.

## 6.6 Integration With Digital Systems

The node exposes queues for commands, results, and health metrics including **wavelength drift state**.

