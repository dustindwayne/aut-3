# 2. Physical Architecture — AUT-3

## 2.1 Cube Node

An AUT-3 cube node consists of:

- A **volumetric medium** with dimensions on the order of millimeters to centimeters.
- One or more **write planes**:
  - Planar arrays of emitters (e.g., micro-lasers or micro-LEDs).
  - Emit structured illumination patterns into the volume.
- One or more **read planes**:
  - Composed of a probe laser and a sensor array.
  - Acquire data sufficient to reconstruct the internal state.
- Local electronics:
  - Drive emitters.
  - Control probe beams.
  - Capture sensor data.
  - Interface with external controllers or a mesh network.

The geometry is intentionally simple: a block of material with orthogonally mounted optical subsystems.

## 2.2 Write Plane

The write plane is a 2D array of emitters aligned with one face of the cube:

- Resolution: application-dependent (e.g., 256×256, 512×512, or higher).
- Emission: one or more wavelengths, individually addressable per emitter.
- Function: imprint optical patterns into the volume by:
  - directly modifying voxel state (e.g., through photochemical or phase-change mechanisms), or
  - injecting fields that participate in a compute step.

Depth targeting can be achieved by:

- Focusing (adjusting the optical focus depth).
- Nonlinear absorption (multi-photon processes).
- Wavelength-dependent absorption in stratified or graded media.

## 2.3 Read Plane

The read plane is a combination of:

- A probe laser or structured illumination source.
- A sensor array viewing the volume through one face.
- Optional scanning or multiplexing optics.

The read system provides **projection data** of the internal volume:

- Different angles, wavelengths, or time gates can be used.
- Tomographic or related reconstruction methods convert projection data into a 3D field of voxel-level observables.

Read operations are designed to be:

- Low-disturbance with respect to stored state.
- Repeatable and calibratable.
- Sufficiently fast for target workloads.

## 2.4 Multi-Wavelength and Multi-Direction Access

Physical access is not limited to a single wavelength or face:

- Multiple emitter arrays or probe systems can be placed on different faces (e.g., X, Y, Z directions).
- Different wavelengths can be used for different functional roles:
  - One band optimized for long-term storage writes.
  - Another for high-speed, high-endurance updates.
  - Another for non-persistent compute fields.

This enables channel separation without requiring that a single material respond identically at all wavelengths.

## 2.5 Internal Stratification (Optional)

The medium can be **stratified** in the depth (Z) direction:

- Lower region: material optimized for stable storage.
- Mid region: material optimized for mid-term, high-cycle state (RAM-like).
- Upper region: material optimized for fast interaction and compute (cache-like or compute slab).

Interfaces between regions are optically engineered to minimize reflections and distortions.

Stratification is not required by the architecture, but it is supported as a practical way to give different regions different behavior.

## 2.6 Node Form Factor and Interfaces

Each cube node presents:

- Mechanical mounting points.
- Power input.
- High-bandwidth data and control links.

Node interfaces are kept generic in the architecture. Implementations may use:

- Electrical links (e.g., high-speed serial).
- Optical fiber links.
- Backplane-style connectors.

The architecture only requires that:

- External controllers can configure and coordinate the node.
- Nodes in a mesh can exchange control and data messages with acceptable latency and bandwidth.
