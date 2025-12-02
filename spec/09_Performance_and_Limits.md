# 9. Performance and Limits — AUT-3

## 9.1 Performance Factors

Key factors influencing AUT-3 performance include:

- **Optical propagation**:
  - Light transit time across the volume (typically negligible relative to other factors).
- **Medium response**:
  - Time for state changes to occur in response to illumination.
- **Emitter and sensor bandwidth**:
  - Maximum pattern update rates and frame rates.
- **Reconstruction and control**:
  - Computational cost of reconstructing state from projections.
  - Time to configure optical fields and schedule operations.

## 9.2 Parallelism

AUT-3 naturally supports high parallelism:

- Write planes can address many voxels in parallel per operation.
- Read planes capture large regions per frame.
- Compute fields act on the entire illuminated volume or subvolume simultaneously.

Exposed parallelism is constrained by:

- Emitter and sensor array sizes.
- Interference and crosstalk considerations.
- Thermal and power limits.

## 9.3 Latency

Latency for a given operation combines:

- Configuration latency (setting up emitters/fields).
- Exposure or interaction time.
- Readout and reconstruction time (if applicable).
- Control latency (issuing commands and processing results).

Different workloads will emphasize different parts of this latency budget.

## 9.4 Throughput

Throughput is determined by:

- Number of independent operations per unit time.
- Volume of voxels affected per operation.
- Ability to overlap compute, write, and read operations.

AUT-3 is most effective when workloads are expressed as large, structured operations over regions, rather than fine-grained, random-access operations.

## 9.5 Scaling Limits

Scaling is limited by:

- Material properties (e.g., maximum useful thickness before losses dominate).
- Optical system complexity (focus, aberrations, alignment).
- Thermal management.
- Interconnect bandwidth between nodes.

Designers must balance:

- Cube size.
- Voxel resolution.
- Number of channels per voxel.
- Number of cubes in a mesh.

## 9.6 Approximation and Algorithm Design

Because AUT-3 is analog and volumetric:

- Algorithms should be designed to tolerate some approximation.
- Many AI and signal-processing workloads are compatible with this property.
- Bit-accurate workloads may need surrounding digital correction or alternative architectures.

The most suitable workloads are those where:

- Large, dense numerical structures are processed.
- Small errors do not invalidate overall results.
