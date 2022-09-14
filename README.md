# The Learning Objectives for the course are summarized below:

* Understand the relevance of virtual screening and identify the benefits of screening very large ligand libraries
* Recall and apply the virtual screening concepts, including docking, active learning, and shape screening
* Recall and apply knowledge of target validation by preparing a target for structure-based virtual screening 
* Recall and apply knowledge of library selection by preparing and filtering a ligand library for screening
* Understand and demonstrate the importance of setting up, running and analyzing validation studies and then running perspective screens using active learning, docking, and shape screening tools
* Understand and demonstrate methods of post-screening analysis, including; filtering, clustering, diversity enhancement, and comparison of scoring functions
* Recall examples of methods that can be used after high-throughput virtual screening 
* Complete a case study covering the HTVS process; assess various aspects of the screen, justify hit selection and submit absolute binding free energy perturbation predictions for chosen hits

As well as using Maestro in this course, participants will learn how to submit jobs and run Schrödinger scripts via the command line. For a useful overview, see our Using the Command Line with the Schrödinger Platform guidance.

# Module 1: Some terms to understand

•	Absorption: The movement of a compound/drug from the site of administration to the bloodstream. This process involves several phases and depends upon the method of delivery (oral, topical, intravenous etc.). Lipinski's rule of 5 famously predicts that poor absorption is more likely when there are more than 5 hydrogen bond donors, 10 hydrogen bond acceptors, a molecular weight greater than 500 and a calculated LogP greater than 5.

•	Chemical stability: The stability of a drug is critical to efficacy, as the loss of a drug through a chemical reaction will result in reduction of potency and may result in degradation into a toxic substance. To learn more about chemical stability of drug substances, read this chapter from the Stability of Drugs and Dosage Forms.

•	Directed screen: A type of high-throughput screen that tests large compound libraries with user-intervention involved in the selecting of compound chemotypes.

•	DNA encoded libraries (DEL): A technology for the synthesis and screening of large collections of small molecule compounds by the conjugation of chemical compounds or building blocks to short DNA fragments that serve as identification bar codes through PCR amplification. To learn more, read through the DEL Wikipedia page that is very well written

•	Drug discovery pipeline: The process by which hits are identified, optimized to leads, and leads are tested for suitability as new chemical entities (NCEs). The NCEs are validated before approval by the FDA.

•	Fragment Based Drug Discovery: A series of methods in drug discovery that use small organic molecules which are small in size and low in molecular weight and may bind only weakly to the biological target (protein), and then grow them or combine them to produce a lead compound with a higher affinity. To learn more, read this introduction to fragment-based drug discovery by Carmot Therapeutics.

•	Free energy perturbation (FEP): An alchemical approach that uses molecular dynamics simulations or Monte Carlo methods to compute the free energy differences between two ligands in solution and in a protein binding site. To learn about the industry standard FEP+ technology read the Schrödinger webpage. To learn more about how this method has been successful in predicting GPCR binding affinities, see this high-level video or read the corresponding Open Access article.

•	Hit: A small molecule that is known to inhibit or bind to a target in drug discovery. Most times, this hit molecule does not have optimized properties or high enough affinity to fully satisfy the needs of a project. Functional groups on the hit are usually altered to address this in what will become a lead molecule. 

•	Lead ( or Core) Hopping: the identification of molecular structures that have the same functional inhibition of a given target with significantly different molecular backbones or core moieties.

•	Ligand-based virtual screening: Using the structure and chemical properties of a hit ligand or series of ligands to assess compounds as potential binders on the computer.

•	Metabolic stability: The stability of a drug within a cellular environment, as many metabolic enzymes within our cells (p450s, oxidases, aldo-ketoreductases, esterases, conjugases etc), are able to degrade drugs into other compounds thus reducing potency and potentially creating toxic substances. To read more on metabolic stability in drug discovery, read this article from Millenium: The Takeda Oncology company.

•	Random screen: A type of high-throughput screen that tests large compound libraries without user-intervention involved in selecting compound chemotypes.

•	Safety: Drug safety is important to assess, including side effects due to off-target effects, as well as toxicity issues that arise from chemical and metabolic instability. To read more on common methods for assessing drug safety, see this Nature correspondence.

