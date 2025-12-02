# 1. Architecture Overview — AUT-3

## 1.1 Purpose

AUT-3 defines a class of computing systems where:

- **State** is stored as optical properties distributed inside a **3D volume**.
- **Computation** occurs when controlled light fields propagate through that volume.
- **Readout** reconstructs the volumetric state using optical sensing.

The same physical volume acts as both **memory** and **compute substrate**. AUT-3 does not separate CPU, RAM, cache, and storage into distinct devices. These roles are implemented as **modes of interaction** with different regions and channels of the volumetric medium.

## 1.2 High-Level Concept

An AUT-3 cube is a node with:

- A volumetric medium whose internal voxels carry a continuous state vector.
- One or more **write planes** that inject structured optical fields.
- One or more **read planes** (laser + sensor) that reconstruct internal state.
- Local electronics that coordinate write, read, and control.

At the system level, nodes are connected into a mesh. The mesh exposes a single logical compute–memory fabric.

## 1.3 Comparison to Classical Architecture

Classical systems:

- CPU performs computation on registers.
- Cache and RAM store near-term state.
- Storage devices retain long-term state.
- Buses move data between these components.

Key differences in AUT-3:

- No separate CPU: the volume itself performs computation when driven optically.
- No separate RAM/cache/storage devices: regions and channels of the same medium behave as different tiers of memory.
- Data movement is minimized: operations are applied **in place**, without shuttling bits to a separate processor.

## 1.4 Design Goals

AUT-3 is designed with the following goals:

- **Unified substrate** for compute and memory.
- **Volumetric scaling**: capacity and compute scale with volume, not just area.
- **High parallelism**: many voxels updated or observed in a single optical operation.
- **Wavelength and direction multiplexing**: different roles (storage, RAM, cache, compute) can share the same space using different optical channels.
- **Modularity**: cubes can be combined into larger systems.
- **Material independence**: specification does not depend on a single medium; it defines requirements that multiple materials could satisfy.

## 1.5 Out of Scope

The AUT-3 specification does not:

- Prescribe a single chemical or physical medium.
- Define a software API or programming language.
- Guarantee specific performance numbers.
- Claim biological or cognitive properties.

It defines the **architecture**, state model, and interaction patterns that make volumetric photonic compute–memory systems feasible and analyzable.
