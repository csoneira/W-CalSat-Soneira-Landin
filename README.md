# W-CalSat analysis — Cayetano Soneira Landín

Research notebooks and calibration data developed by **Cayetano Soneira Landín** for the study of W-band propagation losses, received power and calibration-source performance for a satellite-based CMB calibration concept.

This repository preserves the analysis associated with the 2023 Master's thesis *Fuente de calibración embarcada en satélite para experimentos del Fondo Cósmico de Microondas desde tierra*, completed at the University of Cantabria.

## Publications and scientific provenance

The work represented here was first presented in:

- C. Soneira Landín, *Fuente de calibración embarcada en satélite para experimentos del Fondo Cósmico de Microondas desde tierra*, Master's thesis, Universidad de Cantabria, 2023. [Thesis PDF](https://repositorio.unican.es/xmlui/bitstream/handle/10902/30822/SoneiraLandinCayetano.pdf?sequence=1&isAllowed=y)

It subsequently contributed to:

- F. J. Casas, E. Martinez-Gonzalez, J. Cubas, G. Pascual-Cisneros, I. Sánchez-Ramos, L. Castelló, P. Vielva and B. Barreiro, “LEO-CalSat for the calibration of W-band ground-based CMB polarization experiments,” *Frontiers in Astronomy and Space Sciences* **13** (2026), 1671698. [doi:10.3389/fspas.2026.1671698](https://doi.org/10.3389/fspas.2026.1671698)

The 2026 paper explicitly cites Soneira Landín (2023) in its received-power, detector-saturation and signal-to-noise analysis, and acknowledges Cayetano Soneira Landín's Master's-thesis contribution. The atmospheric-loss and received-power results shown in that part of the paper are therefore directly connected to the calculation chain archived here. The paper does not explicitly label individual figures as reproduced or adapted from the thesis, so no stronger figure-level provenance claim is made here.

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
