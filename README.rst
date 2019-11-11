Project summary
~~~~~~~~~~~~~~~

This repository holds all code and data for "Guiding the refinement of biochemical knowledgebases with ensembles of metabolic networks and machine learning", Medlock & Papin, bioRxiv 2018, currently in press at Cell Systems. The manuscript and the accompanying code describe **A**\utomated **M**\etabolic **M**\odel **E**\nsemble-**D**\riven **E**\limination of **U**\ncertainty with **S**\tatistical learning (**AMMEDEUS**). Description of all analyses contained in this repository are expanded upon in the manuscript.

Our goal was to develop a system for guiding the curation of genome-scale metabolic network reconstructions (GENREs) by harnessing the variability across ensembles of GENREs. We generated ensembles of GENREs consistent with experimental data, performed gene essentiality simulations with those ensembles, and applied machine learning to identify differences between networks that are associated with differences in simulated gene essentiality. We applied this approach to 29 bacterial species with suitable genomic and phenotypic data available, generating prioritized curation targets for all species. We summarize these findings across all 29 species to identify reactions and subsystems in the biochemical database used in the study that, if curated, would substantially reduce uncertainty in gene essentiality simulations for many organisms.

Repository Description
~~~~~~~~~~~~~~~~~~~~~~
+-------+---------------------------------------+---------------------------------------------------------------------------+
|Folder | File                                  |Description                                                                |
+-------+---------------------------------------+---------------------------------------------------------------------------+
|bin    |                                       |Analyses                                                                   |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |biolog_processing.ipynb                |Reads, thresholds, and saves biolog data from Plata et al.                 |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |curation_targets.ipynb                 |Calculates curation target metrics and plots Figures 4a-g, Figure 3d, part |
|       |                                       |of Figure 3E, and  Supplemental Figure 2a-d                                |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |deep_gapfill.ipynb                     |Constructs ensembles by gapfilling using algorithm described in Figure 2a-b|
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |essentiality_dataset_comparison.ipynb  |Reads, thresholds, and saves biolog data from Plata et al.                 |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |generate_recons.ipynb                  |Create and save draft reconstructions from ModelSEED via Mackinac          |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |iterative_gapfill.ipynb                |Previous version of deep_gapfill.ipynb. Not used in manuscript             |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |plot_knockouts.ipynb                   |Processes the knockout simulations, performs k-means clustering, performs  |
|       |                                       |random forest classification, and plots Figures 3a and 3c                  |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |reaction_and_gene_knockouts.ipynb      |Performs gene and reaction knockout simulations for all ensembles          |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |subsample_ensembles.ipynb              |Performs ensemble subsampling and visualization for Figures 2c-d and       |      
|       |                                       |Supplemental Figure 1a-b.                                                  |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |test_train_split.ipynb                 |Verifies that random forest performance on a held out test data set is     |
|       |                                       |equivalent to the out-of-bag performance for all species                   |
+-------+---------------------------------------+---------------------------------------------------------------------------+
|data   |                                       |Data sources and lightly-processed versions of the data                    |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |ModelSEED_Subsystems_20190409.tsv      |subsystem information for modelseed downloaded from the modelseed          |
|       |                                       |biochemistry repository on April 9th, 2019. See data link [1].             |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |biolog_base_composition.csv            |composition for biolog base medium (i.e., media without single C/N source).|
|       |                                       |Determined from biolog plate media compositions used within ModelSEED. See |
|       |                                       |data link [2].                                                             |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |biolog_names_to_seed.csv               |table for converting metabolite names as they appear in Plata et al. to    |
|       |                                       |ModelSEED identifiers. Pectin is excluded due to poor representation of    |
|       |                                       |polymers in constraint-based metabolic models.                             |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |patric_gapfill_solutions.json          |metadata for the gapfill solutions returned by Mackinac when constructing  |
|       |                                       |draft reconstructions for this study.                                      |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |patric_genomes.csv                     |PATRIC genome IDs for each species from Plata et al. Note: Plata et al.    |
|       |                                       |did not report strains used. Criteria for choosing a representative genome |
|       |                                       |are in the methods text of the manuscript.                                 |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |patric_recon_info.json                 |additional metadata returned from Mackinac during reconstruction           |
|       |                                       |generation.                                                                |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |plata_biolog_raw.csv                   |Growth data from Plata et al. Data are explained within the manuscript.    |      
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |plata_thresholded.csv                  |thresholded growth data. Species excluded and threshold for binary         |
|       |                                       |growth/nogrowth (True/False) are in biolog_processing.ipynb.               |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |universal_mundy.json                   |Universal model generated via Mackinac in generate_recons.ipynb.           |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |reactions_seed_20180809.tsv            |summary of ModelSEED reactions used throughout, mainly for the "STATUS"    |
|       |                                       |column which indicates whether there are potential mass balance/charge     |
|       |                                       |issues in a reaction.                                                      |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |seed_universal.json                    |Unused, previous version of the universal model.                           |      
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/essentiality/                         |Experimental gene essentiality data from the Online database of gene       |
|       |                                       |essentiality. Also includes PATRIC annotation files for mapping gene IDs   |
|       |                                       |from experimental files to PATRIC IDs within the models.                   |      
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/modelseed_models/                     |Output dradft models from generate_recons.ipynb.                           |      
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |seed_universal.json                    |Unused, previous version of the universal model.                           |      
+-------+---------------------------------------+---------------------------------------------------------------------------+
+results|                                       |Analysis/simulation output and figures.                                    |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/classification_results/               |Cluster assignments and feature imprtances for each species.               | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/collapsed_essentiality/               |Essentiality simulations, with genes collapsed when another gene had       |
|       |                                       |perfectly correlated knockout results.                                     | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/collapsed_features/                   |Presence/absence of each reaction across each ensemble, with perfectly     |
|       |                                       |correlated reactions collapsed into a single feature                       |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/curation_target_plots/                |Curation target plots for each species (e.g. Fig3a)                        | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/deep_ensembles/                       |Ensemble with ~1000 models/members for each species. Models are serialized |
|       |                                       |as a pickle object that can be loaded within Python and used in Medusa.    |
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/ensembles/                            |Unused, previous version of /deep_ensembles/.                              | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/gene_knockout_pcoa_plots/             |PCoA plots of ensemble gene knockouts, colored by cluster membership.      | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/gene_knockout_plots/                  |Unused, heatmaps of ensemble gene knockouts.                               | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/gene_knockouts/                       |Tables with ensemble gene knockout results for each species.               | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/precision_recall/                     |Precision, recall, and ROC plots for 3 species.                            | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |/subsystems/                           |Plots and tables from subsystem analyses. Includes some unpublished plots. | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |ensemble_biomass_subsampling.svg/.png  |Supplemental figure 1a-b.                                                  | 
+       +---------------------------------------+---------------------------------------------------------------------------+
|       |ensemble_rxn_gene_subsampling.svg/.png |Figure 2c-d.                                                               |
+-------+---------------------------------------+---------------------------------------------------------------------------+

