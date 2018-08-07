# ssl_ensembles
Semi-supervised learning on ensembles of genome-scale metabolic networks.

Project summary
~~~~~~~~~~~~~~~

First, draft GENREs are created for each organism using mackinac to access the ModelSEED implementation available through PATRIC. The GENREs returned are gapfilled on complete media using ModelSEED's modified version of fastGapFill (a continuous optimization problem that is faster than MILP formulations). We convert the GENRE to a cobrapy model on the PATRIC server, then download the model and save to our workspace. We also save the gapfill solution for each GENRE.

Files: jupyter notebook for creation of GENREs from PATRIC - bin/generate_recons.ipynb

Dependencies
~~~~~~~~~~~~
cobrapy >= 0.13
mackinac (devel branch)
medusa (devel branch)
