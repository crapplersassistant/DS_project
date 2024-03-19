# Python for Data Science (DS223) Final Project
##### Working with Big Data: TCGA Pan-Cancer Atlas
***The objective of this project is to work with a large gene expression dataset.  To clean the data and produce a dataset ready for downstream analysis.***

### Steps from the Notebook...

### Final Project PanCancer Atlas
***The Cancer Genome Atlas Pan-Cancer Atlas was a program initiated to categorize 33 cancer types from over 10,000 samples.  Much work has been done in this collaborative effort using a variety of molecular markers - mutations, aneuploidy, copy number, gene expression, methylations, proteomics etc.  In a flagship article on the Cell-of-Origin for the Pan-Cancer Atlas, researchers identified homogenous cancer specific groups based on characteristics associated with cell-of-origin and tissue-specific markers as well as cancer types that had considerable overlap across organ systems. The ability to classify tumors by tissue of origin and to target expression unique to tissue-specific tumors has the potential to enhance site-specific targeting of tumors if novel markers can be identified.  While it is widely accepted that there are "oncogenic" pathways that repeatedly appear across cancer types, there is potentially a diverse landscape of pathways that may be driving or sustaining tumor growth within a given tissue.  Using RNA sequencing data collected and batch corrected from the large sample size and breadth of cancers in the Pan-Cancer Atlas, can we identify organ-specific markers that lend credence to the plausibility that tissues do in fact hold clues to site-specifc treatment options?***

### We will need to install and import several libraries.
Activate a virtual environment.

***Using pandas for dataframe manipulation, matplotlib for visualization, numpy for mathematical manipulation and array operations, sklearn and pytorch for ML modeling.  Additionally, we will need to use the library rpy2 which is a python wrapper of the edgeR package used in gene expression normalization***


##### Load the datasets
***We will load the gene expression data as well as the paired clinical data.***
**[PANCANCER DATA REPO](https://xenabrowser.net/datapages/?cohort=TCGA%20Pan-Cancer%20(PANCAN)&removeHub=https%3A%2F%2Fxena.treehouse.gi.ucsc.edu%3A443)**

### Inspect the gene expression data and generate some helper functions.

***We want to see what the raw data looks like so we can perform the appropriate munging steps.***

##### The PanCancer Atlas dataset requires several preprocessing steps to perform meaningful analysis.  
***There are several tumor sample types denoted in the sample ID.  For example, the primary site of the tumor is denoted in the string index 14-15.  Additionally, the string vector for gene IDs contains both hardware ID and Gene names.  Finally, when dealing with a dataset that is composed of expression level data, it is necessary to adjust the counts for the depth of the sequencing in a sample relative to all other samples, followed by log transformation, and gene-wise scaling to Z-scores.***

##### What measures need to be taken to homogenize the coverage?

***Based on the inspection of the dataset, summary statistics of the numerical columns indicate null values for certain samples as well as negative values.  For the sequencing count normalization across samples, we can set the null values and negative values to zero.  ***

##### Run Gene Expression Normalization with Python wrapper of edgeR
***In order to run this step we needed to clean the gene expression matrix of null and negative values.  Recall:  we are adjusting counts across samples based on a geometric mean normalization factor.***



##### Notes and Issues...
***I had many challenges with this project.  At first I thought about doing some image analysis, but had competency issues when it came to more complex imaging ie medical.  My second project idea was to build a sql database for all the datasets provided on Xena - UCSC's cancer dataset repo - using their API.  However, I ran into issues trying to use the API. Finally, I settled on a project working with the PanCancer Altas from the TCGA project.  It is a large transcriptomic dataset composed of 33 tumors and over 11,000 samples.  After cleaning, this was matrix with dimensions ~ 20530x9715.  Ultimately very slow and compute heavy which limited my ability to do more complex analysis in a reasonable amount of time.***