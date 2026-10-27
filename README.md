# Mantis Jumping Analysis

This repository contains the Jupyter notebook and data tables used to analyze mantis jumping and peering experiments. The notebook processes DeepLabCut (DLC) body-part coordinates, calculates jump and peering kinematics, fits statistical models, and generates manuscript figures.

## Analysis

The notebook covers two main data-processing workflows:

- **Jumping:** filters body-part trajectories, estimates center of mass (COM), and calculates takeoff speed, takeoff angle, body angle, and target geometry.
- **Peering:** filters head-coordinate trajectories and estimates target distance, oscillation frequency, and oscillation amplitude using an FFT.

It also generates figures and fits mixed-effects and individual-level regression models for the reported results.

## Repository contents

- `Code.ipynb` – analysis, statistics, and figure-generation notebook.
- `JumpKinematics.csv` – jump-trial metadata and calculated kinematic measures.
- `PeeringKinematics.csv` – peering-trial metadata and calculated peering measures.
- `Statistics_MixedEffectsModel_Summary.csv` – fixed-effect estimates and model summaries for the mixed-effects analyses.
- `Statistics_IndividualLevelRegressions_Summary.csv` – per-individual linear regression results.
- `CSV files with position coordinates/` – raw DLC coordinate files used by the processing workflows.

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

1. Open a terminal in the repository root, then start Jupyter with `jupyter lab` or `jupyter notebook`.
2. Open `Code.ipynb`. The notebook uses paths relative to the repository root, including `CSV files with position coordinates/`.
3. Run the figure and statistics sections using the checked-in `JumpKinematics.csv` and `PeeringKinematics.csv` tables.
4. To recalculate kinematics from the raw coordinate files, review and enable the commented processing and save calls in the relevant notebook cells. The jump calculation updates `JumpKinematics.csv`; save a copy first if you need to preserve the checked-in table.
5. The statistics section writes `Statistics_MixedEffectsModel_Summary.csv` and `Statistics_IndividualLevelRegressions_Summary.csv` when run.

## Data notes

The jump-processing workflow expects the jump metadata table to include fields such as `filename`, `takeofftime(ms)`, `pixelsize(m)`, `framerate(Hz)`, `TargetPlatform_x`, `TargetPlatform_y`, total mass, and body-part masses. The corresponding raw coordinate files need the body-part x/y columns used in `Code.ipynb` (including head, thorax, abdomen, and leg landmarks).

The peering workflow uses `filename`, `start(ms)`, `stop(ms)`, `Target_y`, `pixelsize(m)`, and `framerate(Hz)` in `PeeringKinematics.csv`, along with `Head_x` and `Head_y` coordinates in each raw trial file.

`Mantis distance and angle.csv` is not present in this repository snapshot. If a notebook cell or figure you need depends on that separate file, obtain it from the original analysis source; the current notebook does not contain a general step that generates it.
