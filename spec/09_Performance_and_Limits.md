# 9. Performance and Limits — AUT-3

Performance is defined by volumetric optical throughput, not clock rates or ALU
counts. AUT-3’s compute occurs across millions of voxels simultaneously through
femtosecond field interactions.

---

## 9.1 Compute Parallelism

Parallelism arises from:
- volumetric region-wide updates
- spectral channel independence
- massively parallel optical field propagation

All voxels in an illuminated region update in the same femtosecond window.

---

## 9.2 Bandwidth

There is no memory bandwidth in the classical sense because:
**data does not move.**

Bandwidth is defined by:
- pulse repetition rate
- tomography throughput
- optical field update frequency

---

## 9.3 Latency

Latency sources:
- pulse emission latency (femtosecond scale)
- reconstruction latency (read-side)
- digital control sequencing

Compute latency is near-constant regardless of region size.

---

## 9.4 Thermal Limits

AUT-3 avoids thermal meltdown through:
- <100 fs pulses
- low duty cycle
- passive cooling
- wavelength-locking stability

Thermal blooming is the primary limit but avoided through ultrafast compute.

---

## 9.5 Material Constraints

Performance is bounded by:
- nonlinearity coefficients
- absorption spectrum
- refractive index stability
- relaxation time

Material engineering determines ultimate throughput.

---

## 9.6 Reconstruction Limits

Tomographic readout requires:
- sufficient photodiode bandwidth
- correct sampling density
- accurate multi-angle projections

Higher spatial resolution requires more reconstruction bandwidth.

---

## 9.7 Scaling Limits

Mesh-scale limits include:
- optical interconnect speed
- wavelength-locking sync across nodes
- readout aggregation bandwidth

---

## 9.8 Summary

AUT-3 performance depends on:
- volumetric optical parallelism
- pulse rate
- material response
- DWDM stability
- tomography throughput

Its speed fundamentally exceeds electronic architectures due to in-place, parallel optical compute.
