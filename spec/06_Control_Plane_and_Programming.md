# 6. Control Plane and Programming Model — AUT-3

## 6.1 Control Responsibilities

The control plane coordinates:

- Configuration of emitters and probe systems.
- Scheduling of compute and memory operations.
- Dataflow between AUT-3 cubes and any external digital systems.
- Monitoring of health and performance metrics.

Control logic can be split between:

- Local controllers on each cube (MCUs, FPGAs, ASICs).
- A higher-level host or supervisory processor.

## 6.2 Operation Description

An AUT-3 operation can be described minimally by:

- Target region(s) in the voxel grid.
- Target channel(s) in the state vector.
- Optical field configuration:
  - Emitter patterns.
  - Wavelength selection.
  - Intensity and timing.
- Readout specification (if any):
  - Which projections to acquire.
  - Whether to reconstruct state.
- Dependencies on previous operations.

At a low level, this can be encoded as an instruction-like structure understood by cube firmware.

## 6.3 Instruction-Level Interface (Conceptual)

A conceptual instruction format might include:

- `OP_TYPE` — write, compute, read, combined.
- `REGION` — coordinates of affected voxels.
- `CHANNEL_MASK` — which state components to act on.
- `FIELD_CONFIG` — identifier or parameters for optical field.
- `DURATION` — exposure time or number of cycles.
- `READ_FLAGS` — whether to capture projections and/or reconstruct.
- `SYNC_FLAGS` — dependency and ordering information.

The specification does not fix a concrete ISA. It defines the kinds of parameters needed for any AUT-3 instruction set.

## 6.4 Programming Abstractions

Higher-level programming models can expose AUT-3 as:

- A tensor/field compute device:
  - Operations describe nonlinear transforms over large tensors.
- An accelerator for specific workloads:
  - APIs designed around matrix multiplications, convolutions, or other kernels.
- A general-purpose compute fabric:
  - Graph-based models where nodes are operations and edges represent data dependencies.

In all cases, the compiler or runtime is responsible for:

- Mapping abstract operations to specific sequences of AUT-3 instructions.
- Choosing where in the volumetric medium to place data and temporary state.

## 6.5 Synchronization and Consistency

AUT-3 operations may:

- Run in parallel on different regions.
- Overlap in time if they do not conflict.

Control logic ensures:

- No two operations write to the same voxel state simultaneously.
- Reads observe consistent states as defined by the programming model.

For certain workloads, relaxed consistency models may be acceptable and can increase throughput.

## 6.6 Integration with Digital Systems

Digital systems interact with AUT-3 via:

- Configuration registers or command queues.
- DMA-like mechanisms for transferring input/output tensors.
- Status and event interfaces.

Practical implementations may expose AUT-3 as:

- A device on a high-speed bus (e.g., PCIe-like).
- A coherent accelerator in a shared memory fabric.
- A standalone system with a minimal control CPU used primarily for orchestration.
