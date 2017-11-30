# YeastMetabolicNetwork-GEM

* Brief Model Description:

This repository contains the current genome-scale metabolic model of _Saccharomyces cerevisiae_ used in the [@SysBioChalmers](https://github.com/SysBioChalmers) group. It is an improved version of [the consensus metabolic model, version 7.6](https://sourceforge.net/projects/yeast/).

* Main Improvements to Original Model:

  * Format changes:
    * FBCv2 compliant.
    * Compatible with latest COBRA and RAVEN parsers.
  * Added information:
    * `subSystems` and `rxnECnumbers` added to reactions based on [KEGG](http://www.genome.jp/kegg/) & [Swissprot](http://www.uniprot.org/uniprot/?query=*&fil=organism%3A%22Saccharomyces+cerevisiae+%28strain+ATCC+204508+%2F+S288c%29+%28Baker%27s+yeast%29+%5B559292%5D%22+AND+reviewed%3Ayes) data.
    * `geneNames` added to genes based on [KEGG](http://www.genome.jp/kegg/) data.
    * Boundary metabolites tracked (available in [`ComplementaryScripts`](https://github.com/SysBioChalmers/yeast-metabolic-network-7.6/blob/master/ComplementaryScripts/boundaryMets.txt)).
  * Simulation improvements:
    * Glucan composition fixed in biomass pseudo-rxn.
    * Proton balance in membrane restored.
    * Ox.Pho. stoichiometry fixed.
    * NGAM rxn introduced.
    * GAM in biomass pseudo-rxn fixed and refitted to chemostat data.

* Model KeyWords:

**GEM Category:** Species; **Utilisation:** maximising growth; **Field:** metabolic-network reconstruction; **Type of Model:** curated, reconstruction; **Model Source:** [Yeast 7.6](https://sourceforge.net/projects/yeast/); **Taxonomy:** _Saccharomyces cerevisiae_; **Metabolic System:** General Metabolism; **Bioreactor**

* Last update: 2017-11-30

* The model:

|Taxonomy | Template Model | Reactions | Metabolites| Genes |
|:-------:|:--------------:|:---------:|:----------:|:-----:|
|_Saccharomyces cerevisiae_|[Yeast 7.6](https://sourceforge.net/projects/yeast/)|3494|2220|909|


This repository is administered by Benjam�n J. S�nchez ([@BenjaSanchez](https://github.com/benjasanchez)), Division of Systems and Synthetic Biology, Department of Biology and Biological Engineering, Chalmers University of Technology.


## Installation

### Required Software:

* A functional Matlab installation (MATLAB 7.3 or higher)
* One of the 2 following:
  * The [COBRA toolbox for MATLAB](https://github.com/opencobra/cobratoolbox).
  * The [RAVEN toolbox for MATLAB](https://github.com/SysBioChalmers/RAVEN).

### Dependencies - Recommended Software:
* libSBML MATLAB API (version [5.15.0](https://sourceforge.net/projects/sbml/files/libsbml/5.15.0/stable/MATLAB%20interface/) is recommended).
* The SBML Toolbox (version [4.1.0](https://sourceforge.net/projects/sbml/files/SBMLToolbox/4.1.0/)  is recommended).
* Gurobi Optimizer for MATLAB (version [6.5.2](http://www.gurobi.com/registration/download-reg) is recommended). 

### Installation Instructions
* Clone aerobic branch from [SysBioChalmers GitHub](https://github.com/SysBioChalmers/yeast-metabolic-network-7.6).
* Add the directory to your Matlab path, instructions [here](https://se.mathworks.com/help/matlab/ref/addpath.html?requestedDomain=www.mathworks.com).


## Complementary Scripts

* `convertYmn2FBC2.m`: Converts yeast7 from COBRA-compatible SBML2 to FBC v2, thereby adding the missing annotation data, which could not be retained with the older COBRA versions.
* `modelCorrections.m`: Corrects various issues in yeast7 (biomass composition, proton balance, Ox.Pho., GAM and NGAM).
* `changeBiomass.m`: Rescales the biomass composition for varying protein content in anaerobic case. Also changes GAM and NGAM.
* `calculateContent.m`: Calculates the protein and carb fraction in the biomass pseudo-rxn.
* `anaerobicModel.m`: Transforms the model to anaerobic conditions.
* `saveYeastModel.m`: Saves yeast model as an `sbml` and `txt` file, and creates `boundaryMets.txt`.
* `boundaryMets.txt`: Contains a list of all boundary metabolites in model, listing the id and name.
* `missingFields`: Folder with functions for adding missing fields to the model.
   * `addGeneNames.m`: Adds the field `geneNames` by extracting the data from KEGG. 
   * `getMissingFields.m`: Retrieves missing information (`rxnECNumbers` and `subSystems`) from KEGG & Swissprot. It uses `changeRules.m` for properly reading the gene-reaction rules, and `findInDB.m`, `getAllPath.m` and `findSubSystem.m` for reading the databases. The latter 3 functions are adapted versions of functions from the [GECKO toolbox](https://github.com/SysBioChalmers/gecko).
   * `ProtDatabase.mat`: Contains the relevant data from Swissprot and KEGG.


## Contributors

* [Eduard J. Kerkhoven](https://www.chalmers.se/en/staff/Pages/Eduard-Kerkhoven.aspx) ([@edkerk](https://github.com/edkerk)), Chalmers University of Technology, Gothenburg Sweden
* [Feiran Li](https://www.chalmers.se/en/staff/Pages/feiranl.aspx) ([@feiranl](https://github.com/feiranl)), Chalmers University of Technology, Gothenburg Sweden
* [Hongzhong Lu](https://www.chalmers.se/en/Staff/Pages/luho.aspx) ([@hongzhonglu](https://github.com/hongzhonglu)), Chalmers University of Technology, Gothenburg Sweden
* [Simonas Marci�auskas](https://www.chalmers.se/en/Staff/Pages/simmarc.aspx) ([@simas232](https://github.com/simas232)), Chalmers University of Technology, Gothenburg Sweden
* [Benjam�n J. S�nchez](https://www.chalmers.se/en/staff/Pages/bensan.aspx) ([@BenjaSanchez](https://github.com/benjasanchez)), Chalmers University of Technology, Gothenburg Sweden