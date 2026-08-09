# Pinewood-Pyrolysis-Thermodynamic-Study
Thermodynamic equilibrium analysis of gas products from pinewood pyrolysis using Cantera and Python.
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

Thermodynamic equilibrium calculations have been completed for:

- 400 °C
- 500 °C
- 600 °C

The calculated equilibrium compositions of H₂, CO and CO₂ are provided in the CSV file, and the corresponding temperature-dependent plot is included as a PNG file.

Experimental gas-analysis data are being collected for comparison with the theoretical results.

## Current Status

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
├── Thermodynamic_study.ipynb
├── thermodynamic_equilibrium_results.csv
├── thermodynamic_equilibrium_results.png
└── README.md