•	Solubility in drug discovery: A measure of how well a small molecule dissolves in the blood, usually predicted through the solubility coefficient of a compound in water versus octanol. For more background on the relationship between solubility and physicochemical properties, see this American Pharmaceutical Review article.

•	Structure-activity relationship (SAR): A relationship that is built based on analyzing multiple compounds with similar cores but different functional groups to understand the impact that chemical structure changes have on the activity of the compound against a target.

•	Structure-based drug design (SBDD): Using the information present in a macromolecule or protein structure to identify hits and optimize drug-like properties.

•	Structure-based virtual screening: Using the structure and chemical properties of a binding site on a macromolecule or protein target to assess compounds as potential binders on the computer.

•	Target: A macromolecule (most commonly a protein) that will be targeted by a small molecule in a drug discovery project. Often the small molecule will cause some conformational change or lock the macromolecule into a particular conformation and thus affect that macromolecule's activity and downstream signaling pathways.


# Module 1.3 The Benefits of Screening Ultra-Large Libraries Transcript (Schoichet paper: https://www.nature.com/articles/s41586-019-0917-9)

* Expanding Chemical Space : Getting new medicines to patients faster is the ultimate goal for drug discovery teams. Yet chemical space is vast, and only a tiny fraction of the billions of potentially pharmacologically active molecules are available to screen physically. Structure-based docking can screen virtual libraries of great size and diversity, enabling us to select only the best-fitting molecules for synthesis and testing.
While physical compound collections typically include less than 20 million compounds......Recent advances, for example the advent of DNA encoded libraries, have extended the scale of screening libraries to the trillions. The GDB-17 (https://gdb.unibe.ch/downloads/), the so-called “chemical universe database” , covers all molecules with up to 17 atoms that contain C, N, O, S, and halogen atoms. This database contains over 166 billion compounds

# Module 4.1d
In this section, for ligand-based virtual screening, we profiled and filtered ~2 million compound subset of the Enamine REAL library.  (pre-run)

# Module 4.3
For shape-based screening of a chemical library with GPU shape, we prepared the library and probe molecules. We select 10 probe(template to compare with) molecules from cognate ligands as well as the PLK1 DUD-E actives(118) we prepared earlier. We can use just one probe, but increasing the number and diversity probes generally improves performance, though this begins to saturate at around 10 molecules. We used the tools within Maestro to cluster these active PLK1 compounds and select 10 diverse probes to use in our Shape screen. 

Each molecule in the screening deck(chemicals library) analyzed in the same way and compared with the profiles of each of the template or probe molecules. We have prepare the screening deck with creating shape data file tool of maestro.

# Module 5.2

Here we used Active Learning Glide (pre-run) in “evaluate” mode with our filtered Enamine REAL subset library (~2 million compounds). Evaluate mode allows us to use a pre -generated ML model to rank a large library to compounds, then choose the number (in this case we will use 5%, which will be prepared with LigPrep) of top-scoring compounds to dock to our validated 2OWB_dry_grid using Glide SP. 

The ML model has been generated already, so we will be using Active Learning Glide in “evaluate” mode. This mode uses the pre-generated model to rank the entire library and then run Glide SP docking for a specified percentage of the top ranked compounds. 

# Module 5.3

In this section, we run GPU shape screening using 10 probe molecules and Enamine REAL subset library shape data file prepared in 4.3, to do that we used shape screening tool.

# Module 6.1
In this section, structure-based and ligand-based prospective screens we ran earlier have to be completed. 
We here used DISE like selection of ordered compounds are often used to balance the tension between “best score” and “chemical diversity”. The premise is that a “novel” candidate compound is potentially more valuable than a “degenerate” candidate of roughly equal score. 

Here we reduced the ~100,000 compounds to top scoring 1000 hits for both SBVS and LBVS

Here our aim is to increase the structural diversity of the 1000 hits. To do that we used dise_select.py, first 100 compounds were used as seed and the compounds come after 100 comparing with fingerprint of seed compounds. and if a compound is considered distinct from the 100 seed compounds based on fingerprint similarity, it will be added to the output list until either 1000 compounds are kept or the input list is exhausted








