# Reinterpretation of Hodgkin-Huxley Potassium Conductance as a Viscoelastic Property of the Axonal Membrane

**Authors:** Saša Harkai & Matej Daniel  
**Affiliation:** Department of Biomechanics, Faculty of Mechanical Engineering, Czech Technical University in Prague  
**Contact:** matej.daniel@cvut.cz

## Overview

This repository contains the source code and data accompanying the manuscript **"Reinterpretation of Hodgkin-Huxley Potassium Conductance as a Viscoelastic Property of the Axonal Membrane."**

The Hodgkin-Huxley model traditionally treats the lipid bilayer as a passive electrical insulator, attributing all conductance changes to protein channels. This study challenges that view by modeling the "active membrane patch" as a **Kelvin-Voigt viscoelastic material**.

We demonstrate that the original potassium conductance data from Hodgkin and Huxley (1952) can be accurately reproduced by assuming that the membrane's mechanical elasticity ($E^*$) is linearly modulated by the transmembrane voltage.

## Repository Structure

* **`model_membrane_mechanics.ipynb`**: The main Jupyter Notebook. It performs the non-linear least squares fitting of the viscoelastic model to the experimental data and generates the figures used in the study.
* **`hhdata.py`**: A Python module containing digitized data from the original Hodgkin & Huxley (1952) publication (specifically Figure 3, potassium conductance) obtained from Daly, A. C., Gavaghan, D. J., Holmes, C., & Cooper, J. (2015).  Royal Society Open Science, 2(12).	https://doi.org/10.1098/rsos.150499

## The Viscoelastic Model

The model posits that the opening probability of the potassium channel is proportional to the mechanical strain ($\epsilon$) of the membrane patch. The membrane is modeled as a **Kelvin-Voigt** system (a spring and dashpot in parallel).

The potassium conductance $g(t)$ is described by the solution to the viscoelastic constitutive equation:

$$g(t) = g_{\infty} \left(1 - e^{-\frac{t}{\tau}} \right)^{n}$$

Where:
* $g_{\infty} = \left(\frac{V_m}{E^*}\right)^n$ is the steady-state conductance.
* $\tau = \frac{\eta^*}{E^*}$ is the mechanical time constant.
* $E^*$ represents the membrane elasticity.
* $\eta^*$ represents the membrane viscosity.
* $n=4$ represents the four subunits of the potassium channel.

## Requirements

To run the analysis code, you will need a Python 3 environment with the following dependencies:

* `numpy`
* `matplotlib`
* `scipy`

You can install these via pip:

```bash
pip install numpy matplotlib scipy
