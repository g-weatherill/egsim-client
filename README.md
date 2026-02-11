<p align="middle">
    <a title='EFEHR' href='www.efehr.org'><img height='50' src='http://www.efehr.org/export/system/modules/ch.ethz.sed.bootstrap.efehr2021/resources/img/logos/efehr.png'></a>
    &nbsp;
    <a title='GFZ' href='https://www.gfz.de/'><img height='50' src='https://media.gfz-potsdam.de/gfz/wv/media/pic/logo/2025_GFZ-Wortbildmarke-EN-Helmholtzdunkelblau-RGB.jpg'></a>
    &nbsp;
    <a title='EPOS' href='https://www.epos-eu.org/'><img height='50' src='https://www.epos-eu.org/themes/epos/logo.svg'></a>
    <br>
</p>


# egsim-client

## Overview

The `egsim-client` is a repository of Jupyter notebooks and other resources to demonstrate how to use the eGSIM webservice API and showcase its application to various workflows in ground motion modelling and seismic hazard assessment.

The notebooks contained within the first layer of the `notebooks` directory are kept aligned with the current version of the API at any time, and should therefore run without problem. Previous versions of the notebooks are kept in the sub-folder `notebooks/legacy`, and these are retained for reference but will not work with the current version of the API.

The notebooks contain a mixture of basic usage (i.e. how to call the API, visualise and explore the outputs and perform some routine analysis) and advanced usage (i.e. how to integrate the eGSIM API more advanced scientific workflows). 


## Installation and Setup

**We recommend running notebooks from the `egsim-client` within a virtual environment, an explanation of which is found here: <https://docs.python.org/3/library/venv.html>**

Create your virtual environment (this repo is tested under Python 3.9.7 - 3.11.3) and run 
```
pip install --upgrade pip setuptools
```

For the basic usage the required dependencies should be installed via:

```
pip install numpy
pip install scipy
pip install matplotlib
pip install pandas
pip install seaborn
pip install jupyter
```
Note: the `requests` package should be already shipped with `notebook`. If not the case then run `pip install requests`.

The advanced notebooks may require other dependencies, which include:

```
pip install scikit-learn
pip install pymc
```

With the virtual env activated, cd into `notebook` and then run:

``` 
jupyter notebook
```
The notebook will upon in, and be executed from, your web browser.

To convert a notebook to HTML from the command line (inside the `notebook` directory)
use `nbconvert`, e.g.:

```
jupyter nbconvert --to html /path/to/notebook.ipynb
```

## Notebooks

### `Model-to-Model`

This notebook provides a general introduction to the use of the eGSIM API for model-to-model comparison. Steps include:

* Example of how to load in and visualise data from an hdf5 output downloaded from the graphical interface of the model-to-model workflow

* Use of the eGSIM API to produce trellis plots comparing different models for a set of scenarios (i.e. reproducing an online graphical interface workflow)

* Use of the eGSIM API to compare the site amplification scaling of a set of ground motion models - a custom workflow not available via the graphical interface.


### `Exploring Models using Dimensionality Reduction`

This notebook shows an example of a more advanced model-to-model analysis that utilises the eGSIM API. Here the expected ground motions from a suite of GMMs are retrieved for a range of scenarios and intensity measures, which are input into a dimensionality reduction analysis to vizualise the model space of the GMMs.

*This requires that the `scikit-learn` toolkit is installed.*

Steps include:

* Using the eGSIM API to find a sub-set of GMMs from the NGA East project, then retrieving the expected ground motions and visualising via a trellis plot.

* Apply Sammons mapping to the expected GMMs and visualize the 2D representation

* Apply and visualize the 2D representation of the GMMs resulting from Principal Component Analysis (PCA), t-Distributed Stochastic Neighbour Embedding (t-SNE), and Isomap.


### `Model-to-Data`

This notebook demonstrates how to use the model-to-data functionality of the eGSIM API to explore the fit of selected GMMs to ground motions from an example flatfile.

**The flatfile is adapted from the Engineering Strong Motion Flatfile (Lanzano et al., 2019)**

Steps include:

* Apply a set of scoring metrics to a selection of GMMs using a sub-set of the sample data with the API.

* Use the eGSIM API to extract the normalized between- and within-event residuals for a selection of GMMs, intensity measures and sub-set of the sample flatfile (reproduces a workflow available via the visual interface)

*  Use the eGSIM API to extract the station-to-station residuals


### `Comparing Observations and Simulations`

This notebook shows how to use the eGSIM model-to-data functionality to perform a more detailed analysis by exploring the trends in random-effects residuals in a database of observed ground motions (adapted from the ESM flatfile) and a database of ground motions produced by a physics-based simulation software (BB-SPEED)

**The flatfile of ground motion values from the physics-based simulation software is adapted from the BB-SPEEDset version 2.3 (Paolucci et al., 2021)**

This notebook produces the example application shown in Zaccarelli et al. (2025 - *submitted*)

Steps include:

* Retrieval of the normalized random-effects residuals for the two flatfiles and comparisons in trends with respect to magnitude and distance.

* Exploration of the residual trends for four earthquakes common to both flatfiles.  


## Data Sources


>Lanzano, G., Sgobba, S., Luzi, L., Puglia, R., Pacor, F., Felicetta, C., D’Amico, M., Cotton, F., & Bindi, D. (2019). The pan-European Engineering Strong Motion (ESM) flatfile: Compilation criteria and data statistics. Bulletin of Earthquake Engineering, 17(2), 561–582. https://doi.org/10.1007/s10518-018-0480-z

>Luzi L., Lanzano G., Felicetta C., D’Amico M. C., Russo E., Sgobba S., Pacor, F., & ORFEUS Working Group 5 (2020). Engineering Strong Motion Database (ESM) (Version 2.0). Istituto Nazionale di Geofisica e Vulcanologia (INGV). https://doi.org/10.13127/ESM.2

>Paolucci, R., Smerzini, C., and Vanini, M. (2021). BB-SPEEDset: A validated dataset of broadband near-source earthquake ground motions from 3d physics-based numerical simulations. Bulletin of the Seismological Society of America, 111(5), 2527–2545. https://doi.org/10.1785/0120210089




## Acknowledgements and Citation


> Zaccarelli, Riccardo; Weatherill, Graeme (2020): eGSIM - a Python library and web application to select and test Ground Motion models. GFZ Data Services. https://doi.org/10.5880/GFZ.2.6.2023.007

> Riccardo Zaccarelli, Graeme Weatherill, Dino Bindi, Fabrice Cotton; Ground‐Motion Models at Your Fingertips: Easy, Rapid, and Flexible Analysis with eGSIM. Seismological Research Letters 2026; doi:https://doi.org/10.1785/0220250228

