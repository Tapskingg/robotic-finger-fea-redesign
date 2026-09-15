# Tendon-Driven Robotic Finger — FEA Failure Investigation & Redesign

## Overview

This project documents a structural FEA investigation of a tendon-driven robotic finger developed for the YEAH robotic hand. https://www.pubinv.org/project/yeah-robotic-hand/

Physical prototypes showed repeated cracking in the rigid ABS structure near the exit of the flexible TPU tendon canal. The objective of the investigation was to reproduce the physical failure region in simulation, identify the underlying stress concentration, and implement a targeted geometry change without unnecessarily increasing the mass or changing the overall finger architecture.

The investigation was performed using **ANSYS Workbench / Mechanical**.

## Engineering Problem

The finger consists of:

- **ABS structure** — provides the rigid finger geometry and primary structural load path.
- **TPU tendon canal** — provides a compliant routing surface for the actuating tendon.

Physical testing showed that the TPU remained intact while cracking occurred in the surrounding ABS near the tendon-channel exit.

The working hypothesis was that the abrupt geometry and material transition caused the tendon reaction load to concentrate locally in the ABS.

## FEA Model

A Static Structural analysis was developed in ANSYS Mechanical.

### Model Setup

- Separate ABS and TPU bodies
- Bonded ABS–TPU interface
- Symmetry represented using a frictionless support on the cut plane
- Bottom ABS mounting interface fixed
- Local mesh refinement around the tendon exit and material transition
- Remote force applied to the TPU tendon-load face

### Comparison Load

A **72 N remote force** was used as a controlled baseline across the design iterations.

The supplied servo specification is **25 kg·cm (~2.45 N·m)**. Actual tendon tension additionally depends on the effective servo horn/spool radius, so the 72 N load is treated as a controlled comparative load rather than a final validated service load.

## Baseline Result

The baseline simulation reproduced a high-stress region corresponding to the observed physical failure location.

**Critical physical breakage-zone stress: approximately 38–49 MPa**

The stress concentration was localized around the ABS immediately adjacent to the TPU tendon-channel exit.

This indicated that the failure was primarily a **local load-path and stress-concentration problem**, rather than evidence that the entire finger required additional material.

## Design Modification

A **0.3 mm transition radius** was introduced at the critical ABS geometry beside the tendon-channel exit.

All major boundary conditions and the comparison load were retained to allow a direct baseline-versus-redesign comparison.

## Results

| Configuration | Stress in Physical Breakage Zone |
|---|---:|
| Baseline geometry | 38–49 MPa |
| 0.3 mm radius redesign | 18–24 MPa |

The targeted geometry modification produced an approximate:

**37–63% reduction in critical-zone stress**

The radius smooths the local load path and removes the original 38–49 MPa hotspot from the known physical failure region.

## Engineering Conclusion

**Recommended solution: implement the 0.3 mm radius at the ABS tendon-canal transition.**

The investigation demonstrates the complete engineering loop:

**Observed physical failure → FEA correlation → root-cause identification → geometry redesign → simulation verification → design recommendation**

## Tools & Methods

- ANSYS Workbench
- ANSYS Mechanical
- Static Structural FEA
- CAD preparation and geometry modification
- Contact definition
- Mesh refinement
- Boundary-condition definition
- von Mises stress analysis
- Failure correlation
- Design iteration

## Repository Contents

This repository contains:

- Engineering case-study presentation
- ANSYS Workbench simulation files
- FEA result images
- Baseline and redesigned geometry documentation

## Project Status

**Investigation complete.**

The 0.3 mm radius is recommended for implementation in the next physical prototype build.
