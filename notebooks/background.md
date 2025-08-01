# Background
Beside inspiration from the aforementioned [Pain Points](./introduction.md#pain-points) found via literature review, we propose practices based on lessons learned from several of our own software projects.

## 6DOF Trajectory Simulator
This was a typical “one-person team” scenario where the developer was the domain
expert.
Being a high-precision ballistic computer to simulate spinning projectiles in a 3D space, this MATLAB program enabled previous research by the author at Embry-Riddle Aeronautical University (ERAU) {cite}`Du2021`.

The main challenge faced in this project was the lack of existing resources to test against for the complex 6DOF trajectory model.
This was successfully mitigated by conducting tests with simpler models under a standardized interface to validate the software.
However, since it was developed in an ad-hoc manner, with little traceable requirements or design documents, adaption of the software for future works by other researchers was hindered, and often required direct communication with the original author.

## SynthEddy
This was a recent project under the "developer & domain expert collaboration" setting, where the author served as the developer.
[SynthEddy](https://github.com/omltcat/turbulent-flow) {cite}`SynthEddy` is a Python program to generate turbulent flow fields consisting of numerous "eddies" (circular flow) with the Synthetic Eddy Method {cite}`PolettoEtAl2013`, to be used as initial conditions (IC) and boundary conditions (BC) for computational fluid dynamics (CFD) simulations.

SynthEddy was developed in a document-driven process, with high traceability of theory, requirements, design, and implementation, leading to easy expansion of the software.
However, it did face a major setback and subsequent redesign because the developer was unaware of the typical use case of the software.
The initial, fully information-hiding modular design (as in {cite}`Parnas1986`) to mimic the physical system was too slow and resource-intensive for the computation scale (in terms of mesh resolution and number of eddies) needed in the domain in practice. 
Our framework aims to avoid the problem of such communication breakdown between the developer and the domain expert.

## Current Practices
The inspiration and jumping off point for this framework is the document-driven template by {cite}`SmithEtAl2024`, which itself is based on the work by {cite}`Parnas1986`.
This previous template offers strong traceability through formal documentation, and is inline with our expectation that the software contributing to a research study should be able to withstand the same level of scrutiny.
However, its somewhat rigid structure made it hard to adapt to the changing nature of research, and introduced too much overhead, taking away valuable time from both the developer and the domain expert.
