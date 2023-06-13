# DESI Early Data Release Overview Paper data

Data files for plots in DESI Collaboration et al 2023,
"The Dark Energy Spectroscopic Instrument: Early Data Release"

Plots in this paper were generated using code in https://github.com/desihub/edrpaper .
Since some of these scripts/notebooks require DESI python packages,
we also provide the processed data points here.

## Figure 1: number of unique tiles per night

**Data file**: `tiles_per_night.csv` with columns night,sv1,sv1x,sv2,sv3.
"sv1x" is for secondary tiles observed during the
sv1 / Target Selection Validation survey.

**Code**: `edrpaper/bin/count_obs`

## Figure 2: N(z) per target type

**Data files**: `Nz_STAR.csv`, `Nz_GALAXY.csv`, `Nz_QSO.csv`.
These are split into 3 separate files for the 3 panels since they
have different redshift ranges.  Each file has the `Z` of the bin center,
`ALL` for the gray summed histogram, and additional columns for the
colored per-targettype histograms.

**Code**: `edrpaper/nb/counting_EDR_targets.ipynb`

## Figure 3: Target density on sky

**Data file**: `goodz_density_hpix_nest_nside64.csv` with columns
healpix,sv1,sv2,sv3.  The healpix column gives the nside=64 nested
healpix numbers; the other columns give the targets per deg^2 for
each of sv1(Target Selection Validation), sv2(Operations Testing), and
sv3(One-Percent Survey).  Healpix that do not have targets from any
of the 3 are not included.

**Code**: `edrpaper/bin/plot_density_skymap`

## Figure 4: Number of overlapping bright tiles for sv3 Rosette 1

**Data file**: `BGS_tilecoverage_rosette1.csv` with columns RA,DEC,NTILE

**Code**: `edrpaper/nb/lss_plots.ipynb`

## Figure 5: ELG target completeness for sv3 Rosette 1

**Data file**: `ELG_completeness_rosette1.csv` with RA,DEC,COMPLETENESS

**Code**: `edrpaper/nb/lss_plots.ipynb`

## Figure 6: comoving number density for LSS catalogs

**Data file**: `lss_nz.json`
Since the different samples have different redshift ranges, this is saved
as a json file with a nested dictionary of the form:
`data[SAMPLE]['z']` and `data[SAMPLE]['nz']`, e.g.
```
import json
import matplotlib.pyplot as plt

with open('lss_nz.json') as fp:
    data = json.load(fp)

for sample in data.keys():
    plt.plot(data[sample]['z'], data[sample]['nz'], label=sample)

plt.legend()
plt.semilogy()
plt.show()
```

**Code**: `edrpaper/nb/lss_plots.ipynb`

## Figure 7: k-correct polynomials

**Data**: Plotting equation 7 using data from Table 9 

**Code**: `edrpaper/nb/lss_plots.ipynb`

