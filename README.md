<img src="atmoscol.jpg" alt="thumbnail" width="800"/>

# Taller de datos científicos con Python AtmosCol 2023

[![nightly-build](https://github.com/ProjectPythia/cookbook-template/actions/workflows/nightly-build.yaml/badge.svg)](https://github.com/ProjectPythia/cookbook-template/actions/workflows/nightly-build.yaml)
[![Binder](https://binder.projectpythia.org/badge_logo.svg)](https://binder.projectpythia.org/v2/gh/ProjectPythia/cookbook-template/main?labpath=notebooks)
[![DOI](https://zenodo.org/badge/475509405.svg)](https://zenodo.org/badge/latestdoi/475509405)

## Motivación

Introducción a la programación científica con Python y acceso a datos hidrometeorológicos de diversas fuentes.

## Autores

Comité científico y organizador de AtmosCol

### Colaboradores

<a href="https://github.com/aladinor/Atmoscol2023/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Atmoscol2023/Atmoscol2023" />
</a>

## Estructura

### Foundational Tools

There are some foundational tools, such as xradar, wradlib, LROSE, and Py-ART!

|        Hora         |                                               Contenido                                                |                                   Tutor                                   |     Duración      |
|:-------------------:|:------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------:|:-----------------:|
| 08:00 AM - 08:15 AM | Apertura del curso. Arranque del Jupyter Lab, instalación de librerias y requerimientos para el taller | Alfonso Ladino, Nicole Rivera, Nestor Bernal, Iván Arias, Maria F. Moreno |    15 minutos     |
| 08:15 AM - 09:00 AM |                         Introducción a Numpy, Pandas, Xarray, Py-Art y Xradar                          |                              Alfonso Ladino                               |    45 minutes     |
| 08:45 AM - 09:30 AM | Acceso a los datos de estaciones IDEAM usando el portal de [datos abiertos](https://www.datos.gov.co/) |                              Alfonso Ladino                               |    45 minutes     |
| 09:30 AM - 10:00 AM |                                          Hands on with Pyrad                                           |             Jordi Figueras i Ventura and Daniel Wolfensberger             |    30 minutes     |
| 10:00 AM - 10:30 AM |                                              Coffee Break                                              |                                                                           |    30 minutes     |
| 10:30 AM - 11:15 AM |                                         Hands on with wradlib                                          |                               Julian Giles                                |    45 minutes     |
| 11:15 AM - 12:00 PM |                                     Hands on with LROSE wind tools                                     |                         Jen DeHart + Ting-Yu Cha                          |    45 minutes     |
| 12:00 PM - 01:15 PM |                                                 LUNCH                                                  |                                                                           | 1 hour 15 minutes |

### Analysis-Specific Tools

There are some analysis-specific tools, such as PyDDA, MetPy, and TOBAC!

|       Time          |    Content                                        | Speaker/Chair | Duration   |
|    :---:            |    :----:                                         |    :---:      | :----:     |
| 01:15 PM - 02:00 PM | Multi-Doppler Analysis with PyDDA                 | Bobby Jackson | 45 minutes |
| 02:00 PM - 02:45 PM | Tracking Cells with TOBAC                         | Sean Freeman + Kelcy Brunner | 45 minutes |
| 02:45 PM - 03:30 PM | Visualizing other Observations and Models with Radar using MetPy | Ryan May and Drew Camron | 45 minutes |
| 03:30 PM - 04:00 PM | Hands on with BALTRAD                             | Daniel Michelson   | 30 minutes |


## Running the Notebooks

You can either run the notebook using [Binder](https://mybinder.org/) or on your local machine.

### Section 1 ( Replace with the title of this section, e.g. "Foundations" )

(Add content for this section, e.g., "The foundational content includes ... ")

### Section 2 ( Replace with the title of this section, e.g. "Example workflows" )

(Add content for this section, e.g., "Example workflows include ... ")

## Running the Notebooks

You can either run the notebook using [Binder](https://binder.projectpythia.org/) or on your local machine.

### Running on Binder

The simplest way to interact with a Jupyter Notebook is through
[Binder](https://binder.projectpythia.org/), which enables the execution of a
[Jupyter Book](https://jupyterbook.org) in the cloud. The details of how this works are not
important for now. All you need to know is how to launch a Pythia
Cookbooks chapter via Binder. Simply navigate your mouse to
the top right corner of the book chapter you are viewing and click
on the rocket ship icon, (see figure below), and be sure to select
“launch Binder”. After a moment you should be presented with a
notebook that you can interact with. I.e. you’ll be able to execute
and even change the example programs. You’ll see that the code cells
have no output at first, until you execute them by pressing
{kbd}`Shift`\+{kbd}`Enter`. Complete details on how to interact with
a live Jupyter notebook are described in [Getting Started with
Jupyter](https://foundations.projectpythia.org/foundations/getting-started-jupyter.html).

### Running on Your Own Machine

If you are interested in running this material locally on your computer, you will need to follow this workflow:

(Replace "cookbook-example" with the title of your cookbooks)

1. Clone the `https://github.com/ProjectPythia/cookbook-example` repository:

   ```bash
    git clone https://github.com/ProjectPythia/cookbook-example.git
   ```

1. Move into the `cookbook-example` directory
   ```bash
   cd cookbook-example
   ```
1. Create and activate your conda environment from the `environment.yml` file
   ```bash
   conda env create -f environment.yml
   conda activate cookbook-example
   ```
1. Move into the `notebooks` directory and start up Jupyterlab
   ```bash
   cd notebooks/
   jupyter lab
   ```
