# Using HyP3 InSAR products to detect active landslides
The combination of Sentinel-1 SAR imagery and the HyP3 on-demand InSAR processing service can be combined to monitor the activity state of the world’s slow-moving landslides efficiently and effectively. This repository contains Jupyter Notebooks that are designed to do this analysis. The main steps are:

1. Request, download and prep a stack of HyP3 interferograms
2. Identify an area of analysis within the InSAR stack
3. Using MintPy, perform a SBAS-based InSAR timeseries analysis using a double difference filter to highlight local deformation (see [Bekaert et al 2020](https://doi.org/10.1016/j.rse.2020.111983))
4. Combine InSAR velocity datasets from ascending and descending orbits to estimate movement in the East-West / vertical direction and identify local deformation “hot spots”

Each of these steps is contained within a separate notebook. Read on to learn more about each notebook.

A note on environments: MintPy is incompatible with some current versions of geospatial python libraries, so steps 1 and 2 must be run in a separate environment than steps 3 and 4. In the future I plan to create dockerfiles for each environment, but until then the user will need to set up their own environments via conda or another package manager. Connect with me on LinkedIn or Twitter!

## Author:
Hi my name is Forrest Williams! I’m passionate about using remote sensing and geospatial data analysis to help solve the world’s environmental challenges. I am currently complete a PhD in Earth Sciences at Massy University in New Zealand, but plan to return home to the U.S. and enter private industry as a data scientist in early 2022.

## Step 1: Request/Download HyP3 products
**Notebook:** download\_hyp3\_insar\_data.ipynb

**Environment:** General Python geospatial analysis environment with the hyp3-sdk package

This notebook handles the requesting and downloading of HyP3 products. Note that you will need to sign up for an account before you can request HyP3 products. Click here to learn more.

## Step 2: Identify area of analysis
**Notebook:** get\_mintpy\_window.ipynb

**Environment:** General Python geospatial analysis environment with the hyp3-sdk package

I find that you are typically interested in a smaller area than the HyP3 InSAR products cover, so this notebook allows to compute the bounds of your study area (in a MintPy readable format) from a study area shapefile.

## Step 3: Time-series processing
**Notebook:** hyp3\_minty.ipynb

**Environment:** MintPy environment

This notebook performs the InSAR time-series SBAS processing using MintPy. If you are not familiar with MintPy I would suggest reading through MintPy’s documentation and examples [here](https://github.com/insarlab/MintPy-tutorial).

## Step 4: Combining and filtering results
**Notebook:** combine\_and\_mask.ipynb

**Environment:** MintPy environment

This step combines the velocity outputs from ascending and descending geometries then creates a hotspot mask to identify areas of deformation that are most likely to be landslide movement
