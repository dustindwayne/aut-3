# Defensive Publication — AUT-3 Volumetric Photonic Compute–Memory Architecture

**Inventor:** `github.com/dustindwayne`, also known as **Dustin W.**  
**Title:** AUT-3 — Volumetric Photonic Compute–Memory Architecture  
**Purpose:** Establish public prior art for the AUT-3 architecture to prevent exclusive patent claims on the combination of features described herein.

## 1. Field

This publication describes a computer architecture in which a three-dimensional optical medium serves simultaneously as:

- A memory medium, storing state as optical properties distributed in volume.
- A compute substrate, transforming that state when driven by controlled light fields.

The system replaces classical CPU/RAM/cache/storage separation with a unified volumetric compute–memory fabric.

## 2. Background

Conventional digital computers separate:

- Computation (CPU, GPU).
- Working memory (RAM, cache).
- Long-term storage (SSDs, HDDs, other non-volatile memory).

These components are connected by buses that introduce latency and bandwidth limitations. Optical and photonic computing research has explored:

- Photonic accelerators for specific numerical operations.
- Volumetric optical storage using holography or multi-photon recording.
- Photonic neural network implementations.

However, prior work typically treats:

- Memory and compute as separate devices.
- Volumetric optical storage as a storage-only medium.
- Photonic accelerators as peripherals attached to conventional memory hierarchies.

AUT-3 differs by defining an architecture where the **same volumetric medium** performs both compute and memory roles, under structured optical control.

## 3. Summary of the Invention

AUT-3 introduces a compute–memory architecture with the following characteristics:

1. **Volumetric state**: Information is stored as continuous multi-dimensional state vectors associated with voxels in a 3D medium.
2. **Write plane**: At least one 2D emitter array injects structured optical fields into the volume, enabling region-level or depth-selective writes and compute fields.
3. **Read plane**: At least one probe laser and sensor system reconstructs internal state from optical projections.
4. **Unified roles**: CPU-like compute, RAM-like working memory, cache-like transient state, and storage-like long-term memory are all realized as different roles of the same volumetric medium.
5. **Wavelength and direction multiplexing**: Different wavelengths and optical access directions can be used to assign distinct functional roles (e.g., storage, working memory, compute) to overlapping regions of the medium.
6. **State model**: Each voxel has a state vector with components assigned to different functional channels (e.g., long-term, working, transient).
7. **Compute model**: Computation is defined as sequences of optical field–medium interactions that transform voxel state in place.
8. **Mesh scaling**: Multiple cubes can be interconnected into a mesh, forming a larger compute–memory fabric.

This combination of features provides a concrete, physically grounded approach to volumetric photonic in-memory computing.

## 4. Detailed Description

A detailed description of the AUT-3 architecture, including:

- Physical architecture of cubes.
- Voxel state model.
- Compute and memory models.
- Control plane and programming interface.
- Node mesh and scaling behavior.
- Fault tolerance and performance considerations.

is provided in the accompanying AUT-3 specification documents in this repository (see `AUT3_Master_Specification.md` and the `spec/` directory).

These documents should be considered an integral part of this defensive publication. Together, they define a specific architecture and set of mechanisms for volumetric photonic compute–memory systems.

## 5. Scope of Prior Art

By publishing this description and the attached specification:

- The AUT-3 architecture, as defined by the combination of volumetric state storage, optical write and read planes, unified compute–memory roles, wavelength and direction multiplexing, and mesh scaling, is placed in the public domain as prior art.
- Any future patent claims that attempt to cover this combination, or obvious variations thereof, can be challenged on the basis of this prior disclosure.

This publication does not restrict others from implementing or extending AUT-3. It prevents exclusive control via patents over the described architectural combination.

## 6. Licensing Intent

The inventor intends that:

- AUT-3 be made available under an open hardware license, specifically the CERN-OHL-S-2.0 or a functionally similar strong copyleft license for hardware designs.
- Implementers are free to build, modify, and distribute AUT-3-based systems, provided they respect the chosen license terms and preserve openness of derivative designs.

Licensing files in this repository provide additional guidance.
