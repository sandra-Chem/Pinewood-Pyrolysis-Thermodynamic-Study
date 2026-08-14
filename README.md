# Pinewood Pyrolysis – Thermodynamic Study Using Python and Cantera

## Overview

This project investigates the **thermodynamic equilibrium behavior of pinewood pyrolysis** using Python and Cantera.

The study examines how equilibrium gas composition and hydrogen production change with temperature under specified thermodynamic conditions.

Two modelling approaches are considered:

1. **Unconstrained Gibbs equilibrium** as a thermodynamic baseline.
2. **Literature-informed constrained Gibbs equilibrium** that accounts for the allocation of biomass into bio-oil and char before gas-phase equilibrium.

The work is a **thermodynamic equilibrium study, not a kinetic study**. It does not calculate reaction rates, activation energies, or time-dependent conversion.

## Objective

* Study the effect of temperature on equilibrium gas composition.
* Calculate equilibrium H₂, CO, CO₂, CH₄ and H₂O composition.
* Estimate H₂ production and H₂ yield relative to dry biomass.
* Establish an unconstrained Gibbs-equilibrium baseline.
* Develop a preliminary constrained/pseudo-equilibrium model incorporating bio-oil and char fractions.
* Compare unconstrained and constrained H₂ predictions.
* Develop a reproducible Python-based workflow for thermodynamic analysis.

## Feedstock

The computational model uses a 300 g raw pinewood basis with 12 wt% moisture.

* Raw pinewood: 300 g
* Moisture: 36 g
* Dry biomass: 264 g

The dry-basis elemental composition used in the model is:

| Element | Composition |
| ------- | ----------: |
| C       |   49.33 wt% |
| H       |    6.06 wt% |
| O       |   44.57 wt% |
| N       |    0.04 wt% |

The corresponding dry-biomass elemental inventory is approximately:

* C = 10.8427 mol atoms
* H = 15.8714 mol atoms
* O = 7.3545 mol atoms
* N = 0.0075 mol atoms

The 36 g moisture is represented as approximately 1.9983 mol H₂O.

## Thermodynamic Model

The equilibrium calculations use:

* **Python**
* **Cantera**
* **GRI30 gas-phase mechanism (`gri30.yaml`)**
* **Graphite (`graphite.yaml`) as a simplified solid-carbon/char surrogate**
* Pressure = **1 atm**
* Temperatures = **600, 700, 800 and 900 °C**
* Equilibrium state = **constant temperature and pressure (TP)**

The equilibrium state is calculated using Cantera's Gibbs-equilibrium functionality.

## Model 1 – Unconstrained Gibbs Equilibrium

In the preliminary model, the feed elemental inventory is represented using:

* CO₂
* H₂
* H₂O
* N₂
* solid carbon

These species provide an initial chemical representation containing the required C/H/O/N inventory. They are starting species for the Gibbs-equilibrium calculation rather than a claim about the initial experimental gas composition.

The elemental balance was verified before equilibrium, with C, H, O and N conserved within numerical tolerance.

### Unconstrained Results

| Temperature | H₂ (mol%) | H₂ yield (g/kg dry biomass) |
| ----------: | --------: | --------------------------: |
|      600 °C |     39.92 |                       39.93 |
|      700 °C |     47.64 |                       57.75 |
|      800 °C |     49.81 |                       68.82 |
|      900 °C |     50.66 |                       73.19 |

The unconstrained model predicts increasing equilibrium H₂ concentration and H₂ yield with increasing temperature over the simulated range.

## Model 2 – Literature-Informed Constrained Gibbs Equilibrium

The constrained model was developed to make the thermodynamic calculation more representative of biomass pyrolysis, where the biomass is distributed among **gas, bio-oil/condensable products and char** rather than being treated only as a gas + solid-carbon equilibrium system.

The constrained workflow is:

```text
Pinewood feed
      │
      ├── Bio-oil / condensables
      │
      ├── Char
      │
      └── Remaining elemental inventory
                 │
                 ▼
          Gas-phase equilibrium
                 │
        ┌────────┼────────┐
        ↓        ↓        ↓
       H₂       CO      CO₂ / CH₄ / H₂O
```

The model first reserves C/H/O material for literature-informed bio-oil and char fractions. The remaining elemental inventory is then assigned to the gas phase, and the C/H/O/N balance is checked before the Gibbs-equilibrium calculation.

### Constraint Basis

For the current sensitivity model:

* Bio-oil fraction = **40.88 wt%**
* Char fraction = **23.23 wt%**
* Remaining gas fraction = **35.88 wt%**

The bio-oil and char elemental compositions are literature-informed and contain explicit modelling assumptions. They are not claimed to be direct measurements of the user's experimental bio-oil or char.

