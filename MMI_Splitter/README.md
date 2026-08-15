# Silicon Photonic 1×2 MMI Splitter

Design and simulation of a 1×2 multimode-interference (MMI) splitter using Ansys Lumerical MODE-EME solver.

The device uses a tapered single-mode input waveguide, a multimode interference region, and two tapered output waveguides. The design was optimized through mode-convergence, MMI-width, MMI-length, wavelength, and taper-width sweeps.

## Design Parameters

| Parameter | Value |
|---|---|
| **Platform** | Silicon photonics |
| **Silicon thickness** | 220 nm |
| **Nominal waveguide width** | 450 nm |
| **Background index** | 1.44 |
| **Target wavelength** | 1550 nm |
| **Initial MMI width** | 10 µm |
| **Initial MMI length** | 20 µm |
| **Optimized MMI width** | 4.5 µm |
| **Optimized MMI length** | 17.5 µm |
| **Optimized taper width** | 1.75 µm |

## Project Scope

- EME mode-convergence analysis
- MMI-width optimization
- MMI-length optimization
- Fine MMI-length sweep
- Wavelength-dependent transmission analysis
- Taper-width optimization
- Final electric-field visualization
- S-parameter extraction
- Preparation of an N-port S-parameter model for INTERCONNECT

## Main Result

The optimized design uses an MMI width of approximately 4.5 µm and an MMI length of approximately 17.5 µm.

## S-Parameter Model

The simulated port responses are being exported to text file and converted into an N-port S-parameter object for circuit-level simulation in INTERCONNECT.

The extracted model will enable:

- Broadband circuit-level simulation
- Integration with waveguides and other PIC components
- Evaluation of power splitting in a larger photonic circuit
- Comparison between component-level EME results and circuit-level behavior

## Detailed Project Summary

[View the detailed project summary](Summary.md)

## Repository Contents

- `README.md` — short project overview
- `Summary.md` — detailed design methodology and results
- `figures/` — sweep results, transmission plots, and field distributions
- `scripts/` — Lumerical scripts
- `s_parameter.txt` — exported S-parameter text file
- `interconnect/` — INTERCONNECT files and N-port model, if available

## Tools

- Ansys Lumerical MODE
- Ansys INTERCONNECT
- MATLAB
- MATLAB
- KLayout, if used for layout inspection
