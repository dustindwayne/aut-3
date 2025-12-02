# 7. Node Mesh and Scaling — AUT-3

## 7.1 Multi-Node Systems

Multiple AUT-3 cubes can be connected into a **node mesh**:

- Each node is functionally similar but may differ in capacity or material tuning.
- Nodes communicate over high-bandwidth interconnects.
- The mesh behaves as a unified compute–memory fabric from the perspective of higher-level software.

## 7.2 Topology

The architecture supports flexible topologies, including:

- 1D chains.
- 2D grids.
- 3D meshes.
- More general graphs.

The chosen topology should:

- Match physical layout constraints.
- Support required bandwidth and latency for the target workload.
- Provide redundancy paths where needed.

## 7.3 Addressing in the Mesh

Each node has:

- A unique Node ID.
- Optionally, a coordinate `(X, Y, Z)` representing its physical or logical position.

Global addressing is achieved by:

- Combining Node ID with local voxel coordinates.
- Managing higher-level logical address spaces across nodes.

## 7.4 Inter-Node Operations

Inter-node operations include:

- Moving or copying data between voxels on different nodes.
- Executing pipelines where the output of one node feeds into operations on another.
- Replication of state for redundancy.

To avoid excessive data movement:

- Designs should favor computations that act on data where it resides.
- Aggregation and reduction operations can be mapped to suitable nodes rather than shuttling full volumes.

## 7.5 Scaling Behavior

As nodes are added:

- Compute capacity increases roughly with total volume of active medium.
- Memory capacity increases with total volume and state-vector dimension.
- Interconnect requirements grow with the degree of coupling between nodes.

For tightly-coupled AI workloads, higher inter-node bandwidth is desirable. For more loosely coupled tasks, lower-bandwidth topologies may be acceptable.

## 7.6 Heterogeneous Nodes

The mesh can include heterogeneous nodes, for example:

- Nodes optimized for long-term storage.
- Nodes tuned for high-speed compute and transient state.
- Nodes specialized for particular wavelength ranges.

The architecture supports heterogeneity as long as:

- Nodes declare their capabilities.
- The control plane and runtime understand how to route work accordingly.
