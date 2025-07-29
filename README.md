This repo is used to aid in visualizing the Florida Current through the use of AVISO+ data with a threshold of geostrophic currents (>0.5 m/s).

`aviso_velocity_download.R` is used to download AVISO+ data.

`aviso_velocity.R` is used to load and plot data.

The processed data can be found here: [aviso_velocity](https://usf.box.com/s/j54a7z0rekvc8jvvfilt5u7ce1a5o5u4)

```bash
aviso_velocity
└── data
    ├── plots
    │   └── animate
    │       └── transect
    ├── processed
    └── raw
        └── copernicus
        └── shapefiles
```


# AVISO+ Sea Surface Height and Velocity

Data downloaded from `Copernicus` for both absolute dynamic topography (m) and
north/east surface velocities (m/s). **NOTE**: you will need a copernicus login to proceed.

Data:       Global Ocean Gridded L4 Sea Surface Heights And Derived Variables

Search:     <https://data.marine.copernicus.eu/products>

Product ID: `SEALEVEL_GLO_PHY_L4_MY_008_047`

Dataset ID: `cmems_obs-sl_glo_phy-ssh_my_allsat-l4-duacs-0.125deg_P1D`

Description: <https://data.marine.copernicus.eu/product/SEALEVEL_GLO_PHY_L4_MY_008_047/description>

Bounds:     
  - Lon: -83.8125, -78.3125  
  - Lat:  22.8125,  26.4375
  
Note: Select all data products when downloading from `MyOceanPro`
      If downloading from `description` page, go to `Data access` then `subset`, 
      then `automate`. Copy the `automate` and modify script below to download
      multiple dates.

Data Info:
<https://documentation.marine.copernicus.eu/PUM/CMEMS-SL-PUM-008-032-068.pdf>


Velocites extraction inspired from:
<https://help.marine.copernicus.eu/en/articles/9711615-how-to-plot-current-vectors-using-r>


## Download Data from `Copernicusmarine` App

- using `copernicusmarine.exe` File

From: <https://help.marine.copernicus.eu/en/articles/10750437-copernicus-marine-toolbox-executable-no-installation>

I recommend moving the file to this directory where this project is stored

To start, open `cmd` or `PowerShell` from explorer. `cd` to location where `.exe`
is located. Then run `copernicusmarine login` and enter "Username" and
"Password". Once completed, you should be able to run the download


### Variables:

- adt            - absolute dynamic topography [m]
- tpa_correction - instrument drift correction [m]
- flag_ice       - ice flag
- sla            - sea level anomaly [m]
- err_sla        - sea level anomaly error [m]

#### u - eastward
  - ugos           - vector velocity [m/s]
  - ugosa          - vector velocity anomly [m/s]
  - err_ugosa      - vector velocity error [m/s]
  
#### v - northward
  - vgos           - vector velocity [m/s]
  - vgosa          - vector velocity anomly [m/s]
  - err_vgosa      - vector velocity error [m/s]
