# Coronagraphy_ExampleNB
Example notebooks for coronagraphic image processing. 

## Background subtraction
[Background_subtraction_and_Stage3-HD141569A.ipynb](https://github.com/STScI-MIRI/Coronagraphy_ExampleNB/blob/main/Background_subtraction_and_Stage3-HD141569A.ipynb) 

The [glow stick anomaly](https://jwst-docs.stsci.edu/jwst-mid-infrared-instrument/miri-features-and-caveats#MIRIFeaturesandCaveats-glow_sticksGlowsticksintheMIRI4QPMcoronagraphs) has made it necessary to acquire background observations for every target, so that the glow sticks can be removed. This notebook steps the user through performing the background subtraction on Stage 2b (`calints.fits`) data, and pushing the background-subtracted exposures through the Stage 3 pipeline for PSF subtraction and recombination.

## JWST Pipeline Stage 3 processing
[JWST-ERS-01386-stage3_example.ipynb](https://github.com/STScI-MIRI/Coronagraphy_ExampleNB/blob/main/JWST-ERS-01386-stage3_example.ipynb)

This notebook guides the user through the different Stage 2 data products necessary for either pushing the observations through Stage 3 of the JWST pipeline, or performing their own PSF subtraction. It also describes the different Stage 3 output products.

## Offset target acquisition tutorial
[Offset_TA_pySIAF_tutorial.ipynb](https://github.com/STScI-MIRI/Coronagraphy_ExampleNB/blob/main/Offset_TA_pySIAF_tutorial.ipynb)

This notebook walks the user through computing APT offsets between two stars, using their RA and Dec coordinates. It is intended for cases where it is not possible or practical to perform TA on the intended science target, so TA must be performed on a nearby star before slewing the telescope to the science target.
