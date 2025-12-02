# 3. State Model — AUT-3

## 3.1 Voxel Grid

The volumetric medium in each cube is abstracted as a **voxel grid**:

- Dimensions: `Nx × Ny × Nz`
- Voxel coordinates: `(x, y, z)` with integer indices
- Physical resolution (voxel size) is implementation-defined.

The voxel grid is a conceptual discretization used to model and control the system. The underlying physical medium may be continuous, but control and reconstruction operate at voxel granularity.

## 3.2 Voxel State Vector

Each voxel has an associated **state vector**:

- `S(x, y, z) ∈ ℝ^K`

where:

- `K` is the number of state components per voxel.
- Components represent optical properties or derived quantities, for example:
  - Absorption at specific wavelengths.
  - Phase delay.
  - Refractive index changes.
  - Fluorescence intensity in specific bands.
  - Aggregated or filtered responses.

AUT-3 does not require a specific `K`. Implementers choose `K` large enough to represent the necessary information for compute and memory roles.

## 3.3 Functional Channels

State vector components are grouped into **functional channels**:

- **Storage channel(s)**:
  - Components with high stability and long retention.
- **RAM channel(s)**:
  - Components with faster write and higher endurance but moderate retention.
- **Cache / compute channel(s)**:
  - Components with the fastest dynamics, suitable for transient computation.

For example:

- `S = [S_store, S_ram, S_cache]`
- Each sub-vector may itself be multidimensional.

The mapping between state components and roles is implementation-defined but must be documented in any concrete AUT-3 system.

## 3.4 State Evolution

State evolution is driven by:

- **Write operations**:
  - Intentionally modify state components via controlled illumination.
- **Compute operations**:
  - Use optical fields to transform subsets of the state, possibly in-place.
- **Natural drift and relaxation**:
  - Material-specific processes that slowly change state in the absence of input.

The architecture assumes:

- There exists a characteristic timescale for drift in each channel.
- Control systems can refresh or correct state fast enough to maintain desired behavior.

## 3.5 Observability

State is observed indirectly via optical readout:

- Probe fields pass through or interact with the volume.
- Sensors capture resulting intensities or phases.
- Reconstruction algorithms map sensor data back to an estimate of `S(x, y, z)`.

The reconstructed state is an approximation of the physical state, subject to:

- Sensor noise.
- Model error.
- Resolution limits.

AUT-3 requires that:

- Reconstruction accuracy is sufficient for the intended compute and memory roles.
- Error bounds can be characterized and accounted for at higher levels.

## 3.6 Logical Addressing

Logical addressing in AUT-3 refers to:

- Mapping higher-level data structures (tensors, graphs, fields) onto the voxel grid and state vectors.
- Managing placement decisions such as:
  - Which regions of the grid store long-term data.
  - Which regions serve as working buffers.
  - Which regions participate in compute operations.

The architecture does not fix a single logical addressing scheme. However, it assumes that:

- Logical structures can be mapped to voxel subsets.
- The mapping can be tracked and updated as the system reuses and restructures space.
