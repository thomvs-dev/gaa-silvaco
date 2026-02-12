# Cylindrical GAA Nanowire p-MOSFET Simulation using Silvaco ATLAS

## Overview

This repository contains a **Silvaco ATLAS device simulation deck** for a **cylindrical Gate-All-Around (GAA) silicon nanowire p-MOSFET** with **sub-10 nm dimensions**, incorporating **quantum confinement** and **ballistic transport** effects using the **NEGF (Non-Equilibrium Green’s Function)** formalism.

The purpose of this deck is **educational and research-oriented**, demonstrating how advanced nanoscale transistor physics can be modeled beyond classical drift–diffusion, particularly for **technology nodes ≤ 5 nm**.

---

## Device Concept

At aggressively scaled dimensions, conventional planar MOSFET assumptions break down due to:

* Strong **quantum confinement** in the nanowire cross-section
* **Ballistic or quasi-ballistic carrier transport**
* Reduced electrostatic control in non-GAA structures

This simulation models a **cylindrical silicon nanowire** completely surrounded by a gate oxide and metal gate, providing **maximum electrostatic control** and minimal short-channel effects.

---

## Key Features of the Device

| Feature         | Description                                |
| --------------- | ------------------------------------------ |
| Device type     | p-MOSFET                                   |
| Architecture    | Cylindrical Gate-All-Around (GAA) nanowire |
| Transport model | NEGF (ballistic quantum transport)         |
| Channel         | Undoped (intrinsic)                        |
| Source/Drain    | Heavily p-doped                            |
| Gate control    | Work-function engineered metal gate        |

---

## Geometry and Dimensions

All dimensions are defined parametrically for clarity and scalability.

| Parameter           | Value  | Description               |
| ------------------- | ------ | ------------------------- |
| Nanowire radius     | 2 nm   | Silicon core radius       |
| Channel length      | 7 nm   | Electrostatic gate length |
| Oxide thickness     | 0.5 nm | Gate oxide (SiO₂)         |
| Source length       | 10 nm  | p⁺ source extension       |
| Drain length        | 10 nm  | p⁺ drain extension        |
| Total device length | 27 nm  | Source + Channel + Drain  |

The simulation uses **cylindrical coordinates**, which are physically appropriate for nanowire structures.

---

## Region Definition

### Region 1: Silicon Nanowire

* Material: Silicon
* Radius: 0 – 2 nm
* Length: 0 – 27 nm

### Region 2: Gate Oxide

* Material: SiO₂
* Radius: 2 – 2.5 nm
* Length: 0 – 27 nm

---

## Electrodes and Contacts

### Source and Drain

* Located at the ends of the nanowire (axial direction)
* Ohmic contacts to the silicon core
* p⁺ doped to 1×10²⁰ cm⁻³

### Gate

* Surrounds the channel region only
* Placed outside the oxide
* Work function: **4.8 eV** (suitable for p-MOS operation)

This configuration represents an **ideal GAA gate with no overlap capacitance**.

---

## Doping Strategy

The device uses a **junction-based architecture with an intrinsic channel**:

| Region  | Type    | Concentration |
| ------- | ------- | ------------- |
| Source  | p⁺      | 1×10²⁰ cm⁻³   |
| Channel | Undoped | —             |
| Drain   | p⁺      | 1×10²⁰ cm⁻³   |

This enables:

* Strong gate control
* Reduced random dopant fluctuation (RDF)
* Clear observation of gate-induced charge modulation

---

## Physical Models Used

This deck intentionally goes beyond classical models.

### Enabled Physics

* **Fermi–Dirac statistics** (degenerate doping)
* **Schrödinger equation** for quantum confinement
* **NEGF multi-subband transport**
* **Quantum corrections for holes**
* **Ballistic carrier transport**

### NEGF Parameters

| Parameter          | Value |
| ------------------ | ----- |
| Number of subbands | 1     |
| Eigenstates        | 1     |
| Energy grid size   | 2000  |

This configuration is appropriate for **ultra-thin nanowires** where only the lowest subband dominates transport.

---

## Biasing Scheme

* Drain voltage: −0.6 V (p-MOS operation)
* Gate sweep: 0 V → −0.6 V in −0.1 V steps
* Source grounded

The simulation captures the **transfer characteristics (Id–Vg)**.

---

## Outputs and Results

### Saved Structures

* `equilibrium.str` – Zero-bias equilibrium solution
* `on.str` – On-state solution

### Logged Data

* `IdVg.log` – Drain current vs gate voltage

### Extracted Metrics

* **Ioff** at Vg = 0 V
* **Ion** at Vg = −0.6 V
* **Ion/Ioff ratio**

These metrics are critical for evaluating **low-power nanoscale devices**.

---

## Visualization

The deck uses **TonyPlot** to visualize:

* Band diagrams
* Carrier distribution
* Electrostatic potential
* Quantum confinement effects
* Transfer characteristics

<img width="1920" height="1020" alt="band" src="https://github.com/user-attachments/assets/bc6be7dd-f59c-45cf-8a44-c37f465eee2a" />

<img width="1920" height="1020" alt="graph" src="https://github.com/user-attachments/assets/c4c05438-d3c6-4d96-9fdf-6a555407253b" />



---

## Educational Value

This simulation demonstrates:

* Why **GAA nanowires outperform planar devices** at small nodes
* How **quantum mechanics dominates** below ~10 nm
* The role of **NEGF** in modeling ballistic transistors
* The impact of **gate work function engineering**
* Differences between **classical DD and quantum transport**

---


## Intended Use

This deck is meant for:

* Learning advanced TCAD concepts
* Research prototyping
* Methodology demonstration

It is **not** intended as a foundry-calibrated compact model.

---


