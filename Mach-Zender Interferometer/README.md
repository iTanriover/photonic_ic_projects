# Mach–Zehnder Interferometer Design
Design and simulation of passive silicon-photonic Mach–Zehnder interferometers (MZIs) using Lumerical and MATLAB.

We designed MZIs using the 50/50  [directional coupler](https://chat.asksage.anl.gov/PROJECT_SUMMARY.md) that is designed on the previous project, for beam splitting and guiding 
The target FSR and delta_phi was achieved through automated parameter sweepsThe project investigates how arm-length imbalance and common arm length affect the spectral response, finesse, and power splitting of an MZI. The final design was tuned to achieve approximately 50/50 output splitting at 1550 nm.

### Final Design Targets
| Parameter | Value |
|---|---|
| Platform | Si |
| Waveguide width | 450 nm |
| Waveguide thickness | 220 nm |
| Target wavelength | 1550 nm |
| Input splitter | Directional Coupler |
| Output combiner | Directional Coupler|
| Short-arm length | [Insert value] |
| Long-arm length | [Insert value] |
| Arm-length imbalance | [Insert value] |
| Final splitting ratio | [Insert value] |
| FSR | [Insert value] |
| Finesse | [Insert value] |
## Main results

The arm-length imbalance controls the wavelength-dependent phase difference:

$$
\Delta\phi(\lambda) = \frac{2\pi n_{\mathrm{eff}}\Delta L}{\lambda}
$$

where $\Delta L$ is the arm-length difference.

The final design was selected by fine-tuning the arm imbalance until the desired splitting ratio was obtained near 1550 nm.

## Detailed project summary

See the full analysis in:

[Project summary](https://chat.asksage.anl.gov/PROJECT_SUMMARY.md)

## Repository contents

- `READ_ME.md` — short project overview
- `PROJECT_SUMMARY.md` — detailed design summary
- `figures/` — MZI layouts, field plots, and simulation results
- `scripts/` — Lumerical and MATLAB scripts
- `data/` — processed simulation data
- `layout/` — layout or GDS files, if available

## Tools

- Ansys Lumerical
- MATLAB
- KLayout, if used for layout inspection
