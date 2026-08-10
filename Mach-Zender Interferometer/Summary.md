# Passive Mach–Zehnder Interferometer Design

## 1. Project Overview

This project investigates the design of a passive silicon-photonic Mach–Zehnder interferometer (MZI) with balanced and unbalanced arms.

The MZI consists of:

1. An input splitter
2. Two waveguide arms
3. An output combiner
4. Two output ports

The balanced-arm device was first analyzed as a reference. An arm-length imbalance was then introduced to create a wavelength-dependent phase difference and spectral response.

The design was progressively optimized using coarse, intermediate, and fine arm-imbalance sweeps. The final design was tuned to achieve approximately 50/50 splitting at 1550 nm.

## 2. Device Structure

The MZI uses two nominally identical splitter/combiner components connected by two waveguide arms.

| Parameter                      | Value             |
| ------------------------------ | ----------------- |
| **Platform**                   | SI                |
| **Waveguide width**            | 450 nm            |
| **Waveguide thickness**        | 220 nm            |
| **Target wavelength**          | 1550 nm           |
| **Input splitter**             |directional coupler|
| **Output combiner**            |directional coupler|
| **Balanced-arm length**        | 16 $\mu m$        |
| **Short-arm length**           | 20 $\mu m$        |
| **Long-arm length**            | 42.5 $\mu m$      |
| **Final arm-length imbalance** |  22.5 $\mu m$       |

## 3. Design Principle

The relative phase between the two arms is approximately:

$$
\Delta\phi(\lambda) =
\frac{2\pi n_{\mathrm{eff}}(\lambda)\Delta L}{\lambda}
$$

where:

* $n_{\mathrm{eff}}$ is the waveguide effective index
* $\Delta L$ is the arm-length difference
* $\lambda$ is the operating wavelength

For an ideal balanced splitter and combiner, the two output powers are complementary. A simplified model is:

$$
P_1(\lambda) =
\frac{1}{2}\left[1+\cos\left(\Delta\phi(\lambda)\right)\right]
$$

$$
P_2(\lambda) =
\frac{1}{2}\left[1-\cos\left(\Delta\phi(\lambda)\right)\right]
$$

The arm imbalance therefore determines the wavelength-dependent transfer between the two outputs.

## 4. Balanced-Arm Reference Design

The balanced-arm MZI was simulated first to establish a reference device with equal optical path lengths.

The balanced structure provides a reference for evaluating:

* Output-power balance
* Common-arm-length effects
* Splitter and combiner behavior
* Baseline transmission

| Parameter                 | Value          |
| ------------------------- | -------------- |
| **Output 1 transmission** | 0.00078        |
| **Output 2 transmission** | 0.9798         |
| **Total transmission**    | 0.98           |

## Group-Index and Arm-Length-Difference Design

The group index was calculated from the wavelength-dependent effective index of the fundamental TE-like waveguide mode:

$$n_g(\lambda) = n_{\mathrm{eff}}(\lambda) - \lambda \frac{d n_{\mathrm{eff}}}{d\lambda}$$


The effective index was obtained using the Lumerical FDE solver over the wavelength range of interest. The wavelength derivative was calculated using a central finite difference:


$$n_g(\lambda_0) \approx n_{\mathrm{eff}}(\lambda_0) - \lambda_0 \frac{n_{\mathrm{eff}}(\lambda_0+\Delta\lambda) - n_{\mathrm{eff}}(\lambda_0-\Delta\lambda)}{2\Delta\lambda}$$

The calculated group index at the design wavelength was:

| Parameter             | Value          |
| --------------------- | -------------- |
| **Design wavelength** | 1550 nm        |
| **Effective index**   | 2.3515         |
| **Group index**       | 4.3306         |
| **Wavelength step**   | 1 nm           |

For an unbalanced MZI, the free spectral range (FSR) is approximately:

$$\mathrm{FSR} \approx \frac{\lambda_0^2}{n_g\Delta L} $$

where:

* $\lambda_0$ is the design wavelength
* $n_g$ is the waveguide group index
* $\Delta L$ is the arm-length difference

The required arm-length difference for a target FSR was calculated using:  

$\Delta L \approx \frac{\lambda_0^2}{n_g,\mathrm{FSR}}$

Using:

* $\lambda_0 = 1550$ nm
* $n_g \approx 4.33$
* Target FSR = 25 nm

gives:

$\Delta L \approx \frac{(1550\ \mathrm{nm})^2} {(4.33)(25\ \mathrm{nm})} \approx 22.35\ \mu\mathrm{m}$

Yet, this calculation doesn't include the required phase difference $\Delta \phi$. Combining the phase shift - arm imbalance equation ($
\Delta\phi(\lambda) =
\frac{2\pi n_{\mathrm{eff}}(\lambda)\Delta L}{\lambda}
$) with the equation above gives  
<!--$$\Delta L =\left( (\floor \frac{\Delta \phi}{2\pi})*2\pi + \Delta \phi \right)\frac{\lambda}{2\pi n_{\mathrm{eff}}} $$  -->

$$\Delta L =\left(\mathrm{round}\left(\frac{\Delta\phi}{2\pi}\right)2\pi + \Delta\phi_{target} \right)\frac{\lambda}{2\pi n_{\mathrm{eff}}}$$  
where rounding is used for calculating the closest value that satisfy target FSR with zero phase difference.
Here, for 50/50 splitting ($\Delta\phi_{target} = \pi/2$) at 1550 nm an arm-length difference of approximately **22.5 $\mu m$** was selected as the initial design value for a target FSR of approximately **25 nm**.