Data links:
[1] https://github.com/ModelSEED/ModelSEEDDatabase/blob/dev/Biochemistry/Pathways/ModelSEED_Subsystems.tsv
[2] https://github.com/ModelSEED/ModelSEEDDatabase/blob/dev/Media/media_list_with_meta.txt


Reproducibility Notes
~~~~~~~~~~~~~~~~~~~~~
* deep_gapfill.ipynb has a loop that iterates over each species to generate an ensemble. For each species, this process took 30-120 minutes in my experience. As a result, notebook failures would often require restarting the process, so the code block checks for existing ensembles for each species. If fast generation of all ensembles is necessary, use of a cluster and reworking the notebook to act on individual species, rather than iterating over all species, is recommended. We opted not to take this approach to simplify the codebase and because I had access to reasonably hefty computing power.

* generate_recons.ipynb requires that a user creates a PATRIC account to access the ModelSEED resource via Mackinac. You can create an account on the PATRIC site (https://www.patricbrc.org) but we recommend following whatever the current instructions are for creating a PATRIC account from the ModelSEED website (http://modelseed.org). When executing the notebook, you must replace my account name in the `mackinac.get_token()` function with your own account name, and then you will be prompted to enter your password within the notebook. This cannot be automated, to my knowledge.

* Draft models generated with generate_recons.ipynb contain gapfilled reactions from ModelSEED during their complete media gapfilling step. During this step, flux through biomass is constrained to be positive and exchange reactions for any metabolite for which a transporter is annotated is enabled; reactions required for a feasible solution are added to the network. This process is sensitive to the version of the ModelSEED biochemistry used, thus the solutions returned maay change over time and be substantially different from the models I obtained for this manuscript.

* I attempted to generate figures as final as possible in these notebooks; multiple figures were assembled with Adobe Illustrator in the final publication. Chemical structures were drawn in chemdraw.


Dependencies
~~~~~~~~~~~~
cobrapy >= 0.13
mackinac (devel branch at the time -- see commit 83eced233406c27ed0d749e6d9f76d41350e3b09 in https://github.com/gregmedlock/mackinac)
medusa (devel branch -- see commit e7c7eb88aea0b4dd8d08b996c441ab5f1758cd07 in https://github.com/gregmedlock/Medusa)
