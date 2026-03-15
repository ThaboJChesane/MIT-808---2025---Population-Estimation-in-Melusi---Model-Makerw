# MIT 808 Project 6 – Model Makers  
### Small-Area Population Estimation using Drone Imagery and Machine Learning

## Overview
This project aims to develop a data-driven framework for estimating population size in informal settlements using high-resolution drone imagery and machine learning techniques.

Traditional census methods are expensive, infrequent, and often inaccurate in rapidly growing settlements. By combining **computer vision**, **geospatial analysis**, and **statistical modelling**, this project explores how building footprints extracted from aerial imagery can be used to estimate population distribution.

The study focuses on **Melusi (Atteridgeville, Pretoria)**.

---

# Project Objectives

The main objectives of this project are:

1. **Dwelling Extraction**
   - Use a fine-tuned **Segment Anything Model (SAM)** to detect and extract building footprints from drone imagery.

2. **Population Estimation**
   - Use **building features, density metrics, and household survey data** to estimate population size.

3. **Machine Learning Model**
   - Develop a **Bayesian regression model** to predict population per building.

4. **Model Evaluation**
   - Assess the performance and validity of the deep learning and regression models.

5. **Framework Development**
   - Propose a reproducible framework for population estimation in informal settlements.

---

# Study Area
The study focuses on:

**Melusi Settlement**  
Atteridgeville, Pretoria, South Africa

This area represents a rapidly developing informal settlement where accurate population estimates are difficult to obtain using traditional census approaches.

---

# Data Sources

## 1. Drone Imagery
- Resolution: **3 cm**
- Source: Department of Geography, Geoinformatics and Meteorology (GGM), University of Pretoria
- Format: Large **GeoTIFF (~7.5 GB)**

The imagery is tiled using **QGIS XYZ tiling** to create manageable image tiles for training the segmentation model.

### Tiling Parameters

| Parameter | Value |
|---|---|
Extent | Map canvas |
Min zoom | 18 |
Max zoom | 20 |
Overlap | 64 |
Quality | 95 |
Tile size | 1024 × 1024 |

These tiles are used as inputs for the **Segment Anything Model**.

---

## 2. GRT-I Baseline Survey Dataset
A household survey dataset collected in:

- **2021**
- **2022**
- **2023**

Versions used:

| Dataset | Description |
|---|---|
BaselineData_V6 | Household survey data without coordinates |
DataBaseline_v2 | Survey data with household coordinates |

This dataset contains **200+ demographic and socio-economic variables**.

---

# Project Workflow

The project consists of four main stages.

## 1. Exploratory Data Analysis (EDA)

EDA is performed to:

- understand dataset structure
- detect missing values
- analyse correlations
- identify useful predictive features

Example analyses include:

- feature correlation heatmaps
- population distribution by block
- household size distribution
- spatial mapping of survey households

---

## 2. Image Processing and Tiling

The drone imagery is extremely large and must be divided into smaller tiles before model training.

Steps:

1. Load GeoTIFF imagery into **QGIS**
2. Generate **XYZ tiles**
3. Export **1024 × 1024 PNG tiles**
4. Prepare tiles for SAM training

---

## 3. Building Detection Model

A **fine-tuned Segment Anything Model (SAM)** is used to detect buildings in the imagery.

### Output
- building masks
- building polygons
- building footprint features

These features are later used for population modelling.

---

## 4. Population Estimation Model

A **Bayesian regression model** is used to estimate population.

### Input Features

Examples include:

- building footprint area
- building density metrics
- proximity features
- household survey variables


## Python libraries:

pandas
numpy
geopandas
matplotlib
seaborn
scikit-learn
pymc
opencv
torch
segment-anything


## GIS tools:

- QGIS
- GeoTIFF processing
- OpenStreetMap basemaps

---

# Example Visualisations

Examples of EDA outputs include:

- Survey distribution across sites
- Household population correlation analysis
- Population distribution per block
- Spatial household population map

These analyses help identify features useful for modelling.

---

# Ethical Considerations

- The survey data is owned by **GRT-INSPIRED**
- The drone imagery is owned by **GGM, University of Pretoria**
- Data is used **strictly for academic research**

Public release of the data requires permission.

---

# Authors

**Thabo Chesane**  
University of Pretoria  
Department of Computer Science  
u20507102@tuks.co.za  

**Kgoboko Maripane**  
University of Pretoria  
Department of Computer Science  
u16373317@tuks.co.za  

---

# Supervisors

**Dr. Samy Katumba**  
Department of Geography, Geoinformatics and Meteorology  
University of Pretoria

**Dr. Adedayo Adeleke**
Department of Geography, Geoinformatics and Meteorology  
University of Pretoria

---

# License
This project is for **academic research purposes only**.

