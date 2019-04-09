# ssl_ensembles
Semi-supervised learning on ensembles of genome-scale metabolic networks.

Project summary
~~~~~~~~~~~~~~~

This repository holds all code and data for "Guiding the refinement of biochemical knowledgebases with ensembles of metabolic networks and semi-supervised learning", Medlock & Papin, bioRxiv 2018, currently in preparation for resubmission.

Our goal was to develop a system for guiding the curation of genome-scale metabolic network reconstructions (GENREs) by harnessing the variability across ensembles of GENREs. We generated ensembles of GENREs consistent with experimental data, performed gene essentiality simulations with those ensembles, and applied machine learning to identify differences between networks that are associated with differences in simulated gene essentiality. We applied this approach to 29 bacterial species with suitable genomic and phenotypic data available, generating prioritized curation targets for all species. We summarize these findings across all 29 species to identify reactions and subsystems in the biochemical database used in the study that, if curated, would substantially reduce uncertainty in gene essentiality simulations for many organisms.

Data sources
~~~~~~~~~~~~

*ModelSEED data*
ModelSEED reaction subsystem assignments: https://github.com/ModelSEED/ModelSEEDDatabase/blob/dev/Biochemistry/Pathways/ModelSEED_Subsystems.tsv

Dependencies
~~~~~~~~~~~~
cobrapy >= 0.13
mackinac (devel branch)
medusa (devel branch)
