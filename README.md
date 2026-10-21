# W-CalSat atmospheric attenuation and received-power calculations

Research notebooks and calibration data used to estimate W-band propagation losses and received power for a calibration-satellite concept.

## Repository layout

- `legacy/`: the original 2023 analysis snapshot, kept intact so notebook-relative paths remain valid.
  - `W_CalSat_Power_Calculation.ipynb`: end-to-end power calculations, including measured/modelled input power and propagation losses.
  - `UCA_Measures.ipynb`: legacy measurement/calibration analysis.
  - `Experiments diagram.ipynb`: laboratory measurement schematics.
  - `PS_Results_*.npy`: calibration measurements used by the notebooks.
  - `point2point.amc`: configuration for the `am` atmospheric model.
- `docs/REPRODUCIBILITY.md`: scientific and provenance limitations of the archived analysis.
- `requirements.txt`: Python dependencies observed in the notebooks.

The `am` configuration evaluates 30--150 GHz in 10 MHz steps, uses spherical geometry and a US-standard-atmosphere temperature profile, and outputs atmospheric attenuation and free-space path loss. The file explicitly omits ozone and stratospheric H2O.

## Reproducibility status

This is a research archive, not yet a fully reproducible software package. In particular:

1. the notebooks were executed on Windows and contain stored local-path output;
2. `W_CalSat_Power_Calculation.ipynb` calls `atmosphere.ps1`, which is not present in the repository;
3. the original Python package versions were not recorded;
4. the `.npy` files have no accompanying machine-readable acquisition metadata in the repository.

See [`docs/REPRODUCIBILITY.md`](docs/REPRODUCIBILITY.md) before reusing numerical results.

## Environment

```bash
python -m venv .venv
source .venv/bin/activate          # Linux/macOS
# .venv\Scripts\Activate.ps1      # Windows PowerShell
pip install -r requirements.txt
```

Install the [`am` atmospheric model](https://lweb.cfa.harvard.edu/~spaine/am/) separately. To run the archived notebooks with their original relative paths, start Jupyter from `legacy/`.

## Scientific use

For quantitative reuse, record the exact software versions, instrument configuration, calibration chain, units and array schema for each measurement product. Do not infer those quantities from filenames alone.
