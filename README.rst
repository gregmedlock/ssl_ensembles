# ssl_ensembles
Semi-supervised learning on ensembles of genome-scale metabolic networks.

Project summary
~~~~~~~~~~~~~~~

First, draft GENREs are created for each organism using mackinac to access the ModelSEED implementation available through PATRIC. The GENREs returned are gapfilled on complete media using ModelSEED's modified version of fastGapFill (a continuous optimization problem that is faster than MILP formulations). We convert the GENRE to a cobrapy model on the PATRIC server, then download the model and save to our workspace. We also save the gapfill solution for each GENRE. Due to connectivity issues with PATRIC, the notebook may need to be rerun multiple times. PATRIC goes down intermittently, and this script will fail with HTTP errors when that is the case.

Files: jupyter notebook for creation of GENREs from PATRIC - bin/generate_recons.ipynb

Second, biolog data from Plata, et al. 2015, are imported and thresholded as in the original paper's analysis at >10 relative colorimetric units from their tetrazolium dye assay. We filter organisms for inclusion by requiring growth on at least 20 carbon sources. Then we convert metabolite identifiers to be consistent with modelSEED identifiers.

Dependencies
~~~~~~~~~~~~
cobrapy >= 0.13
mackinac (devel branch)
medusa (devel branch)
