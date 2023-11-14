# Coronagraphy_ExampleNB

Example notebooks for reducing MIRI coronagraphic observations with the [official jwst pipeline](https://github.com/spacetelescope/jwst).

## General JWST calibration pipeline help

We refer users to the [STScI JWebbinar repository](https://www.stsci.edu/jwst/science-execution/jwebbinars) for help on installing and running the pipeline. The following JWebbinars are particularly relevant:

Before launch and commissioning:
- JWebbinar 1: Pipeline Information and Data Products
- JWebbinar 3: Pipeline: Imaging Mode
- JWebbinar 12: JWST Pipeline 101

After launch and commissioning:
- JWebbinar 18: JWST Pipeline refresher 
- JWebbinar 19: ERS: Reducing & Analyzing JWST Coronagraphic Data with spaceKLIP 
- JWebbinar 20: JWST Science Use Cases
- JWebbinar 22: NIRSpec and MIRI: Lessons Learned from Commissioning 
- JWebbinar 24: Jdaviz, the Visualization Tool for JWST


## Pipeline demonstration notebooks

Several notebooks demonstrating how to use the pipeline for different use cases are available in the [pipeline_demos](pipeline_demos) folder. In that folder, you will find another README explaining their contents and usage. These take a complete sequence the JWST-ERS-1386 observations of the exoplanet host HIP 65426, including science target, reference star, and background observations in the F1550C filter. There are 6 notebooks:

### Stage 1
   1. [calwebb_detector1-single_exposure.ipynb](pipeline_demos/calwebb_detector1-single_exposure.ipynb) -> run and configure each step of Stage 1 separately for a single exposure.
   2. [calwebb_detector1-all_exposures.ipynb](pipeline_demos/calwebb_detector1-all_exposures.ipynb) -> run Stage 1 on all the exposures associated with the observing sequence
### Stage 2
   3. [calwebb_image2-single_exposure.ipynb](pipeline_demos/calwebb_image2-single_exposure.ipynb) -> run and configure each step of Stage 2 separately for a single exposure.
   4. [calwebb_image2-all_exposures.ipynb](pipeline_demos/calwebb_image2-all_exposures.ipynb) -> run Stage 2 on all the exposures associated with the observing sequence, using custom-generated association files to link background observations and enable background subtraction.

### Stage 3

   5. [calwebb_coron3.ipynb](pipeline_demos/calwebb_coron3.ipynb) -> run Stage 3 on the flux-calibrated and background-subtracted science and PSF reference exposures using a custom association file.

### Full pipeline

   6. [full_miri_coron_pipeline.ipynb](pipeline_demos/full_miri_coron_pipeline.ipynb) -> run all stages of the pipeline on the full observing sequence. 

These notebooks supersede the older pipeline demonstration notebooks below, which are preserved because although they are outdated, they do contain potentially useful information.

## Older pipeline notebooks

These have been moved to the folder [old_pipeline_demos](old_pipeline_demos).

### Background subtraction
[Background_subtraction_and_Stage3-HD141569A.ipynb](https://github.com/STScI-MIRI/Coronagraphy_ExampleNB/blob/main/Background_subtraction_and_Stage3-HD141569A.ipynb) 

The [glow stick anomaly](https://jwst-docs.stsci.edu/jwst-mid-infrared-instrument/miri-features-and-caveats#MIRIFeaturesandCaveats-glow_sticksGlowsticksintheMIRI4QPMcoronagraphs) has made it necessary to acquire background observations for every target, so that the glow sticks can be removed. This notebook steps the user through performing the background subtraction on Stage 2b (`calints.fits`) data, and pushing the background-subtracted exposures through the Stage 3 pipeline for PSF subtraction and recombination.

### JWST Pipeline Stage 3 processing
[JWST-ERS-01386-stage3_example.ipynb](https://github.com/STScI-MIRI/Coronagraphy_ExampleNB/blob/main/JWST-ERS-01386-stage3_example.ipynb)

This notebook guides the user through the different Stage 2 data products necessary for either pushing the observations through Stage 3 of the JWST pipeline, or performing their own PSF subtraction. It also describes the different Stage 3 output products.

## Offset target acquisition tutorial
[Offset_TA_pySIAF_tutorial.ipynb](https://github.com/STScI-MIRI/Coronagraphy_ExampleNB/blob/main/Offset_TA_pySIAF_tutorial.ipynb)

This notebook walks the user through computing APT offsets between two stars, using their RA and Dec coordinates. It is intended for cases where it is not possible or practical to perform TA on the intended science target, so TA must be performed on a nearby star before slewing the telescope to the science target.

## Questions or feedback?

If you have questions or would like to see additional notebooks here for MIRI Coronagraphy, please contact us [via the Helpdesk](https://jwsthelp.stsci.edu/)!

-- the MIRI Coronagraphy team, Last updated: Nov 2023