The current constrained model keeps these product fractions fixed across 600–900 °C. Therefore, this model is a **preliminary temperature-sensitivity study**, not a fully temperature-dependent experimental product-distribution model.

## Constrained Results

| Temperature | H₂ (mol%) | H₂ yield (g/kg dry biomass) |
| ----------: | --------: | --------------------------: |
|      600 °C |     37.98 |                       24.72 |
|      700 °C |     45.80 |                       35.30 |
|      800 °C |     46.78 |                       37.29 |
|      900 °C |     45.74 |                       36.57 |

The constrained model predicts its highest H₂ yield within the simulated range at **800 °C**.

This should **not** be interpreted as the experimentally optimum pyrolysis temperature. It is the maximum predicted by the current fixed-constraint theoretical model.

## Unconstrained vs Constrained Comparison

The comparison shows that introducing bio-oil and char constraints lowers the predicted H₂ yield relative to the unconstrained baseline.

| Temperature | Unconstrained (g/kg) | Constrained (g/kg) |
| ----------: | -------------------: | -----------------: |
|      600 °C |                39.93 |              24.72 |
|      700 °C |                57.75 |              35.30 |
|      800 °C |                68.82 |              37.29 |
|      900 °C |                73.19 |              36.57 |

The unconstrained model increases continuously with temperature, whereas the current constrained model reaches a maximum around 800 °C and decreases slightly at 900 °C.

## Interpretation

The difference between the two models arises from their assumptions.

### Unconstrained model

The simplified gas + solid-carbon system allows a much larger fraction of the feed elemental inventory to participate in gas-phase equilibrium.

### Constrained model

Part of the feed inventory is first allocated to bio-oil/condensable products and char. Therefore, less C/H/O is available to the gas phase for equilibrium H₂ formation.

The constrained model therefore provides a more restrictive thermodynamic estimate.

## Important Limitations

The present calculations are **theoretical equilibrium calculations** and should not be interpreted as direct predictions of the experimental batch fixed-bed reactor.

Important limitations include:

* Gibbs equilibrium assumes thermodynamic equilibrium.
* Reaction kinetics and heating-rate effects are not explicitly modeled.
* Residence-time effects are not explicitly modeled.
* The current constrained model uses fixed product constraints across temperatures.
* Bio-oil and char compositions are literature-informed surrogate representations.
* The gas-phase mechanism is not a dedicated pinewood pyrolysis mechanism.
* Experimental reactor behavior may therefore differ significantly from the equilibrium predictions.

## Thermodynamic vs Kinetic Scope

This project is a **thermodynamic modelling study**.

The Cantera calculations determine the equilibrium composition that minimizes Gibbs free energy at specified temperature and pressure.

The project does **not** currently calculate:

* reaction rate constants
* activation energies
* Arrhenius kinetics
* residence-time-dependent conversion
* time-dependent species evolution

A future kinetic model could be developed separately if experimentally determined or literature-supported kinetic parameters become available.

## Software and Tools

* Python
* Cantera
* NumPy
* Pandas
* Matplotlib
* Jupyter Notebook

## Current Status

**Ongoing**

### Completed

* Pinewood feed and moisture calculation
* Dry-basis elemental inventory
* Elemental-balance verification
* Unconstrained Gibbs-equilibrium model
* H₂ concentration and H₂-yield analysis
* Literature-informed constrained Gibbs-equilibrium model
* Constrained vs unconstrained comparison

### Future Work

* Improve the temperature dependence of the product constraints.
* Compare model predictions with experimental gas data.
* Extend the treatment of condensable/bio-oil products.
* Develop process and energy analysis in DWSIM.
* Compare thermodynamic predictions with experimental pyrolysis behavior.

## Project Structure

```text
Pinewood-Pyrolysis-Thermodynamic-Study/
│
├── README.md
├── notebooks/
│   └── THERMODYNAMIC_STUDY_PYROLYSIS.ipynb

│
├── data/
│   ├── unconstrained_equilibrium_results.csv
│   └── constrained_gibbs_temperature_results.csv
│
├── results/
│   ├── unconstrained_H2_yield_vs_temperature.png
│   ├── constrained_H2_yield_vs_temperature.png
│   ├── unconstrained_vs_constrained_H2_yield.png
│   └── unconstrained_vs_constrained_H2_mol_percent.png
│
└── docs/
    └── model_notes.md
```

## Note

The unconstrained results represent a **thermodynamic equilibrium baseline for a simplified gas + solid-carbon system**. The constrained results represent a **preliminary literature-informed sensitivity model** in which material is reserved for bio-oil/condensables and char before gas-phase equilibrium.

Both models should therefore be interpreted as **computational thermodynamic studies**, not direct measurements or validated predictions of the experimental reactor.
