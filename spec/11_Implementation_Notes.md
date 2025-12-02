# 11. Implementation Notes — AUT-3

## 11.1 Candidate Media

Potential classes of media for AUT-3 include:

- Photochromic polymers and glasses.
- Phase-change materials (e.g., chalcogenides) in volumetric form.
- Photorefractive crystals.
- Doped sol–gel materials.
- Electro-optic or nonlinear optical polymers.

Selection criteria:

- Ability to change optical properties under illumination.
- Endurance and retention suitable for the intended memory tier.
- Compatibility with chosen wavelengths.
- Fabrication viability at required volumes and resolutions.

## 11.2 Optical Subsystems

Implementation choices for optical subsystems:

- Emitters:
  - Micro-LED arrays.
  - VCSEL arrays.
  - Other integrated photonic sources.
- Sensors:
  - CMOS or CCD arrays.
  - Integrated photonic detectors where applicable.
- Optics:
  - Simple lens systems where possible to reduce complexity.
  - Optional adaptive optics or diffractive elements for precise field shaping.

## 11.3 Control Electronics

Local control electronics may include:

- FPGAs or ASICs for timing-critical control of emitters and sensors.
- Embedded processors for calibration and management.
- High-speed serial links for interfacing with external hosts or other nodes.

## 11.4 Thermal Management

Photonic and material processes generate heat:

- Designs must include heat spreading and dissipation strategies.
- Thermal limits may constrain the maximum duty cycle of intensive operations.
- Thermal sensors and feedback can be used to adjust workloads dynamically.

## 11.5 Prototyping Considerations

Initial proof-of-concept systems can:

- Use lower-resolution voxel grids.
- Focus on demonstrating:
  - Reliable write and read cycles.
  - Simple compute operations over small regions.
- Use off-the-shelf components:
  - Laboratory lasers.
  - Standard optics.
  - Commercial image sensors.

Successive prototypes can:

- Increase resolution and volume.
- Integrate optics and electronics more tightly.
- Explore additional wavelengths and roles.
