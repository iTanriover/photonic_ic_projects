# Silicon Photonic Edge Coupler Design

## 1. Project overview

This project demonstrates the design and simulation of a silicon-photonic edge coupler using a parabolic inverse taper.

The objective was to expand the mode of a silicon waveguide and improve its coupling to an SMF-28 optical fiber. The design was analyzed using the finite-difference eigenmode (FDE) solver and the eigenmode expansion (EME) solver in Lumerical MODE.

The initial study uses an oxide-cladded taper and omits the substrate. This simplified structure was selected to focus on the taper profile, modal overlap, and taper-length optimization.

## 2. Device geometry

The device consists of a silicon waveguide that tapers from a narrow facet tip to a wider single-mode waveguide.

| Parameter | Value |
|---|---:|
| Platform | Silicon photonics |
| Silicon thickness | 220 nm |
| Waveguide input width | 450 nm |
| Taper-tip width | 150 nm |
| Cladding | SiO₂ |
| Substrate | Omitted |
| Taper profile | Parabolic |
| Target wavelength | 1550 nm |

The taper width was defined by:

$$
w(z)=w_{\mathrm{tip}}+
\left(w_{\mathrm{wg}}-w_{\mathrm{tip}}\right)
\left(\frac{z}{L}\right)^2
$$

where:

- $$w(z)$$ is the waveguide width at position $$z$$
- $$w_{\mathrm{tip}}$$ is the facet-tip width
- $$w_{\mathrm{wg}}$$ is the input-waveguide width
- $$L$$ is the taper length

For this design:

$$
w_{\mathrm{tip}}=150\ \mathrm{nm}
$$

$$
w_{\mathrm{wg}}=450\ \mathrm{nm}
$$

The taper therefore expands from 150 nm at the facet to 450 nm at the input side.

## 3. Design objective

The design objective was to maximize coupling between the taper mode and the SMF-28 mode near 1550 nm.

The main design metrics were:

- Modal overlap
- Transmission through the taper
- Taper-length dependence
- Fiber-position sensitivity
- Equivalent insertion loss

The modal overlap was calculated using the normalized field-overlap expression:

$$
\eta=
\frac{
\left|
\iint
E_{\mathrm{fiber}}^*(x,y)
E_{\mathrm{taper}}(x,y)
\,dx\,dy
\right|^2
}{
\left(
\iint |E_{\mathrm{fiber}}(x,y)|^2\,dx\,dy
\right)
\left(
\iint |E_{\mathrm{taper}}(x,y)|^2\,dx\,dy
\right)
}
$$

where $$E_{\mathrm{fiber}}$$ and $$E_{\mathrm{taper}}$$ are the transverse electric-field profiles of the SMF-28 and taper modes.

## 4. FDE modal-overlap analysis

The FDE solver was used to calculate the modes of the oxide-cladded taper and the SMF-28 fiber.

The SMF-28 mode was positioned relative to the taper, and the modal overlap was calculated for different fiber positions.

![SMF-28 profile](figures/SMF_mode_profile.jpg)
![Taper Input profile](figures/150_mode_profile.jpg)

The calculated modal overlap was approximately 90%.

Because the taper geometry is symmetric, the optimum fiber position was found at the center of the taper. This is consistent with the symmetry of the mode profiles: lateral displacement from the center reduces the overlap with the taper mode.

| Metric | Result |
|---|---:|
| Target wavelength | 1550 nm |
| Fiber mode | SMF-28 |
| Taper-tip width | 150 nm |
| Taper input width | 450 nm |
| Modal overlap | Approximately 90% |
| Optimum fiber position | Centered on the taper |

The overlap result represents a mode-matching estimate. It does not include all propagation, radiation, reflection, and fabrication effects.

## 5. EME simulation

The EME solver was used to model propagation through the complete taper. This accounts for mode evolution along the taper and provides a transmission estimate for different taper lengths.

The taper-length sweep was performed from 0.3 mm to 2.1 mm. The initial sweep identified an optimum near 1.5 mm.

![Taper length versus transmission](figures/taper_length_sweep_coarse.jpg)

The taper length was then refined around the initial optimum by testing 1.35 mm and 1.65 mm.

![Taper length versus transmission](figures/taper_length_sweep_fine.jpg)


