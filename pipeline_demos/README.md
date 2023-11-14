# Coronagraphy Pipeline Tutorial

This tutorial guides users through running the jwst calibration pipeline on MIRI coronagraphy data, using the JWST-ERS-1386 program's observations of HIP 65426 as an example. We show how to customize the pipeline at the stage level and at the individual step level. We do not show how to override reference files.

The pipeline consists of 3 stages:

1. Stage 1: detector-level corrections and "ramps to slopes". 
    This stage converts the data from units of uncalibrated "DN" into the rate unit "DN/s" by performing linearity corrections and slope-fitting to the groups that comprise each integration.
2. Stage 2: photometric calibration
    This stage converts the slopes into units of MJy/sr. Also performs background subtraction, if an association file is provided with background exposures identified.
3. Stage 3: PSF subtraction
    This stage constructs a PSF from the PSF reference targets and subtracts it from the science target(s) using the KLIP algorithm. If more than one roll is used to observe the science target, it derotates and co-adds them.

Pipeline documentation is available here: 


## Requirements

The notebooks make use of the following Python modules:

Standard
- os
- collections
- pathlib

Non-standard
- numpy
- pandas
- matplotlib

Astronomy-specific
- astropy
- astroquery
- jwst

## Contents and usage notes

Please copy the directory structure in addition to the notebooks and README. The notebooks are configured to read and write from the directories provided in this repository. Each notebook has a dedicated output folder, as well as an optional input folder for placing example data downloaded from MAST.
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


### Stage 1

#### `calwebb_detector1-single_file.ipynb`
- Output location: `./stage1/output-step/{step_name}/`

This notebook demonstrates how to run and configure each step of `Detector1Pipeline` independently of the rest of the pipeline. It is useful to run the pipeline in this way if you want to fiddle with the parameters of a particular step and examine its output without having to run the entire stage.

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

