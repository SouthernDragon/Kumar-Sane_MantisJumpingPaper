# Mantis Jumping Analysis

This repository contains the Jupyter notebook and data used to analyze mantis jumping and peering experiments. It includes high-speed jumping videos, normal-frame-rate peering videos, and the body-part position coordinates digitized from those videos with DeepLabCut (DLC).

## Analysis

The notebook analyzes the DLC coordinate CSVs alongside the trial metadata:

- **Jumping:** filters body-part trajectories, estimates center of mass (COM), and calculates takeoff speed, takeoff angle, body angle, and target geometry using the trial metadata in `JumpKinematics.csv`.
- **Peering:** filters head-coordinate trajectories and estimates target distance, oscillation frequency, and oscillation amplitude using an FFT and the trial metadata in `PeeringKinematics.csv`.

It also generates plots used in the paper and fits mixed-effects and individual-level regression models. The videos are provided as source footage; the analyses use the digitized position-coordinate CSVs rather than processing the videos directly.

## Repository contents

- `Code.ipynb` – analysis, statistics, and figure-generation notebook.
- `JumpKinematics.csv` – jump-trial metadata and calculated kinematic measures.
- `PeeringKinematics.csv` – peering-trial metadata and calculated peering measures.
- `Statistics_MixedEffectsModel_Summary.csv` – fixed-effect estimates and model summaries for the mixed-effects analyses.
- `Statistics_IndividualLevelRegressions_Summary.csv` – per-individual linear regression results.
- `CSV files with position coordinates/` – DLC-digitized body-part position coordinates used by the processing workflows.
- `mp4 videos/` – high-speed jumping videos and normal-frame-rate peering videos corresponding to the trials.

## Requirements

Python 3 and Jupyter are required. The notebook imports these packages:

- `numpy`
- `pandas`
- `scipy`
- `matplotlib`
- `seaborn`
- `statsmodels`

Install them with:

```bash
python -m pip install numpy pandas scipy matplotlib seaborn statsmodels jupyter
```

## Running the notebook

1. Install the requirements below.
2. Open a terminal in the repository root and start Jupyter with `jupyter lab` or `jupyter notebook`.
3. Open `Code.ipynb` and choose **Run All**. Run the notebook from the repository root so its relative data paths resolve.

The notebook workflow reads raw DLC position coordinates from `CSV files with position coordinates/` and uses trial information in `JumpKinematics.csv` and `PeeringKinematics.csv` to analyze jump and peering kinematics, then produces the paper plots and statistical summaries. **Run All** runs the enabled notebook cells from top to bottom. Some analysis, plotting, and file-saving commands are intentionally commented out; uncomment the relevant commands when you want to include those steps or save their outputs. Enabled save commands may overwrite existing CSV files, so keep a copy of any results you want to preserve.