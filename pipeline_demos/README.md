# Coronagraphy Pipeline Example Notebooks


## Introduction

These tutorials guide users through running the jwst calibration pipeline on MIRI coronagraphy data, using the JWST-ERS-1386 program's observations of HIP 65426 as an example. We show how to customize the pipeline at the stage level and at the individual step level. We do not show how to override reference files. 

The MIRI coronagraphy pipeline consists of 3 stages:

1. Stage 1: detector-level corrections and "ramps to slopes"
   - https://jwst-pipeline.readthedocs.io/en/latest/jwst/pipeline/calwebb_detector1.html#calwebb-detector1
   - This stage converts the data from units of uncalibrated "DN" into the rate unit "DN/s" by performing linearity corrections and slope-fitting to the groups that comprise each integration.
2. Stage 2: photometric calibration
   - https://jwst-pipeline.readthedocs.io/en/latest/jwst/pipeline/calwebb_image2.html#calwebb-image2
   - This stage converts the slopes into units of MJy/sr. Also performs background subtraction, if an association file is provided with background exposures identified.
3. Stage 3: PSF subtraction
    - https://jwst-pipeline.readthedocs.io/en/latest/jwst/pipeline/calwebb_coron3.html#calwebb-coron3
    - This stage constructs a PSF from the PSF reference targets and subtracts it from the science target(s) using the KLIP algorithm. If more than one roll is used to observe the science target, it derotates and co-adds them.


General pipeline documentation is available here: https://jwst-pipeline.readthedocs.io/en/latest/ . The different pipelines are listed on this page: https://jwst-pipeline.readthedocs.io/en/latest/jwst/pipeline/main.html#pipelines . 


## Requirements

The notebooks make use of the following Python modules:

Python Standard Library
- os
- collections
- pathlib

Non-Standard Library packages
- numpy
- pandas
- matplotlib

Astronomy-specific packages
- astropy
- astroquery
- jwst

## Contents and usage notes

No data files are provided in this repository. The default behavior for each notebook is to use the output of the notebook corresponding to the preceding pipeline stage (see note below about directory structure). Additionally, all notebooks include code to download the data they need directly from MAST, as well as a few brief instructions for switching it on. This enables users to skip running earlier pipeline stages. 

Please copy the directory structure included in this repository, in addition to the notebooks and README. The notebooks are configured to read and write from the directories provided in this repository. Each notebook has a dedicated output folder, as well as an optional input folder for placing example data downloaded from MAST. 

The directory structure is as follows:
- pipeline_demos/
    - {notebooks here}
    - uncal/
    - stage1/
        - output/
        - output-steps/
    - stage2/
        - input/
        - output-steps/
        - output-asn_all/
    - stage3/
        - input/
        - output/
    - full_pipeline_output/
        - stage1/
        - stage2/
        - stage3/

Notebooks that generate association files will place those files into their respective output folders.

Some notebooks include much more detail than others. The most detailed notebook, in terms of pipeline customization and annotation, is `calwebb_detector-single_file.ipynb` - the notebook that runs a single exposure through each step of the Detector1Pipeline class. In the interest of brevity, subsequent notebooks assume that the user is familiar with the concepts presented in "earlier" notebooks. If something isn't clear in, for example, the `full_pipeline.ipynb` notebook, we suggest that users take a look at the other notebooks to see if it is explained there.

### Stage 1

#### `calwebb_detector1-single_file.ipynb`
- Output location: `./stage1/output-step/{step_name}/`

This notebook demonstrates how to run and configure each step of `Detector1Pipeline` independently of the rest of the pipeline. It is useful to run the pipeline in this way to fiddle with the parameters of a particular step and examine its output without having to run the entire stage.

#### `calwebb_detector1-all_exposures.ipynb`
- Output location: `./stage1/output/`

This notebook runs the Stage 1 pipeline class with default parameters on the full sequence of HIP 65426 15 micron observations.

### Stage 2

#### `calwebb_image2-single_exposure.ipynb`
- Output location: `./stage2/output-single/`

Same idea as `calwebb_detector1-single_file.ipynb`.

#### `calwebb_image2-all_exposures.ipynb`
- Output location: `./stage2/output-asn_all/`

Same idea as `calwebb_detector1-all_exposures.ipynb`, with the added benefit that it demonstrates how to trigger and customize the background subtraction.

### Stage 3

#### `calwebb_coron3.ipynb`
- Output location: `./stage3/output/`

### All stages
- `full_pipeline.ipynb`
- Output location: `./full_pipeline_output/`

This runs the full pipeline in a single notebook on the entire observing sequence.

