# 5. Memory Model — AUT-3

## 5.1 Unified Memory Concept

AUT-3 does not segregate memory into separate hardware units (registers, cache, RAM, storage). Instead, it defines **tiers** of memory behavior within the same volumetric medium:

- **Long-term storage**:
  - High stability, slow write.
- **Working memory (RAM-like)**:
  - Faster write, moderate stability.
- **Transient state (cache/compute)**:
  - Fast dynamics, low retention.

These behaviors can be achieved via:

- Different material regions.
- Different state components within each voxel.
- Different wavelength and illumination strategies.

## 5.2 Tiers and Regions

A concrete AUT-3 implementation may organize its volume as:

- Lower depth region:
  - Material tuned for long-term state, used for data that must persist.
- Mid-depth region:
  - Material optimized for working data, updated frequently.
- Upper region:
  - Material optimized for rapid state changes during compute operations.

Alternatively, tiers may be expressed within the state vector components of each voxel (e.g., separate storage and working channels).

## 5.3 Allocation and Placement

Higher-level software, in cooperation with firmware, handles:

- Mapping logical data structures to voxel regions and channels.
- Choosing where to place data based on:
  - Lifetime requirements.
  - Update frequency.
  - Access patterns.

Examples:

- Model parameters stored in long-term channels.
- Activations stored in working-memory channels.
- Temporary intermediates held in transient channels.

## 5.4 Persistence

Persistence policy is determined by channel and region:

- Long-term channels:
  - Designed to maintain state across power cycles, subject to material limits.
- Working-memory channels:
  - May be volatile or semi-volatile.
- Transient channels:
  - Intended for use during active compute; not relied on for long-term retention.

Implementations should document:

- Expected retention times.
- Recommended refresh policies.

## 5.5 Backup and Replication

In multi-node AUT-3 meshes, redundancy can be achieved by:

- Replicating critical long-term state across nodes.
- Using projection-based snapshots of volumetric state as backup artifacts.
- Distributed storage of snapshots and deltas in other nodes or external systems.

Backup and redundancy strategies belong at the system level. The architecture permits but does not mandate specific schemes.

## 5.6 Address Space

From the perspective of host systems:

- AUT-3 exposes an addressable logical space of tensors or fields.
- This space is backed by the volumetric state of one or more cubes.

The mapping from logical addresses to voxel regions is managed by:

- A memory manager aware of tier behavior.
- Firmware that enforces placement and access rules.

The architecture requires that:

- Logical data can be addressed and updated without exposing physical details to general-purpose software (unless desired).
