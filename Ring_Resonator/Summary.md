# Silicon Photonic Microring Resonator Design

## 1. Project Overview

This project demonstrates the design and simulation of a passive silicon-photonic microring/racetrack resonator near 1550 nm.

The design targets a resonance wavelength of 1550 nm and a free spectral range (FSR) of approximately 20 nm. The group index calculated during the previous MZI project was used to estimate the resonator radius.

The resonator was first analyzed using varFDTD and then validated using full FDTD simulations. Coupling-length and radius subsequently altered to control the loaded quality factor, resonance wavelength, and FSR.

## 2. Design Platform and Targets

| Parameter                | Target             |
| ------------------------ | ------------------ |
| **Platform**             | Silicon photonics  |
| **Silicon thickness**    | 220 nm             |
| **Waveguide width**      | 450 nm             |
| **Nominal bus–ring gap** | 150 nm             |
| **Target wavelength**    | 1550 nm            |
| **Target FSR**           | 20 nm              |
| **Target loaded Q**      | Approximately 1500 |
| **Group index**          | 4.336     |

<!--The resonator uses a bus waveguide coupled to a racetrack resonator.

| Parameter                   | Value            |
| --------------------------- | ---------------- |
| **Resonator type**          | Racetrack |
| **Radius**                  | 4.4 $\mu m$   |
| **Coupling length**         | 0.9  $\mu m$  |
| **Coupling gap**            | 150 nm           |-->

## 3. Design Methodology

The group index obtained from the previous MZI design was used to estimate the resonator size.

For a resonator with round-trip length $(L_{\mathrm{rt}})$, the FSR is approximately:

```math
\mathrm{FSR} \approx \frac{\lambda_0^2}{n_g L_{\mathrm{rt}}}
```

For an ideal circular ring:

```math
L_{\mathrm{rt}} = 2\pi R
```

For a racetrack resonator:

```math
L_{\mathrm{rt}} = 2\pi R + 2L_s
```

where:

* $(R)$ is the bend radius
* $(L_s)$ is the length of one straight section
* $(n_g)$ is the group index
* $(\lambda_0)$ is the design wavelength

The initial radius was calculated from the target FSR and then rounded to the available geometric precision. This rounding introduced a small difference between the analytical target and the simulated result.

## 4. Initial varFDTD Simulation

The initial ring structure was simulated using varFDTD to evaluate the approximate transmission response and identify the resonance behavior.

![Initial resonator transmission](figures/initial_varfdtd_transmission.jpg)

The varFDTD simulation was used to provide an efficient first estimate before full FDTD validation.

The main quantities extracted were:

* Resonance wavelength
* Free spectral range
* Resonance linewidth
* Through-port transmission
* Approximate loaded quality factor

## 5. Initial FDTD Validation

The resonator was validated using full FDTD simulation.

The initial FDTD result produced:

| Parameter                | Result                |
| ------------------------ | --------------------- |
| **Resonance wavelength** | Approximately 1552 nm |
| **FWHM linewidth**       | Approximately 0.4 nm  |
| **Loaded Q**             | Approximately 3900    |
| **FSR**                  | Approximately 21 nm   |

The loaded quality factor was calculated from the resonance wavelength and full-width-at-half-maximum linewidth:

```math
Q_{\mathrm{loaded}} = \frac{\lambda_{\mathrm{res}}}{\Delta\lambda_{\mathrm{FWHM}}}
```

Using the approximate values:

```math
Q_{\mathrm{loaded}} \approx \frac{1552\ \mathrm{nm}}{0.4\ \mathrm{nm}} \approx 3900
```

![Initial FDTD transmission](figures/initial_fdtd_transmission.jpg)

The simulated resonance and FSR are close to the design targets. The small deviations are attributed to:

* Rounding of the calculated radius
* Discrete geometric dimensions
* Numerical mesh resolution
* Approximation in the group-index-based design
* Differences between the ideal analytical model and the complete curved geometry

## 6. Coupling-Length Comparison

Following, three racetrack resonators were simulated using varFDTD using coupling lengths of:

```math
L_c = 1,\ 2,\ \mathrm{and}\ 6.4\ \mu\mathrm{m}
```

The value of (6.4\ \mu\mathrm{m}) corresponds to the approximate 50/50 coupling length obtained previously for a 150 nm gap on the same waveguide platform.

![Coupling-length comparison](figures/coupling_length_comparison.jpg)

The coupling length controls the strength of interaction between the bus waveguide and the resonator, enabling controlling Q factor.

In general:

* Shorter coupling length produces stronger coupling.
* Stronger coupling generally reduces the loaded Q.
* Longer coupling length produces weaker coupling and higher Q.

## 7. Final Design

The final design was selected by jointly considering: Resonance wavelength, FSR, and Loaded Q.

The FSR and resonance wavelength is determined by resonator round-trip length $(L_{\mathrm{rt}})$. To control Q factor, we varied the coupling length

| Parameter                 | Final result          |
| ------------------------- | --------------------- |
| **Resonance wavelength**  | Approximately 1550 nm |
| **FSR**                   | Approximately 20 nm   |
| **Loaded Q**              | Approximately 1500    |
| **FWHM linewidth**        | 1 nm       |
| **Ring/racetrack radius** | 4.4 $\mu m$        |
| **Coupling length**       | 0.9     $\mu m$    |
| **Coupling gap**          | 150 nm                |

The expected linewidth for a resonance near 1550 nm and loaded Q of approximately 1500 is:

```math
\Delta\lambda_{\mathrm{FWHM}} \approx \frac{1550\ \mathrm{nm}}{1500} \approx 1.03\ \mathrm{nm}
```
Transmission from the through port is shown below.
![Final resonator transmission](figures/final_resonator_transmission.jpg)

## 8. Near-Resonance Field Distribution

The electric-field distribution was plotted at a wavelength close to resonance to visualize coupling into the ring and circulating field enhancement.

![Near-resonance field distribution](figures/resonator_field_map.jpg)

The field map illustrates:

* Input-bus propagation
* Coupling from the bus into the resonator
* Field circulation within the ring
* Resonant enhancement near the selected wavelength
* Output transmission through the bus waveguide

## 9. Conclusions

A passive silicon-photonic microring/racetrack resonator was designed for operation near 1550 nm with a target FSR of approximately 20 nm.

The design workflow demonstrated that:

* The resonator length primarily controls the FSR.
* Coupling length strongly controls the loaded Q and resonance linewidth.
* The initial FDTD design produced a resonance near 1552 nm, a linewidth of approximately 0.4 nm, a loaded Q of approximately 3900, and an FSR of approximately 21 nm.
* Differences between analytical estimates and full-wave results arise from geometric rounding, numerical resolution, and the detailed resonator geometry.
