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
| **Platform**                   | [Insert platform] |
| **Waveguide width**            | [Insert value]    |
| **Waveguide thickness**        | [Insert value]    |
| **Target wavelength**          | 1550 nm           |
| **Input splitter**             | [Insert type]     |
| **Output combiner**            | [Insert type]     |
| **Balanced-arm length**        | [Insert value]    |
| **Short-arm length**           | [Insert value]    |
| **Long-arm length**            | [Insert value]    |
| **Final arm-length imbalance** | [Insert value]    |

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
* Finesse without intentional arm imbalance

| Parameter                 | Value          |
| ------------------------- | -------------- |
| **Output 1 transmission** | [Insert value] |
| **Output 2 transmission** | [Insert value] |
| **Total transmission**    | [Insert value] |
| **Finesse**               | [Insert value] |
| **Excess loss**           | [Insert value] |

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

