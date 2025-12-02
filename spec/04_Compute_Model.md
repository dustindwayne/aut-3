# 4. Compute Model — AUT-3

## 4.1 Overview

In AUT-3, computation is defined as **controlled transformations of voxel state** driven by **optical fields**.

A single compute step can be expressed abstractly as:

- `S' = F(S, U)`

where:

- `S` is the current volumetric state.
- `U` describes one or more optical control fields (illumination patterns, wavelengths, timing).
- `S'` is the updated state.

Compute operations may:

- Transform state in-place.
- Use intermediate optical fields that are not themselves stored.
- Be applied to all voxels or restricted subregions.

## 4.2 Optical Fields as Operators

Emitters and compute beams define **optical fields**:

- Spatial distribution: intensity and phase over the volume.
- Spectral content: single or multiple wavelengths.
- Temporal profiles: pulse sequences, continuous waves, or modulated signals.

The medium responds according to its optical transfer function. Under linear and nonlinear optics, this can be approximated as:

- Linear propagation and scattering.
- Nonlinear absorption and refractive index changes.
- Phase accumulation.

At a given level of abstraction, a compute operation is modeled as applying a parameterized operator:

- `S' = Op_theta(S)`

where:

- `theta` encodes the configuration of emitters, beams, and timing.

## 4.3 Types of Compute Operations

Examples of compute operations include:

- **Local transforms**:
  - Apply per-voxel functions (e.g., thresholding, scaling) via targeted illumination.
- **Neighborhood operations**:
  - Use optical propagation to mix information between neighboring voxels.
- **Global transforms**:
  - Use interference and propagation to implement approximations of convolutions, correlations, or transforms over regions.

The architecture does not prescribe specific operations. It defines the general pattern:

1. Configure optical fields.
2. Apply fields to the current state for a defined duration.
3. Optionally read back the resulting state (full or partial).
4. Optionally repeat with new configurations.

## 4.4 Sequential and Parallel Composition

Compute operations can be composed:

- **Sequentially**:
  - Apply `Op1`, then `Op2`, etc.
- **In parallel**:
  - Different regions or channels can be driven concurrently if hardware permits.
  - Different wavelengths can interact with different channels simultaneously.

The control plane ensures that:

- Dependencies between operations are respected.
- Regions are not unintentionally overwritten by overlapping operations.

## 4.5 Conditional Behavior

Conditional computation is implemented by:

- Reading selected state components from sensors.
- Evaluating conditions in control electronics or higher-level controllers.
- Choosing subsequent optical operations based on those conditions.

At a higher abstraction level, this allows:

- Branching control flow.
- Early stopping in iterative algorithms.
- Data-dependent activation of specific compute patterns.

Conditionals operate at the control level. The underlying medium remains continuous and analog.

## 4.6 Precision and Approximation

AUT-3 is inherently analog:

- State components are continuous values.
- Optical transformations involve noise and approximation.

Higher-level algorithms must be expressed to tolerate:

- Limited precision.
- Reconstruction noise.
- Drift corrections.

Where needed, digital error-correction can be applied around AUT-3 operations, but the core compute fabric is modeled as continuous rather than bit-precise.
