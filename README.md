# MMA3001-Project
Reconstruction of Missing Indoor CO₂ Measurements Using Numerical Interpolation

MMA3001 — Numerical Methods and Machine Learning | Engineering Project

Project overview

Indoor environmental sensors record carbon dioxide (CO₂) concentrations that can support analysis of building ventilation and indoor air quality. Sensor records may contain missing measurements caused by communication interruptions, equipment faults or data-collection problems. This project evaluates whether numerical interpolation can estimate such missing readings from nearby valid observations.

Research question: How does missing-data gap duration affect the reconstruction accuracy and computational performance of linear interpolation, cubic spline interpolation and Piecewise Cubic Hermite Interpolating Polynomial (PCHIP)?

The project implements a reproducible Python workflow for cleaning CO₂ measurements, selecting suitable sensor data, artificially withholding known readings and comparing reconstruction methods against the withheld measurements. The work demonstrates that a numerically successful reconstruction is not necessarily an accurate estimate of the original environmental conditions.

Key findings

For sensor 6012002000869, linear interpolation achieved the lowest root mean square error (RMSE) among the three methods at each tested gap size. Errors generally increased as longer sequences of measurements were withheld; the more complex cubic spline approach did not consistently improve accuracy.

Important limitation: Only one eligible non-overlapping 12-reading gap was selected by the validation procedure, so results for that category are exploratory and must not be interpreted as a statistically reliable estimate of performance for long gaps. Across all four categories, the recorded validation run comprised 91 artificial-gap experiments, 273 method evaluations, and zero reported execution failures. The zero-failure result concerns execution, not reconstruction accuracy.

The validation selects disjoint local windows within each run. Windows used for different gap lengths are therefore different parts of the time series, which may themselves have different CO₂ variability. This limits causal interpretations of the effect of gap duration.

Data

The project uses MMA3001 Dataset 2: Smart Building Occupancy and Environmental Data, focusing on the environmental CO₂ records rather than attempting to infer occupancy directly.

The cleaned CO₂ dataset contains 42,843 valid, unique sensor–timestamp observations across five sensors. The preliminary and reported validation experiments use sensor 6012002000869 (13,800 observations). Another well-represented sensor, 6012002000326 (29,039 observations), could be used for an additional generalisation test.

The preprocessing workflow removes missing/invalid timestamps, non-finite or non-positive CO₂ values; sorts observations by time; and consolidates duplicate measurements at the same sensor and timestamp using their median. Original recording gaps are distinguished from artificially hidden known measurements used for validation.

Repository structure

The following is the recommended repository layout; adjust paths or names to match the actual repository before publishing.

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