## 6. Final transmission and insertion loss

The final EME transmission was approximately:

$$
T\approx0.98.1
$$

The corresponding insertion loss was calculated as:

$$
\mathrm{IL}=-10\log_{10}(T)
$$

$$
\mathrm{IL}\approx0.083\ \mathrm{dB}
$$

The reported loss is the simulated transmission loss of the taper. It should not be interpreted as a complete packaged-fiber coupling loss because the current model does not include all practical coupling effects.

## 7. Fiber-position analysis

The fiber position was optimized using the FDE modal-overlap calculation.

Because the taper and oxide environment are symmetric, the maximum overlap occurs when the SMF-28 mode is centered on the taper.

The fiber-position optimization demonstrates that:

- Center alignment maximizes the modal overlap.
- Lateral displacement reduces the overlap.
- The optimum position is determined by the symmetry of the taper mode.

## 8. Simulation procedure

### 8.1 FDE setup

The FDE modal-overlap analysis was performed as follows:

1. Open a Lumerical MODE `.lms` file.
2. Run `set_FDE.lsf` to place the SMF-28 mode and taper geometry.
3. Run `overlap_analysis.lsf` to calculate the modal overlap.

### 8.2 EME setup

The EME model was created as follows:

1. Open the Lumerical MODE `.lms` file.
2. Run `set_FDE.lsf` if the geometry and FDE region require initialization.
3. Run `add_EME.lsf`.
4. Confirm that the EME region covers the complete taper.
5. Confirm that input and output power monitors are present.
6. Run the EME simulation using `eme propagate`.
7. Extract the transmitted power.

### 8.3 Taper-length sweep

The taper-length sweep was performed as follows:

1. Open a Lumerical MODE `.lms` file.
2. Open `taper_length_swp.lsf`.
3. Enter the desired taper-length range and step size.
4. Run the script.
5. Plot taper length against transmission.
6. Select the optimum taper length.
7. Perform a finer sweep around the optimum.

## 9. Design interpretation

The taper length controls how gradually the optical mode evolves from the narrow taper tip to the 450 nm waveguide.

A short taper can produce:

- Nonadiabatic mode conversion
- Radiation loss
- Higher-order-mode excitation
- Lower transmission

A sufficiently long taper provides more gradual mode evolution and generally improves transmission. However, increasing the taper length also increases:

- Device footprint
- Layout complexity
- Exposure to fabrication variation
- Potential accumulated propagation loss

The sweep therefore provides a practical compromise between transmission and device length.

## 10. Limitations

The current model is intended as a simplified edge-coupler demonstration. The following effects were omitted or simplified:

- Silicon substrate
- Full three-dimensional facet geometry
- Facet reflection
- Fiber tilt
- Vertical fiber displacement
- Lateral alignment tolerance beyond the analyzed position sweep
- Sidewall roughness
- Taper-tip fabrication variation
- Material absorption
- Broadband coupling performance
- Packaging-related effects

The reported approximately 90% modal overlap and approximately 98.1% EME transmission should therefore be treated as component-level simulation results under the stated assumptions.

## 11. Future work

Possible extensions include:

- Add the silicon substrate to the simulation.
- Perform full 3D FDTD validation.
- Sweep fiber lateral and vertical offsets.
- Include fiber tilt.
- Optimize taper-tip width.
- Compare linear and parabolic taper profiles.
- Evaluate broadband coupling from 1500 nm to 1600 nm.
- Include fabrication tolerances.
- Generate a fabrication-ready GDS layout.
- Calculate total fiber-to-chip coupling efficiency.

## 12. Final results

| Design quantity | Result |
|---|---:|
| Taper type | Parabolic inverse taper |
| Taper-tip width | 150 nm |
| Waveguide width | 450 nm |
| Silicon thickness | 220 nm |
| Cladding | SiO₂ |
| Substrate | Omitted |
| Target wavelength | 1550 nm |
| Modal overlap | Approximately 90% |
| Optimum fiber position | Centered |
| Taper-length sweep range | 0.3–2.1 mm |
| Final taper length | Approximately 1.45 mm |
| Final transmission | Approximately 98.1% |
| Equivalent insertion loss | Approximately 0.083 dB |

