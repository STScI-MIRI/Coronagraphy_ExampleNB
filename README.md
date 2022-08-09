# Coronagraphy_ExampleNB
Example notebooks for coronagraphic image processing. 

## Background subtraction
[Background_subtraction_and_Stage3-HD141569A.ipynb](https://github.com/STScI-MIRI/Coronagraphy_ExampleNB/blob/main/Background_subtraction_and_Stage3-HD141569A.ipynb) 

The [glow stick anomaly](https://jwst-docs.stsci.edu/jwst-mid-infrared-instrument/miri-features-and-caveats#MIRIFeaturesandCaveats-glow_sticksGlowsticksintheMIRI4QPMcoronagraphs) has made it necessary to acquire background observations for every target, so that the glow sticks can be removed. This notebook steps the user through performing the background subtraction on Stage 2b (`calints.fits`) data, and pushing the background-subtracted exposures through the Stage 3 pipeline for PSF subtraction and recombination.
