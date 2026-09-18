Photonic Integrated Circuit Design Projects
This repository contains sample photonic-device designs and simulations developed using Ansys Lumerical MODE(FDE, EME)/FDTD/INTERCONNECT, MATLAB, and related photonic-design tools.
# Projects
## Directional Coupler
Design and analysis of a silicon-photonic directional coupler near 1550 nm, including:

Supermode analysis  
Gap and waveguide-width sweeps  
Coupling-length extraction  
Monte Carlo tolerance analysis  
Straight and bent-geometry FDTD validation  

See [Summary.md](directional_coupler/Summary.md).

## Mach-Zender Interferometer
Design and analysis of a silicon-photonic Mach-Zender Interferometer (MZI) near 1550 nm, including:

Balanced and unbalanced MZIs  
Group-index extraction  
Arm-length-difference design for a target free spectral range  
50/50 splitting optimization at 1550 nm  
Broadband transmission analysis.  

See [Summary.md](Mach-Zender_Interferometer/Summary.md).

## Multi Mode Interferometer
Design and analysis of a silicon-photonic 1x2 Multi Mode Interferometer (MMI) at 1550 nm, including:

EME mode-convergence analysis  
MMI-width optimization  
MMI-length optimization  
Fine MMI-length sweep  
Wavelength-dependent transmission analysis  
Taper-width optimization  
Final electric-field visualization  
S-parameter extraction  

See [Summary.md](MMI_Splitter/Summary.md).

## Micro Ring Resonator
Design and analysis of a silicon-photonic Micro Ring Resonator (MMR) at 1550 nm, including:

Group-index-based resonator initial design  
Ring and racetrack resonator simulations in varFDTD and FDTD   
Coupling-length analysis  
Resonance-wavelength, FSR, and Quality-factor targeted final design  

See [Summary.md](Ring_Resonator/Summary.md).

## Edge Coupler
Design and analysis of a silicon-photonic parabolic inverse-taper edge coupler at 1550 nm, including:

FDE modal-overlap analysis with an SMF-28 fiber  
Fiber-position optimization  
EME taper-length sweep  
Fine taper-length optimization  
Transmission and insertion-loss extraction  
Final electric-field visualization  
See [Summary.md](Edge_Coupler/SUMMARY.md).

## Optical Half-Band FIR Filter

INTERCONNECT circuit-level simulation of a three-MZI optical half-band finite-impulse-response (FIR) filter based on the lattice architecture reported by Jinguji and Oguma.  
The design was adapted to the silicon-photonic platform used in the previous component-design projects and updated for 1550 nm central wavelength and 25 nm FSR.
 
See [README.md](half_band_filter/README.md).
