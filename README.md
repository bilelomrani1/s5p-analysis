# S5P-Analysis

This is the companion repository of [s5p-tools](https://github.com/bilelomrani1/s5p-tools). It shows how to download, preprocess and analyze Sentinel-5P data with Python.

## Setting up

We recommend setting up a virtual environment with [conda](https://docs.conda.io/projects/conda/en/latest/) for easy management of external dependencies. 

1. Clone the [s5p-tools](https://github.com/bilelomrani1/s5p-tools) repository locally.
    ```
    git clone https://github.com/bilelomrani1/s5p-tools.git
    ```

2. Create a virtual environment named `s5p` with Python 3.7 and `s5p-tools` dependencies.

    ```
    conda create -n s5p python=3.7
    conda activate s5p
    conda config --add channels stcorp
    conda install -y -c stcorp -c conda-forge jupyterlab cartopy dask harp seaborn
    pip install -r s5p-tools/requirements.txt
    ```

## Downloading data

We use the default script provided by `s5p-tools` to download and process data from Sentinel-5P. Here, we query the tropospheric column of NO2 over mainland France between 01/06/2020 and 08/06/2020. For more details on how to use `s5p-tools`, please refer to the README.

> **Note:** The shapefile provided in this repository contains multiple geometries corresponding to the different administrative areas of mainland France. In this case, `s5p-tools` considers the union of all geometries when masking with the --shp flag.

```
python s5p-tools/s5p-request.py L2__NO2___ --aoi geojson/france.geojson --shp shp/fr-regions.shp --date 20200601 20200608
```

## Opening the notebook

1. Create a Jupyter server with
    ```
    jupyter lab
    ```

2. Open the notebook `s5p-analysis.ipynb`.

## Acknowledgements

The authors are grateful to the Luxembourg Institute of Socio-Economic Research (LISER) for funding this project. The authors would also like to acknowledge the European Spatial Agency for providing the API for the Sentinel 5P Hub. The content is solely the responsibility of the authors and does not necessarily represent the official views of the LISER.

If you use this code, please consider citing the following paper.

```
@article{OMRANI2020105089,
title = "Spatio-temporal data on the air pollutant nitrogen dioxide derived from Sentinel satellite for France",
journal = "Data in Brief",
volume = "28",
pages = "105089",
year = "2020",
issn = "2352-3409",
doi = "https://doi.org/10.1016/j.dib.2019.105089",
url = "http://www.sciencedirect.com/science/article/pii/S2352340919314453",
author = "Hichem Omrani and Bilel Omrani and Benoit Parmentier and Marco Helbich",
keywords = "Air pollution, Remote sensing, Monitoring",
abstract = "Monitoring of air pollution is an important task in public health. Availability of data is often hindered by the paucity of the ground monitoring station network. We present here a new spatio-temporal dataset collected and processed from the Sentinel 5P remote sensing platform. As an example application, we applied the full workflow to process measurements of nitrogen dioxide (NO2) collected over the territory of mainland France from May 2018 to June 2019. The data stack generated is daily measurements at a 4 × 7 km spatial resolution. The supplementary Python code package used to collect and process the data is made publicly available. The dataset provided in this article is of value for policy-makers and health assessment."
}
```
