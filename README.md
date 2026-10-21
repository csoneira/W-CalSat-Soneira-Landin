# W-CalSat atmospheric attenuation and received-power calculations

Research notebooks and calibration data used to estimate W-band propagation losses and received power for a calibration-satellite concept.

## Scope

The repository contains three distinct elements:

- `W_CalSat_Power_Calculation.ipynb`: end-to-end power calculations, including measured/modelled input power and propagation losses.
- `UCA_Measures.ipynb`: legacy measurement/calibration analysis.
- `Experiments diagram.ipynb`: laboratory measurement schematics.
- `PS_Results_*.npy`: power-supply / source calibration measurements used by the notebooks.
- `point2point.amc`: configuration for the `am` atmospheric model.

The `am` configuration evaluates 30--150 GHz in 10 MHz steps, uses spherical geometry and a US-standard-atmosphere temperature profile, and outputs atmospheric attenuation and free-space path loss. The file explicitly omits ozone and stratospheric H2O.

## Reproducibility status

This is a research archive, not yet a fully reproducible software package. In particular:

1. the notebooks were executed on Windows and contain stored local-path output;
2. `W_CalSat_Power_Calculation.ipynb` calls `atmosphere.ps1`, which is not present in the repository;
3. the original Python package versions were not recorded;
4. the `.npy` files have no accompanying machine-readable acquisition metadata in the repository.

These limitations are documented in [`docs/REPRODUCIBILITY.md`](docs/REPRODUCIBILITY.md). The legacy files remain at repository root for now because the notebooks use relative paths; moving them without first normalising I/O would risk breaking the analysis.

## Environment

Create a Python environment and install the observed notebook dependencies:

```bash
python -m venv .venv
# Linux/macOS
source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Install the [`am` atmospheric model](https://lweb.cfa.harvard.edu/~spaine/am/) separately. The current atmospheric wrapper is Windows-specific and incomplete in this repository; see the reproducibility notes before attempting to regenerate atmospheric outputs.

## Scientific use

For quantitative reuse, record the exact software versions, instrument configuration, calibration chain, units and array schema for each measurement product. Do not infer those quantities from filenames alone.
