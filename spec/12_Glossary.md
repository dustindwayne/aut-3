# 12. Glossary — AUT-3

- **AUT-3**: A volumetric photonic compute–memory architecture in which a 3D optical medium serves as both state storage and compute substrate.
- **Voxel**: A volumetric element in the conceptual grid used to represent the medium’s internal state.
- **State vector**: The set of numerical values associated with a voxel, representing optical properties and derived quantities.
- **Write plane**: A 2D array of emitters used to inject optical patterns into the volume for writing and compute operations.
- **Read plane**: A system of probe illumination and sensors used to reconstruct the internal state of the volume.
- **Channel**: A subset of state vector components grouped by function (e.g., storage, working memory, transient compute).
- **Tier**: A memory behavior category (e.g., long-term storage, working memory, transient cache) defined by stability and performance properties.
- **Node**: An individual AUT-3 cube, including its medium, optics, electronics, and interfaces.
- **Mesh**: A multi-node arrangement where multiple AUT-3 cubes are interconnected.
- **Projection**: A 2D sensor measurement obtained by probing the volume with light from a particular direction and configuration.
- **Reconstruction**: The process of estimating voxel state from one or more projections.
- **Compute field**: An optical field intentionally configured to transform the volumetric state, rather than solely to write or read it.
