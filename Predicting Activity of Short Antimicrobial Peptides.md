Predicting Activity of Short Antimicrobial Peptides through Physico-chemical Properties of the Whole Protein

Aim: 

To design a random forest model to predict the activity of short antimicrobial peptides by choosing physicochemical properties as the input feature. We also aim to find the most relevant features required to build our model.

Amps: 

Antimicrobial peptides (AMPs) are a short stretch of amino acids, ranging from five to hundred, that occur naturally or can be synthesised. They are a growing class of peptides that play a critical role in immune system function with a wide spectrum of targets, such as, bacteria, viruses and parasites (Bahar AA, 2013). 

Defensin was the first antimicrobial peptide obtained from animals; in 1956, it was isolated from rabbit leukocytes (JG, 1956). AMPs are also present in the lysosomes of human leukocytes (H. I. Zeya, 1963). 

The major role of AMPs is the destruction of lipopolysaccharide layer of the cell membrane in prokaryotes. As this membrane is important for the survival of the microorganism, this attack causes cell lysis and death. Some AMPs have a rapid effect where they kill the target within seconds (al., 2001).

AMPs play a vital role in immunomodulatory response of the body. They gather immune cells, such as, neutrophils and macrophages to the infection site and simulate the release of cytokines and chemokines. They promote antigen-specific immunity by acting on B-lymphocytes indirectly (Guryanova, 2022).

Due to their diverse functions, AMPs are used to develop therapies against microorganisms, especially those that are resistant to drugs.

Role in drug discovery:

AMPs have a broad range of targets and unique mode of action: disruption of cell membrane. This makes them an alternative to antibiotics that target only specific cell proteins and enzymes. In drug discovery, AMPs can be used to develop therapies against antibiotic resistant bacteria (Jiaqi Xuan, 2023). 

Apart from direct cell killing, AMPs also help to modulate immune response by promoting the activity of cells involved in immunity, regulating inflammation, and chemotaxis stimulation (Duarte-Mata DI, 2023). This property renders them suitable to design drugs with more than one property: cell killing and immune response regulation. 

Methodology:

1. Pfeature library was obtained from \_ that we used to calculate our input features.
1. Our data set was obtained from the [paper](https://www.cell.com/molecular-therapy-family/nucleic-acids/fulltext/S2162-2531\(20\)30132-3). Peptide dataset contained 1529 positive AMPs, which means that they have a proven antimicrobial activity, and 1529 negative AMPs which do not have any antimicrobial activity. A snippet of our FASTA file is shown below:

![](Aspose.Words.4a397f8e-b1cf-4815-bb4a-7279a60238c3.001.png)

1. Redundant sequences were removed using CD-HIT with a threshold value of 0.99. The dataset was reduced to 1337 positive AMPs and 1422 negative AMPs.
1. Composition based features were summarized in a table using the [Pfeature Manual](https://webs.iiitd.edu.in/raghava/pfeature/Pfeature_Manual.pdf).

|**Feature class**|**Description**|**Function**|
| :-: | :-: | :-: |
|AAC|Amino acid composition|aac\_wp|
|DPC|Dipeptide composition|dpc\_wp|
|TPC|Tripeptide composition|tpc\_wp|
|ABC|Atom and bond composition|atc\_wp, btc\_wp|
|PCP|Physico-chemical properties|pcp\_wp|
|AAI|Amino acid index composition|aai\_wp|
|RRI|Repetitive Residue Information|rri\_wp|
|DDR|Distance distribution of residues|ddr\_wp|
|PRI|Physico-chemical properties repeat composition|pri\_wp|
|SEP|Shannon entropy|sep\_wp|
|SER|Shannon entropy of residue level|ser\_wp|
|SPC|Shannon entropy of physicochemical property|spc\_wp|
|ACR|Autocorrelation|acr\_wp|
|CTC|Conjoint Triad Calculation|ctc\_wp|
|CTD|Composition enhanced transition distribution|ctd\_wp|
|PAAC|Pseudo amino acid composition|paac\_wp|
|APAAC|Amphiphilic pseudo amino acid composition|apaac\_wp|
|QSO|Quasi sequence order|qos\_wp|
|SOC|Sequence order coupling|soc\_wp|

1. The physicochemical properties (PCP) feature was calculated for the whole protein (pcp\_wp).
1. Both the positive and negative classes were combined and merged with class labels.
1. In data preprocessing stage, features were assigned to the X variable and class was assigned to the Y variable.
1. The random forest model was built, and its accuracy was noted.
1. Feature importance was plotted through Gini index.

Results:

The model accuracy was obtained as 0.6213. Matthews Correlation Coefficient (MCC) is used to provide performance metrics for imbalanced dataset where it provides a balanced measure. The MCC for our model was 0.243 which provides low ability to distinguish between classes. According to the Gini index, PCP\_Z4 was the most important feature in building the model, then came PCP\_Z1, PCP\_Z2 and PCP\_Z3.

The ROC curve obtained shows that the model has AUC score of 0.66, which means that the classifier has the ability of 66% percent to differentiate between the positive and negative values.

The curve also shows that the model performs better than the random guessing.

![](Aspose.Words.4a397f8e-b1cf-4815-bb4a-7279a60238c3.002.png)

Further improvements:

The model needs further improvements by tweaking, changing the algorithm or adjusting hyperparameters.
# References:
1. al., J. M. (2001). Rapid Killing of Streptococcus pneumoniae with a Bacteriophage Cell Wall Hydrolase. *Science294*. doi:10.1126/science.1066869
1. Bahar AA, R. D. (2013). Antimicrobial Peptides. *Pharmaceuticals*. doi:https://doi.org/10.3390/ph6121543
1. Duarte-Mata DI, S.-C. M. (2023). Antimicrobial peptides´ immune modulation role in intracellular bacterial infection. *Front Immunol*. doi:10.3389/fimmu.2023.1119574
1. Guryanova, S. V. (2022). Immunomodulatory and Allergenic Properties of Antimicrobial Peptides. *International journal of molecular sciences*. doi:https://doi.org/10.3390/ijms23052499
1. H. I. Zeya, J. K. (1963). Antibacterial and Enzymic Basic Proteins from Leukocyte Lysosomes: Separation and Identification. *Science142*. doi:10.1126/science.142.3595.1085
1. JG, H. (1956). Phagocytin: a bactericidal substance from polymorphonuclear leucocytes. *J Exp Med.* doi:10.1084/jem.103.5.589
1. Jiaqi Xuan, W. F.-S. (2023). Antimicrobial peptides for combating drug-resistant bacterial infections,. *Drug Resistance Updates,*. doi:https://doi.org/10.1016/j.drup.2023.100954.



