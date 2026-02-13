# SpectralSight: Multispectral Earth Observation & OSCD Visualization

This project provides a streamlined pipeline for reading, processing, and visualizing multispectral satellite imagery, specifically focusing on the **Onera Satellite Change Detection (OSCD)** dataset.

## Introduction to Earth Observation Data

Satellite sensors capture energy across various wavelengths of the electromagnetic spectrum, many of which are invisible to the human eye. While a standard camera captures Red, Green, and Blue (RGB), multispectral satellites like **Sentinel-2** capture additional bands such as Near-Infrared (NIR) and Short-Wave Infrared (SWIR), which are essential for monitoring vegetation health, urban sprawl, and water bodies.

### Publicly Available Datasets

Several high-quality, open-access datasets power modern remote sensing research:

- **Sentinel-2 (ESA):** Offers 13 spectral bands with spatial resolutions up to 10 meters. It is the industry standard for high-frequency land monitoring.
- **Landsat 8/9 (USGS):** Provides a long-term historical record of Earth's surface, crucial for climate change studies.
- **MODIS:** Great for global-scale observations, though it has a lower spatial resolution (250m to 1km).
- **OSCD (Onera Satellite Change Detection):** A specialized dataset containing Sentinel-2 images of cities worldwide taken at different times. It is designed specifically for training and evaluating change detection algorithms.

## Aim of this Notebook

The primary goal of the `visulization-multispactral.ipynb` file is to bridge the gap between raw `.tif` satellite files and interpretable visual data. The workflow focuses on:

1. **Dynamic Band Loading:** Programmatically navigating nested directory structures to locate specific spectral bands (B02, B03, B04).
2. **Reflectance Normalization:** Raw satellite data often contains high-bit depth values that appear dark or distorted on standard screens. This notebook applies clipping and scaling to convert Top-Of-Atmosphere (TOA) reflectance into a 0–1 range.
3. **True-Color Composition:** Stacking individual grayscale bands into a cohesive RGB image to allow for human-level analysis of geographic features.

## Technical Workflow

The implementation utilizes `rasterio` for geospatial data handling and `matplotlib` for visualization.

- **File Discovery:** Uses `pathlib` and `glob` to find band-specific files regardless of naming inconsistencies.
- **Preprocessing:** Implements a normalization function that handles the high dynamic range of Sentinel-2 data.
- **Visualization:** Generates side-by-side comparisons of different cities and timestamps within the OSCD dataset.

## Requirements

To run this work locally, you will need:

```bash
pip install gdal rasterio numpy matplotlib
```


## OSCD dataset citation
```bash
@data{asqe-7s69-19,
  doi = {10.21227/asqe-7s69},
  url = {https://dx.doi.org/10.21227/asqe-7s69},
  author = {Rodrigo Caye Daudt and Bertrand Le Saux and Alexandre Boulch and Yann Gousseau},
  publisher = {IEEE Dataport},
  title = {OSCD - Onera Satellite Change Detection},
  year = {2019}
}
```
