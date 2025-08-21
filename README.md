# Soil_Flux
Processing and visualizing soil greenhouse gas flux data from Gasmet GT5000 Terra, with sample datasets included.

Soil Gas Flux Data Processing – Gasmet GT5000 Terra

This repository contains Python scripts and sample data for processing soil greenhouse gas flux measurements collected using the Gasmet GT5000 Terra system. It calculates flux rates for CO₂ and N₂O, generates time-series plots, and produces output files suitable for further analysis.

Features

Process raw RESULTS.txt and log.txt files from soil gas measurements.

Calculate linear slopes of gas concentrations over time.

Generate plots for each sample showing gas concentrations with linear regression fits.

Compute soil fluxes (μmol m⁻² s⁻¹) using chamber geometry, volume, and temperature corrections.

Save processed results as CSV files for further analysis.

File Structure
.
├── Sample_data_processing/       # Folder containing sample data folders
│   ├── Sample1/
│   │   ├── RESULTS.txt
│   │   ├── log.txt
│   │   └── figures/              # Generated plots
│   └── Sample2/
├── process_soil_flux.py          # Main processing script
└── README.md

Requirements

Python 3.8+

Libraries:

pip install pandas numpy matplotlib seaborn

Usage

Place your RESULTS.txt and log.txt files inside a folder for each sample.

Update root_folder in the script to point to the parent directory containing all sample folders:

root_folder = r'C:\path\to\Sample_data_processing'
main(root_folder)


Run the script:

python process_soil_flux.py


After running, each sample folder will contain:

figures/ – PNG plots of gas concentration time series

Soil Flux.csv – CSV file with calculated slopes and soil fluxes

Chamber Geometry and Flux Calculation

Chamber dimensions (example setup):

Collar radius: 0.1143 / 2 m

Collar height: 0.18288 m

Volume of sampling pipe: 0.0011 m³

General Flux Formula
𝐹
=
𝑑
𝐶
𝑑
𝑡
⋅
𝑉
𝐴
⋅
𝑉
𝑚
⋅
273
𝑇
+
273
F=
dt
dC
	​

⋅
A⋅V
m
	​

V
	​

⋅
T+273
273
	​


Where:

𝑑
𝐶
𝑑
𝑡
dt
dC
	​

 = slope of gas concentration over time (ppm s⁻¹)

𝑉
V = total chamber + pipe volume (m³)

𝐴
A = soil surface area enclosed by chamber (m²)

𝑉
𝑚
V
m
	​

 = molar volume of gas (m³ mol⁻¹)

𝑇
T = chamber air temperature (°C)

Simplified Formula (used in code)
Soil Flux
=
Slope
×
Volume Ratio
Area Footprint
×
Temperature Ratio
Soil Flux=
Area Footprint
Slope×Volume Ratio
	​

×Temperature Ratio

Where:

Volume Ratio = Chamber volume / molar volume

Temperature Ratio = 
273
𝑇
+
273
T+273
273
	​

