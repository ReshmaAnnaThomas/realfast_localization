# realfast_localization
Jupyter notebooks to do realfast localization. A test dataset can be found [here](https://drive.google.com/drive/folders/1g7i-F3OgctoNC59N-OGTue3UhfGFqEU8?usp=sharing)

Install rfpipe software from [here](https://github.com/realfastvla/rfpipe/tree/main)

* Step 1: Refining the candidates -- in npix, DM grids, better RFI, etc
* Step 2: Once you find the candidate and save the canddata and cand collection, you can use that info to cut a snipett of data from the full SDM. This is done using the code [bdf_dediperse_cut.py](https://github.com/demorest/sdmpy/blob/master/scripts/bdf_dedisperse_cut.py). This code also dedisperses the candidate based on the canddm from the cand data.
* Step 3: Now you have the mini SDM which you can use to image. For this use [importasdm](https://casadocs.readthedocs.io/en/v6.2.0/api/tt/casatasks.data.importasdm.html) in casa tasks to convert the SDM to a measurement set (MS) file.
* Step 4: Check the .ms file. Do flagging if necessary.
* Step 5: Download calibration products (*tbl files) from the NRAO data archive. Calibrate the .ms using [applycal](https://casadocs.readthedocs.io/en/v6.2.0/api/tt/casatasks.calibration.applycal.html) in CASA. Note: use spwmap if needed.
* Step 6: Image using [tclean](https://casadocs.readthedocs.io/en/stable/api/tt/casatasks.imaging.tclean.html). Do a sub-banded searching by choosing different sets of subsequent spws.  

IMPORTANT: Make sure to use the CASA version specified in the NRAO calibration products. Also check the frequency ordering, spw numbers etc of the realfast SDM and make sure they match with those of the calibration products. 
