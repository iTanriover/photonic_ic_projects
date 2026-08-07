# Mach–Zehnder Interferometer Design

Design and simulation of passive silicon-photonic Mach–Zehnder interferometers (MZIs) using Ansys Lumerical and MATLAB.

The arm-length imbalance controls the wavelength-dependent phase difference:

$$
\Delta\phi(\lambda) = \frac{2\pi n_{\mathrm{eff}}\Delta L}{\lambda}
$$

where $\Delta L$ is the arm-length difference.

The MZIs were designed using the 50/50 [directional coupler](../directional_coupler/) previously designed for beam splitting and guiding. This project investigates how the arm-length imbalance and common arm length affect the spectral response, free spectral range (FSR), finesse, and output power splitting.

The target FSR and phase difference were achieved through automated parameter sweeps. The final design was tuned to achieve approximately 50/50 output splitting at 1550 nm.

## Final Design Targets

| Parameter             | Value               |
| --------------------- | ------------------- |
| Platform              | Si                  |
| Waveguide width       | 450 nm              |
| Waveguide thickness   | 220 nm              |
| Target wavelength     | 1550 nm             |
| Input splitter        | Directional Coupler |
| Output combiner       | Directional Coupler |
| Short-arm length      | [Insert value]      |
| Long-arm length       | [Insert value]      |
| Arm-length imbalance  | [Insert value]      |
| Final splitting ratio | [Insert value]      |
| FSR                   | [Insert value]      |
| Finesse               | [Insert value]      |

## Detailed Project Summary

See the full analysis in:

[Project summary](Summary.md)

## Repository Contents

* `README.md` — short project overview
* `PROJECT_SUMMARY.md` — detailed design summary
* `figures/` — MZI layouts, field plots, and simulation results
* `scripts/` — Lumerical and MATLAB scripts
* `data/` — processed simulation data
* `layout/` — layout or GDS files, if available

## Tools

* Ansys Lumerical
* MATLAB
* KLayout, if used for layout inspection
