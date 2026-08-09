# Pinewood Pyrolysis – Thermodynamic Study

Thermodynamic equilibrium analysis of gas products from pinewood pyrolysis using Cantera and Python.

## Objective

The aim of this study is to estimate the theoretical equilibrium composition of gases produced during pinewood pyrolysis at different temperatures and compare the theoretical results with experimentally measured gas compositions.

The study focuses particularly on hydrogen production.

## Methodology

- Pinewood was used as the biomass feedstock.
- Experimental pyrolysis experiments were performed at different temperatures.
- Gas samples were collected and analyzed using a gas analyzer.
- Thermodynamic equilibrium calculations were performed using Cantera.
- Python was used for calculations, data processing, and visualization.
- The theoretical equilibrium compositions of H₂, CO, and CO₂ were calculated at 400, 500 and 600 °C.

## Current Results

During a heating experiment with a target temperature of 600 °C, gas samples were collected when the reactor reached 400 °C, 500 °C, and 600 °C. The collected gas samples were analyzed using a gas analyzer.

The calculated equilibrium compositions of H₂, CO and CO₂ are provided in the CSV file, and the corresponding temperature-dependent plot is included as a PNG file.
Gas compositions measured at 400, 500 and 600 °C during the heating experiment are being compared with thermodynamic equilibrium calculations at the corresponding temperatures.

## Current Status

## Experimental Gas Analysis

A pinewood pyrolysis experiment was conducted with a target reactor temperature of 600 °C.

Gas samples were collected during the heating process when the reactor reached approximately 400 °C and 500 °C, followed by samples at 600 °C. An additional gas sample was collected after approximately 15 minutes at 600 °C.

Therefore, the 400 °C and 500 °C measurements represent gas composition during the heating ramp of the 600 °C experiment rather than independent pyrolysis experiments conducted at those temperatures.

The gas samples were analyzed using a gas analyzer.

The measured gas components included:
- CO
- CO₂
- H₂
- O₂
- NOx

The experimental results are provided in `experimental_gas_results.csv`.


**Ongoing**

- Thermodynamic calculations for 400–600 °C completed.
- Experimental gas-analysis data collected for the initial temperature range.
- Comparison between experimental and theoretical results is in progress.
- Further experiments and thermodynamic calculations at higher temperatures (700–900 °C) are planned.

## Future Work

- Extend equilibrium calculations to 700, 800 and 900 °C.
- Add corresponding experimental gas-analysis results.
- Compare experimental and theoretical H₂, CO and CO₂ compositions.
- Analyze the effect of temperature on hydrogen production.
- Investigate the limitations of the equilibrium model for representing actual pyrolysis conditions.

## Project Structure

```text
Pinewood-Pyrolysis-Thermodynamic-Study/
│
├── README.md
├── Thermodynamic_study.ipynb
├── thermodynamic_equilibrium_results.csv
├── thermodynamic_equilibrium_results.png
│
├── experimental_results.csv
└── experimental_gas_results.png
