# Wideband Vivaldi Antenna and Balun

A **2-6 GHz balanced tapered-slot Vivaldi antenna** and its associated **wideband balun/feed transition**, developed in CST Studio Suite for broadband RF reception, electronic-support experiments and phase-interferometry studies.

> **Project status:** the electromagnetic models and PCB manufacturing outputs are available. The numerical values below are simulation results. Physical prototype, VNA, gain and radiation-pattern measurements are still required before the design can be considered experimentally validated.

## Project Overview

The antenna is a PCB-based, balanced/differential Vivaldi structure intended for broadband directional operation between **2 GHz and 6 GHz**. Its natural feed reference is approximately **100 ohms differential**, so it should not be connected directly to a conventional 50-ohm single-ended SMA port without an appropriate transition.

The balun included in this repository is intended to provide the interface between a **50-ohm single-ended RF chain** and the antenna's **100-ohm balanced feed**. The antenna and balun are therefore published together as one integrated RF front-end project.

## Antenna Specifications

| Parameter | Value |
|---|---|
| Antenna type | Balanced tapered-slot Vivaldi antenna |
| Design band | 2-6 GHz |
| PCB dimensions | 155 mm x 215 mm |
| Aperture width | 122 mm |
| Substrate model | RO4350B-like RF laminate |
| Substrate thickness | 1.524 mm |
| Relative permittivity | 3.48 |
| Loss tangent | 0.0037 |
| Conductor model | Finite-conductivity copper, 5.8 x 10^7 S/m |
| Nominal feed | 100-ohm differential |
| Feed gap | 0.50 mm |
| Feed position | 18 mm from the PCB edge |
| Taper start | 36 mm |
| Elliptical cavity radii | Rx = 14 mm, Ry = 16 mm |

## Simulated Antenna Performance

The lossy-material CST model remains below the **-10 dB S11 criterion across the full 2-6 GHz band**, with simulated S11 values approximately between **-11.4 dB and -16.6 dB**.

| Frequency | Simulated directivity | Radiation efficiency | Total efficiency |
|---|---:|---:|---:|
| 2 GHz | 7.167 dBi | -0.1963 dB | -0.4882 dB |
| 4 GHz | 8.790 dBi | -0.2826 dB | -0.4329 dB |
| 6 GHz | 8.142 dBi | -0.3685 dB | -0.4711 dB |

The 4 GHz model shows the most balanced end-fire pattern. At 6 GHz, the antenna retains directional behavior while exhibiting more visible higher-order mode and side-lobe structure.

## Validation Studies Included

The antenna model was evaluated using:

- lossy copper and dielectric models;
- PEC comparison to confirm that the matching result is not caused only by material loss;
- open-boundary distances of 0.35, 0.50 and 0.80 wavelength;
- 50, 75 and 100-ohm port-reference studies;
- feed-gap tolerance of plus or minus 0.10 mm;
- substrate-permittivity tolerance of plus or minus 0.05;
- far-field monitors at 2, 4 and 6 GHz;
- a two-antenna coupling configuration.

## Two-Antenna Interferometry Configuration

A second CST configuration places two identical Vivaldi antennas **220 mm apart** for phase-interferometry and direction-finding studies.

In this simulation:

- both antenna ports remain below the -10 dB matching criterion across the operating band;
- simulated coupling, S21, remains approximately between **-58 dB and -80 dB**;
- the low modeled coupling supports the intended use of the pair for phase-difference experiments.

These values must still be verified on fabricated hardware because cables, baluns, connectors, mounting structures and the surrounding environment can change both amplitude and phase behavior.

## Balun and Feed Transition

The antenna requires a balanced feed. The supplied balun project is intended to:

- accept a 50-ohm single-ended RF input;
- generate two balanced outputs with approximately 180-degree phase difference;
- interface with the antenna's 100-ohm differential feed region;
- cover the same intended 2-6 GHz operating range.

The repository currently includes the CST model and Gerber package for the balun. Its insertion loss, amplitude balance, phase balance, return loss and common-mode suppression should be confirmed from the CST project and later measured using a calibrated VNA before final system integration.

## Repository Files

```text
wideband-vivaldi-antenna-balun/
├── README.md
├── Vivaldi.cst
├── Vivaldi.pdf
├── VivaldiGerber.zip
├── Balun.cst
└── BalunGerber.zip
```

### File descriptions

- `Vivaldi.cst` — CST electromagnetic model of the antenna.
- `Vivaldi.pdf` — Turkish simulation and validation report.
- `VivaldiGerber.zip` — PCB manufacturing outputs for the antenna.
- `Balun.cst` — CST model of the wideband balun/feed transition.
- `BalunGerber.zip` — PCB manufacturing outputs for the balun.

## Recommended Hardware Integration

```text
50-ohm SDR / RF receiver
          |
          v
2-6 GHz wideband balun
          |
          v
100-ohm balanced feed
          |
          v
Vivaldi antenna
```

Keep the two balanced traces or connections short, symmetric and mechanically identical. For dual-antenna phase measurements, use equal-length RF paths and characterize the complete receiver channels before estimating angle of arrival.

## Fabrication and Measurement Plan

Before final use:

1. Verify the Gerber stack-up and laminate with the PCB manufacturer.
2. Fabricate the Vivaldi antenna and balun using controlled RF materials and tolerances.
3. Measure balun S-parameters, amplitude balance and phase balance.
4. Measure antenna S11 with the complete balun and connector assembly.
5. Compare measured and simulated impedance behavior.
6. Measure radiation pattern, gain and front-to-back ratio.
7. For the antenna pair, calibrate cable and receiver-channel phase offsets.

## Author

**Cem Sondur**  
Electrical and Electronics Engineering  
RF, microwave, antenna and signal-processing design

## Rights and Use

Copyright (c) 2026 Cem Sondur. No open-source hardware licence has currently been granted. The files are shared for engineering review, education and experimental development without warranty. Independently verify the design before fabrication, transmission or safety-critical use.