The analytical arm-length difference was then refined using full-device simulations. The final response can differ from the analytical estimate because of:

* Wavelength-dependent effective and group indices
* Splitter and combiner imbalance
* Waveguide propagation loss
* Bend geometry
* Transition regions
* Numerical and geometric phase errors

The final arm-length difference was selected by sweeping the arm imbalance and fine-tuning the output splitting ratio at **1550 nm**.
<!--
## 5. Arm-Imbalance Sweep

An unbalanced MZI was created by increasing the length of one arm while keeping the other arm as the reference arm.

The arm imbalance was swept using:

* Large step sizes for the initial design space
* Smaller step sizes to identify the useful region
* Fine steps to tune the final splitting ratio at 1550 nm

### Large-Step Sweep

<!-- Insert figure here -->

* **x-axis:** arm length or arm-length imbalance
* **y-axis:** finesse

### Small-Step Sweep

<!-- Insert figure here -->

* **x-axis:** arm length or arm-length imbalance
* **y-axis:** finesse

These sweeps were used to identify the relationship between arm geometry and the spectral response.
-->
## 6. Fine Tuning at 1550 nm

The arm imbalance was fine-tuned to obtain the target splitting ratio at 1550 nm.

<!-- Insert figure here -->

* **x-axis:** arm length or arm-length imbalance
* **y-axis:** splitting ratio at 1550 nm

| Parameter                     | Value          |
| ----------------------------- | -------------- |
| **Target wavelength**         | 1550 nm        |
| **Target splitting ratio**    | [Insert value] |
| **Final arm imbalance**       | [Insert value] |
| **Simulated splitting ratio** | [Insert value] |
| **Final finesse**             | [Insert value] |

The final design was selected from the fine sweep based on the closest agreement with the target splitting ratio.

## 7. Effect of Constant Arm Length

The common arm length was varied while keeping the arm-length imbalance constant.

This separates the effects of:

* Absolute arm length
* Arm-length imbalance
* Optical phase difference
* Device footprint
* Propagation loss

<!-- Insert figure here -->

* **x-axis:** constant/common arm length
* **y-axis:** finesse

| Parameter              | Value          |
| ---------------------- | -------------- |
| **[Insert parameter]** | [Insert value] |
| **[Insert parameter]** | [Insert value] |
| **[Insert parameter]** | [Insert value] |

The results indicate whether the finesse is primarily controlled by the arm imbalance or is also affected by the total arm length.

## 8. Final Broadband Response

The final MZI design was simulated over the selected wavelength range.

<!-- Insert figure here -->

* **x-axis:** wavelength
* **y-axis:** transmission or normalized output power
* **Curves:** Output 1 and Output 2

The final response is summarized below:

| Parameter                            | Value          |
| ------------------------------------ | -------------- |
| **Wavelength range**                 | [Insert range] |
| **Target wavelength**                | 1550 nm        |
| **Output 1 transmission at 1550 nm** | [Insert value] |
| **Output 2 transmission at 1550 nm** | [Insert value] |
| **Splitting ratio at 1550 nm**       | [Insert value] |
| **FSR**                              | [Insert value] |
| **Finesse**                          | [Insert value] |
| **Maximum insertion loss**           | [Insert value] |
| **Output extinction ratio**          | [Insert value] |

## 9. Final Field Distribution

The electric-field distribution was examined at the target wavelength to confirm propagation through the splitter, arms, and combiner.

<!-- Insert figure here -->

* **Wavelength:** 1550 nm
* **Field component:** [Insert component, e.g., $E_y$]

The field plot shows interference between the two arms and the resulting power distribution at the output ports.

## 10. Final Design Summary

| Parameter                 | Value          |
| ------------------------- | -------------- |
| **Waveguide width**       | [Insert value] |
| **Waveguide thickness**   | [Insert value] |
| **Input splitter type**   | [Insert type]  |
| **Output combiner type**  | [Insert type]  |
| **Short-arm length**      | [Insert value] |
| **Long-arm length**       | [Insert value] |
| **Arm-length imbalance**  | [Insert value] |
| **Target wavelength**     | 1550 nm        |
| **Final splitting ratio** | [Insert value] |
| **FSR**                   | [Insert value] |
| **Finesse**               | [Insert value] |
| **Total transmission**    | [Insert value] |

## 11. Conclusions

A passive MZI was designed and analyzed using balanced and unbalanced arm configurations.

The main conclusions are:

* Balanced arms provide a reference response with no intentional path-length difference.
* Arm-length imbalance produces wavelength-dependent interference.
* Coarse-to-fine sweeps provide an efficient method for selecting the final arm imbalance.
* The common arm length can affect finesse, loss, and device footprint even when the imbalance remains constant.
* The final design was tuned to achieve approximately 50/50 splitting at 1550 nm.
* The broadband simulation confirms the wavelength-dependent response of the passive MZI.

## 12. Limitations and Next Steps

Possible extensions include:

* Including fabrication variations in waveguide width and arm length
* Modeling splitter and combiner imbalance
* Adding bend-loss and transition-loss analysis
* Performing Monte Carlo simulations of the full MZI
* Comparing circuit-level and full-FDTD results
* Generating a fabrication-ready GDS layout
* Evaluating thermal sensitivity and phase drift

---

**Ibrahim Tanriover**

