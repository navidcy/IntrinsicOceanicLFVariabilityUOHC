## Notebooks and Datasets for <br/> Intrinsic oceanic decadal variability of upper-ocean heat content

A repository with Jupyter notebooks and datasets that reproduce the analyses and figures included in the paper:

Constantinou, N. C. and Hogg, A. McC. (2021) Intrinsic oceanic decadal variability of upper-ocean heat content. _J. Climate_. (in press; doi:[10.1175/JCLI-D-20-0962.1](https://doi.org/10.1175/JCLI-D-20-0962.1))


```bibtex
@article{Constantinou-Hogg-2021,
  doi = {10.1175/JCLI-D-20-0962.1},
  url = {https://doi.org/10.1175/JCLI-D-20-0962.1},
  note = {In press.},
  year = {2021},
  volume = {},
  number = {},
  pages = {},
  author = {Navid C. Constantinou and Andrew McC. Hogg},
  title = {Intrinsic oceanic decadal variability of upper-ocean heat content},
  journal = {J. Climate}
}
```


## Contents

- [`prepare-raw-data.ipynb`](https://nbviewer.jupyter.org/github/navidcy/IntrinsicOceanicLFVariabilityUOHC/blob/master/prepare-raw-data.ipynb): download raw data from various ACCESS-OM2 models and from CMEMS and manipulate (regrid, coarsen, montly averages, 2D reduction) to produce output in `output` directory.
- `grids.zip`: compressed `.nc` files with grid details for the ACCESS-OM2 models at three resolutions. Unzip before running notebooks.
- `interpolation_weights`: compressed `.nc` files with the interpolation weights that `xesmf` package uses to regrid the ACCESS-OM2 model output and the CMEMS satellite altimetry onto a regular longitude-latitude grid with 1 degree lateral resolution. Unzip before running notebooks.

### Directory structure

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
├── prepare-raw-data.ipynb
└── ...
```
