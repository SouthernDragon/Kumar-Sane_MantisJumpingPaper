# Mantis Jumping Analysis

This repository contains analysis code and data for studying mantis jumping behavior from DeepLabCut (DLC) pose-tracking outputs. The workflow converts body-part coordinates into center-of-mass (COM) trajectories, computes takeoff kinematics, and generates figures for distance- and angle-dependent jumping analyses.

## Project overview

The notebook in this repository processes raw DLC-derived CSV files to:

- estimate body COM coordinates from labeled body parts,
- apply filtering to the motion time series,
- calculate takeoff speed and takeoff angle,
- compute target distance and target angle relative to the animal,
- generate plots of COM trajectories and kinematic relationships.

## Repository structure

- `Kumar-Sane_MantisJumpingPaper_Codes.ipynb` – main Jupyter notebook containing the analysis workflow and plotting code.
- `Kumar-Sane_MantisJumping_Distance_Angle.csv` – processed metadata/summary table containing derived variables for each trial.
- `DeepLabCut digitized csv files/` – raw or filtered DLC output files used as input for the analysis.
- `Trimmed csv files for analysis/` – trimmed trial CSV files used during preprocessing and analysis.

## Data inputs

The analysis expects CSV files with body-part coordinate columns and metadata fields such as:

- `filename`
- `takeofftime(ms)`
- `touchdown(ms)`
- `pixelsize(m)`
- `framerate(Hz)`
- `TargetPlatform_x`, `TargetPlatform_y`
- body-part coordinate columns such as `Head_x`, `ProThorax_x`, `MesoThorax_x`, and others

## Python environment

The notebook uses the following Python packages:

- `numpy`
- `pandas`
- `scipy`
- `matplotlib`
- `seaborn`

A typical environment can be created with:

```bash
pip install numpy pandas scipy matplotlib seaborn jupyter
```

## How to use

1. Open `Kumar-Sane_MantisJumpingPaper_Codes.ipynb` in Jupyter Notebook or JupyterLab.
2. Run the cells in order.
3. The notebook will load the metadata CSV and trial files, compute the derived kinematic variables, and generate the requested figures.
4. Some cells include functions that save output tables or plots, depending on the analysis section being executed.

## Notes

- The notebook includes a helper function to parse time-series values stored as string-formatted lists in the CSV.
- The analysis is organized around two experimental conditions: `Distance` and `Angle`.
- The processed outputs include COM trajectories and derived variables such as `TakeOffSpeed`, `TakeOffAngle`, `TargetDistance`, and `TargetAngle`.

## License

This repository does not currently include a license file. If you plan to share or reuse the code publicly, consider adding an appropriate open-source license.
