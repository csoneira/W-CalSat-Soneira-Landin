# Reproducibility notes

## What is defined in the repository

`point2point.amc` defines the atmospheric calculation itself:

- frequency grid: 30 to 150 GHz, 10 MHz spacing;
- spherical geometry;
- radio refractivity;
- source and observer altitude, zenith angle and relative humidity as run-time inputs;
- US-standard-atmosphere temperature structure with tropospheric H2O;
- output columns: frequency, atmospheric attenuation (`tau`, dB) and free-space loss (`tau_fsl`, dB).

`W_CalSat_Power_Calculation.ipynb` reads these propagation terms and combines them with its source-power and telescope calculations. Its observed Python dependencies are listed in `requirements.txt`.

## Missing information

The present repository does not contain enough information for strict computational reproducibility:

- The notebook invokes `atmosphere.ps1`; that wrapper is absent.
- Original Python and package versions are unknown.
- The committed notebook output records a local Windows working directory and therefore should not be interpreted as a portable execution record.
- The `PS_Results_*.npy` files lack a documented array schema, units, instrument model/settings, acquisition timestamps and calibration uncertainties.
- No uncertainty propagation or validation dataset is documented at repository level.

These are provenance gaps, not values to reconstruct from filenames or notebook output.

## Minimum record for future measurements

For each acquisition, record: UTC timestamp, instrument and serial number, firmware/software version, frequency grid and units, source setting and units, measured quantity and units, calibration/reference state, geometry, environmental conditions, and estimated uncertainty. Store these fields beside the numerical array in a text-based metadata file.

## Before publishing numerical results

1. Restore or replace the missing atmospheric wrapper and verify it against a known `am` command.
2. Create a pinned environment from a successful clean run.
3. Define the `.npy` array schema and units.
4. Re-run notebooks from a clean checkout and remove dependence on user-specific paths.
5. State assumptions and propagate the dominant measurement/model uncertainties.
