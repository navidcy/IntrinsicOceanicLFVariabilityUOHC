## Notebooks and Datasets for <br/> Intrinsic oceanic decadal variability of upper-ocean heat content

A repository with Jupyter notebooks and datasets that reproduce the analyses and figures included in the paper:

Constantinou, N. C. and Hogg, A. McC. (2021) Intrinsic oceanic decadal variability of upper-ocean heat content. _J. Climate_. (in press; doi:[10.1175/JCLI-D-20-0962.1](https://doi.org/10.1175/JCLI-D-20-0962.1))


```bibtex
@article{Constantinou-Hogg-2021,
  doi = {10.1175/JCLI-D-20-0962.1},
  year = {2021},
  volume = {34},
  number = {15},
  pages = {6175-6189},
  author = {Navid C. Constantinou and Andrew McC. Hogg},
  title = {Intrinsic oceanic decadal variability of upper-ocean heat content},
  journal = {J. Climate}
}
```


## Contents

- [`prepare-raw-data.ipynb`](https://nbviewer.jupyter.org/github/navidcy/IntrinsicOceanicLFVariabilityUOHC/blob/master/prepare-raw-data.ipynb): Downloads raw data from various ACCESS-OM2 models and from CMEMS,  manipulates the data (regrids, coarsens, monthly averages, 2D reductions), and produces smaller datasets
saved in `output` directory

- `grids.zip`: compressed `.nc` files with grid details for the ACCESS-OM2 models at three resolutions. Unzip before running notebooks

- `interpolation_weights.zip`: compressed `.nc` files with the interpolation weights that `xesmf` package uses to regrid the ACCESS-OM2 model output and the CMEMS satellite altimetry onto a regular longitude-latitude grid with 1 degree lateral resolution. Unzip before running notebooks

- `output`: Empty directory that is populated with output produced by `prepare-raw-data.ipynb`. Alternatively, if you don't have access to the raw the ACCESS-OM2 model output, you can dowload the processed output from the Zenodo repository at doi:[10.5281/zenodo.4924968](https://doi.org/10.5281/zenodo.4924968) and populate the `output` directory.

- [`process-data.ipynb`](https://nbviewer.jupyter.org/github/navidcy/IntrinsicOceanicLFVariabilityUOHC/blob/master/process-data.ipynb): Process output from `output` directory to produce figures.

- `figures`: Figures produced by `process-data.ipynb` notebook.


## ACCESS-OM2 model output

Some of the raw ACCESS-OM2 model output is available at doi:[10.4225/41/5a2dc8543105a](https://doi.org/10.4225/41/5a2dc8543105a). However, accessing output from this doi requires users to have access the [Australian National Computing Infrastructure (NCI)](https://nci.org.au).

Users with access to NCI's HPC systems should be able to download all model output used
here given that they are members of projects `cj50` and `ik11`. The experiments we use here
are summarized in the table below.

| Resolution | Forcing | Experiment name |
| :---:        |     :---:      | :---          |
| 1   | IAF     | `1deg_jra55v13_iaf_spinup1_B1`    |
| 1   | RYF     | `1deg_jra55_ryf9091_gadi`    |
| 0.25   | IAF     | `025deg_jra55v13_iaf_gmredi6`    |
| 0.25   | RYF     | `025deg_jra55_ryf9091_gadi`    |
| 0.10   | IAF     | `01deg_jra55v140_iaf`, `01deg_jra55v140_iaf_cycle2`, `01deg_jra55v140_iaf_cycle3`    |
| 0.10   | RYF     | `01deg_jra55v13_ryf9091`    |

(The IAF 0.10 degree outputs are also available via [THREDDS](https://www.unidata.ucar.edu/software/tds/current) at [`https://dapds00.nci.org.au/thredds/catalogs/cj50/access-om2/raw-output/access-om2-01/access-om2-01.html`](https://dapds00.nci.org.au/thredds/catalogs/cj50/access-om2/raw-output/access-om2-01/access-om2-01.html).)

Notebook `prepare-raw-data.ipynb` utilizes [`cosima-cookbook`](https://github.com/cosima/cosima-cookbook)'s functionality to load the required variables needed from the above-mentioned experiments.

Alternatively, if getting access to the [Australian National Computing Infrastructure](https://nci.org.au) seems cumbersome, then feel free to download the processed output from Zenodo repository doi:[10.5281/zenodo.4924968](https://doi.org/10.5281/zenodo.4924968) and use this processed data to populate the `output` directory.


## Directory structure

After you have unzipped all files and either have run `prepare-raw-data.ipynb` notebook or 
downloaded `output` from Zenodo repository at doi:[10.5281/zenodo.4924968](https://doi.org/10.5281/zenodo.4924968), the repository's directory structure should look like:

```
.
├── README.md
├── LICENSE
├── .gitinore
├── grids
│   ├── ocean_grid_10.nc
│   ├── ocean_grid_025.nc
│   └── ocean_grid_01.nc
├── interpolation_weights
│   ├── bilinear_tracer_weights_in025degcmems_out1deg.nc
│   ├── bilinear_tracer_weights_in1degACCESSOM2_out1deg.nc
│   ├── bilinear_tracer_weights_in025degACCESSOM2_out1deg.nc
│   └── bilinear_tracer_weights_in010degACCESSOM2_out1deg.nc
├── output
│   ├── README.md
│   ├── cmems-monthlymean-regridded
│   │   ├── ssh-XXXX.nc
│   │   └── ...
│   ├── ssh-1deg-RYF-regridded
│   │   ├── ssh-XXXX.nc
│   │   └── ...
│   ├── ...
│   ├── ssh-1deg-IAF-regridded
│   │   ├── ssh-XXXX.nc
│   │   └── ...
│   ├── ...
│   ├── uohc-1deg-0m-50m-RYF
│   │   ├── uohc-XXXX.nc
│   │   └── ...
│   ├── ...
│   └── uohc-1deg-0m-50m-IAF
│       ├── uohc-XXXX.nc
│       └── ...
├── figures
│   ├── figure1.pdf
│   └── ...
├── prepare-raw-data.ipynb
└── process-data.ipynb
```
