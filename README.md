# Pinewood Pyrolysis – Thermodynamic Study

## Overview

This project investigates the thermodynamic equilibrium composition of gaseous species associated with pinewood pyrolysis using Python and Cantera.

The computational study examines how the equilibrium composition of selected gas species changes with temperature under specified thermodynamic conditions.

## Objective

* Study the effect of temperature on thermodynamic equilibrium gas composition.
* Calculate equilibrium mole percentages of selected gaseous species.
* Explore hydrogen formation under different temperature conditions.
* Develop a Python-based computational workflow for thermodynamic analysis.

## Computational Method

Thermodynamic equilibrium calculations are performed using Cantera.

The calculation uses the elemental composition of pinewood as the initial composition and determines the equilibrium gas-phase composition at specified temperatures and pressure.

Cantera's `equilibrate("TP")` method is used to calculate the equilibrium state at constant temperature and pressure.

### Conditions

* Feedstock: Pinewood
* Pressure: 1 atm
* Temperatures currently studied: 400, 500 and 600 °C
* Main species analyzed: H₂, CO, CO₂ and CH₄

## Software and Tools

* Python
* Cantera
* NumPy
* Pandas
* Matplotlib
* Jupyter Notebook

## Results

The current computational analysis provides thermodynamic equilibrium compositions at 400, 500 and 600 °C.

The calculated results are stored in:

* `thermodynamic_equilibrium_results.csv`

The corresponding visualization is provided as:

* `thermodynamic_equilibrium_results.png`

The complete computational workflow is available in:

* `Thermodynamic study.ipynb`

## Current Status

**Ongoing**

The current version contains equilibrium calculations for 400–600 °C.

Future work will extend the temperature range and further investigate the temperature dependence of equilibrium gas composition and hydrogen formation.

## Future Work

* Extend equilibrium calculations to higher temperatures.
* Analyze the temperature dependence of H₂, CO, CO₂ and other relevant gas species.
* Improve the organization and automation of the computational workflow.
* Investigate the suitability and limitations of thermodynamic equilibrium modelling for biomass pyrolysis systems.
* Develop further computational analysis using Python and Cantera.

## Project Structure

```text
Pinewood-Pyrolysis-Thermodynamic-Study/
│
├── README.md
├── Thermodynamic study.ipynb
├── thermodynamic_equilibrium_results.csv
└── thermodynamic_equilibrium_results.png
```

## Note

The calculated compositions represent thermodynamic equilibrium states under the assumptions and conditions specified in the model. They should therefore be interpreted as theoretical equilibrium results rather than direct predictions of an experimental reactor output.
