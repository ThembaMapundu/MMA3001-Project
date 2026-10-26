# MMA3001-Project
Reconstruction of Missing Indoor CO₂ Measurements Using Numerical Interpolation

MMA3001 — Numerical Methods and Machine Learning | Engineering Project

Project overview

Indoor environmental sensors record carbon dioxide (CO₂) concentrations that can support analysis of building ventilation and indoor air quality. Sensor records may contain missing measurements caused by communication interruptions, equipment faults or data-collection problems. This project evaluates whether numerical interpolation can estimate such missing readings from nearby valid observations.

Research question: How does missing-data gap duration affect the reconstruction accuracy and computational performance of linear interpolation, cubic spline interpolation and Piecewise Cubic Hermite Interpolating Polynomial (PCHIP)?

The project implements a reproducible Python workflow for cleaning CO₂ measurements, selecting suitable sensor data, artificially withholding known readings and comparing reconstruction methods against the withheld measurements. The work demonstrates that a numerically successful reconstruction is not necessarily an accurate estimate of the original environmental conditions.

Key findings

For sensor 6012002000869, linear interpolation achieved the lowest root mean square error (RMSE) among the three methods at each tested gap size. Errors generally increased as longer sequences of measurements were withheld; the more complex cubic spline approach did not consistently improve accuracy.

Data

The project uses MMA3001 Dataset 2: Smart Building Occupancy and Environmental Data, focusing on the environmental CO₂ records rather than attempting to infer occupancy directly.

The cleaned CO₂ dataset contains 42,843 valid, unique sensor–timestamp observations across five sensors. The preliminary and reported validation experiments use sensor 6012002000869 (13,800 observations). Another well-represented sensor, 6012002000326 (29,039 observations), could be used for an additional generalisation test.

Repository structure
.
├── README.md

├── SourceData/

│   └── co2_clean.xlsx     

├── notebooks/

│   ├── 01_Data_Exploration.ipynb

│   ├── 02_Sensor_Selection.ipynb

│   ├── 03_Interpolation.ipynb

│   └── 04_Validation.ipynb



Reproducibility and documentation

Core notebook functions use docstrings to describe inputs and outputs. To reproduce a reported run, record the input dataset version, selected sensor, gap sizes, window-selection settings, random seed and package versions. The CSV outputs provide a trial-level audit trail and a summary of accuracy and runtime.

