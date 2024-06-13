# What is this?
The ‘Design-Test-Make-Analyze’ paradigm features a combination of different candidate prediction algorithms from structure, oxidation state, to pathway prediction, to improve candidate selection efficiency towards experimental realization. 

- The first step involves a machine learning model[1] to evaluate the synthesizability of the input candidates (e.g. hypothetical ABO3 structures downloaded from the Materials Project). A workstation with RTX- has been used to train this machine learning model. A few hours to one day are required for training (no cross validation). Relevant software package is available at this GitHub page. 
- The second step involves a statistical oxidation state probability model[2] to evaluate the likelihood of a compound to be charge neutral, based on the likelihood of individual elemental states. A workstation with 16-core CPU and 128GB RAM has been used to train this model. A few hours are required for 1 ternary system typically. The software package is available online at https://github.com/maungthway/synthesizability-ranking-filter. 
- The third step involves a data-driven synthesis planning model, aiming at searching for highly selective and thermodynamically spontaneous reaction pathways[3], [4]. The calculation speed depends on the complexity of the phase diagram, which typically takes a few hours for a target ternary candidate. The software package of the reaction network is available online at https://github.com/maungthway/synthesizability-ranking-filter. 
Detailed system requirements and installation guides can be found at respective repositories. 



## How to use the SC model

Please use Python 3.7.7.
To install, just clone the repository. Then install all required packages:

```bash
pip install -r requirement.txt
```

## Usage

You can train and test the ternary SC model by:

```bash
python main.py
```

You can choose to include or exclude FTCP feature set, or use only atomic features by running:

```bash
python main.py --rp include_ftcp
python main.py --rp exclude_ftcp
python main.py --rp atomic
```
You can also use pre-trained compositional model or full crystal representation model to predict SC for compounds:

```bash
python .\predict.py --type formula --crystal CaTiO3
python .\predict.py --type cif --crystal .\data\predict_cif\CaTiO3_mp-4019_conventional_standard.cif
```

## Citations
Synthesizability using Machine Learning on Databases of Existing Inorganic Materials,” ACS Omega, vol. 8, no. 9, pp. 8210–8218, Mar. 2023, doi: 10.1021/acsomega.2c04856.
[2]	M. Thway et al., “Exploring material compositions for synthesis using oxidation states.” arXiv, May 14, 2024. Accessed: May 21, 2024. [Online]. Available: http://arxiv.org/abs/2405.08399
[3]	M. J. McDermott, S. S. Dwaraknath, and K. A. Persson, “A graph-based network for predicting chemical reaction pathways in solid-state materials synthesis,” Nat Commun, vol. 12, no. 1, p. 3097, May 2021, doi: 10.1038/s41467-021-23339-x.
[4]	M. J. McDermott et al., “Assessing Thermodynamic Selectivity of Solid-State Reactions for the Predictive Synthesis of Inorganic Materials,” ACS Cent. Sci., vol. 9, no. 10, pp. 1957–1975, Oct. 2023, doi: 10.1021/acscentsci.3c01051.
