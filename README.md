# Navier-Stokes Finite-Time Singularity Visualizer

Interactive WebGL/Three.js research profiler modeling the finite-time blowup construction for the 3D incompressible Navier-Stokes equations. Based on the exact mathematical profiles from *Finite Time Blowup for Navier-Stokes* (OpenAI).

## Mathematical Overview

The visualization demonstrates finite-time blowup ($\Vert{}u(t)\Vert{}_{L^\infty} \to \infty$ as $t \uparrow 1$) with bounded kinetic energy by structuring a self-similar core surrounded by an oscillatory momentum-flux transfer annulus.

### Similarity Scaling Implemented
- **Remaining Time Parameter:** $\tau = 1 - t$
- **Concentration Scale:** $q(z, \tau) \approx \tau + \vert{}z\vert{}^{1/D}$
- **Scaling Exponents:** With $h = 0.08$:
  - Tangential Velocity: $A = 1/2 + h = 0.58$
  - Axial Jet Scale: $D = 1/2 - h = 0.42$

## Implementation Details
- **GPU Pipeline:** 90,000 advected particles rendered via Three.js `BufferGeometry` and custom GLSL vertex/fragment shaders.
- **Dynamic Color Mapping:** Real-time velocity magnitude mapping to an analytical Inferno colormap inside GLSL.
- **Adaptive Time-Stepping:** Dynamic time progression scaling with $\tau^{1/2}$ to resolve the high-shear dynamics as $\tau \to 0$.
