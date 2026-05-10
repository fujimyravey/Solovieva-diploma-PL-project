# Polar low pressure regression and Sentinel-3 SLSTR scene viewer

This repository contains notebooks and project files prepared for a diploma project on polar lows.

The project has two main parts:

1. a regression model for estimating polar low central pressure from Sentinel-3 SLSTR crop images;
2. a scene-track viewer for checking the spatial and temporal matching between satellite scenes and polar low tracks.

## Repository structure

notebooks/
- 01_train_PL_regression_model.ipynb
- 02_PL_scene_track_viewer.ipynb

data/
- Solovieva_diploma_PL_training_dataset.csv
- Solovieva_diploma_PL_training_dataset_metadata.json
- Solovieva_diploma_PL_training_dataset_rematched_consistent.csv
- Solovieva_diploma_PL_viewer_track_points_rematched_consistent.csv

models/
- reserved for the trained regression model

sample_data/
- small example subset of Sentinel-3 SLSTR crop images

docs/
- screenshots and additional project materials

## Notebooks

### 01_train_PL_regression_model.ipynb

This notebook contains the model training pipeline:

- loading the training table;
- checking required columns;
- loading and preprocessing crop images;
- adding contextual features;
- splitting data into train, validation and test subsets;
- training the convolutional regression model;
- calculating quality metrics;
- saving model outputs and diagnostic plots.

Main target variable:

- slp: sea-level pressure in the polar low center, hPa.

### 02_PL_scene_track_viewer.ipynb

This notebook contains the scene-track viewer.

The viewer is used to:

- display Sentinel-3 SLSTR crop images;
- show scene date, time, satellite, coordinates and pressure;
- match the scene time with polar low track points;
- interpolate the cyclone position between neighboring track points;
- estimate the offset between the scene center and the track position.

## Data

The full image archive and model files can be too large for a regular GitHub repository. For this reason, the repository contains tables, notebooks and a small example subset. The full data and trained model should be stored separately or added through Git LFS if needed.

## Installation

The project was prepared for Google Colab.

Main Python packages:

- tensorflow
- numpy
- pandas
- matplotlib
- scikit-learn
- pillow
- openpyxl
- tqdm
- ipywidgets
- ipyleaflet

Install dependencies locally:

    pip install -r requirements.txt

## Usage

Run the notebooks in this order:

1. notebooks/01_train_PL_regression_model.ipynb
2. notebooks/02_PL_scene_track_viewer.ipynb

Before running the notebooks, check paths to the project folder, data tables, image folder and model folder.

## Limitations

The model estimates pressure from satellite image crops and a limited set of contextual features. Prediction quality depends on the consistency of track data, the temporal matching between scenes and tracks, the pressure distribution in the training sample and the quality of crop images.

The viewer is intended for data checking, visual inspection and interpretation of results. It is not an operational monitoring system.

## Author

Maria Solovieva

## License

License conditions should be specified before public release.
