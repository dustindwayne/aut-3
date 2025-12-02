# 10. AI Relevance and Use Cases — AUT-3

## 10.1 AI Workloads and AUT-3

AI workloads often involve:

- Large tensors (weights, activations).
- Continuous-valued operations.
- Iterative refinement.
- High parallelism.

AUT-3 is well aligned with these characteristics:

- It operates on volumetric continuous state.
- It can implement large, parallel transformations with a single optical field.
- It can keep model parameters and working state in the same physical volume, avoiding data transfer bottlenecks.

## 10.2 Example Use Cases

### 10.2.1 Deep Learning Inference

- Store model weights in long-term channels.
- Store activations in working-memory channels.
- Use compute operations to implement approximate matrix multiplications, convolutions, and nonlinearities.

### 10.2.2 Generative Models and World Models

- Represent world states as volumetric fields.
- Evolve states using optical compute steps.
- Maintain histories and latent representations in long-term regions.

### 10.2.3 Associative and Content-Addressable Memory

- Encode patterns into volumetric state.
- Use optical fields to retrieve or complete patterns based on partial cues.
- Implement continuous attractor-like behavior using the medium’s dynamics.

## 10.3 Hybrid Systems

AUT-3 can be combined with digital systems:

- Use AUT-3 for high-dimensional, approximate compute.
- Use digital processors for control flow, exact arithmetic, and interfaces.
- Exchange tensors at key points in computations.

This hybrid model allows systems to benefit from AUT-3’s volumetric merits while retaining precise digital control where necessary.

## 10.4 Research Directions

Research areas enabled or accelerated by AUT-3 include:

- New training methods for analog, volumetric compute fabrics.
- Representations that naturally exploit three-dimensional state.
- Algorithms that balance localized and global optical interactions.
- Long-term stability and calibration techniques for photonic compute–memory systems.
