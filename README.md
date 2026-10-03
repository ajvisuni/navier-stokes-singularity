# Navier-Stokes Finite-Time Singularity Visualizer

Interactive WebGL/Three.js illustrative visualization inspired by the finite-time blowup construction for the 3D incompressible Navier-Stokes equations. Loosely based on the similarity scaling in [*Finite Time Blowup for Navier-Stokes*](https://cdn.openai.com/pdf/32d9f210-8b73-45e0-91bc-82a30aef8a9a/navier-stokes.pdf) (OpenAI).

## Mathematical Overview

The visualization illustrates the idea of finite-time blowup ($\Vert{}u(t)\Vert{}_{L^\infty} \to \infty$ as $t \uparrow 1$) by structuring a self-similar core surrounded by an oscillatory momentum-flux transfer annulus. The paper proves blowup with bounded kinetic energy; this demo does not compute or verify energy.

### Similarity Scaling Implemented
- **Remaining Time Parameter:** $\tau = 1 - t$
- **Concentration Scale:** $q(z, \tau) \approx \tau + \vert{}z\vert{}^{1/D}$
- **Scaling Exponents:** With $h = 0.08$:
  - Tangential Velocity: $A = 1/2 + h = 0.58$
  - Axial Jet Scale: $D = 1/2 - h = 0.42$

## Implementation Details
- **Rendering Pipeline:** 90,000 particles rendered via Three.js `BufferGeometry` and custom GLSL vertex/fragment shaders. Particle positions are updated on the CPU each frame.
- **Dynamic Color Mapping:** Real-time velocity magnitude mapping to a piecewise-linear approximation of the Inferno colormap inside GLSL.
- **Adaptive Time Progression:** The global time advance scales with $\tau^{1/2}$ to slow the animation as $\tau \to 0$. The particle step itself is fixed.

> **Unofficial project, not affiliated with or endorsed by OpenAI.**
>
> The velocity field here is a hand-built kinematic surrogate that mimics the paper's scaling. It is **not** the paper's solution and **not** a Navier-Stokes solver, and it is not verified to be divergence-free. The paper's result concerns the **forced** equations (smooth, compactly supported force, starting from rest ); this visualization/demo has no force term. The paper is very recent and still is being checked by the community at this time. For a more readable account of the profile construction, see [Lei & Ren, arXiv:2609.35406](https://arxiv.org/abs/2609.35406).
