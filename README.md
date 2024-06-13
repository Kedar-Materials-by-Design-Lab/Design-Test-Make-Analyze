# What is this?
The ‘Design-Test-Make-Analyze’ paradigm features a combination of different candidate prediction algorithms from structure, oxidation state, to pathway prediction, to improve candidate selection efficiency towards experimental realization. 

- The first step involves a machine learning model[1] to evaluate the synthesizability of the input candidates (e.g. hypothetical ABO3 structures downloaded from the Materials Project). A workstation with RTX- has been used to train this machine learning model. A few hours to one day are required for training (no cross validation). Relevant software package is available at this GitHub page. 
- The second step involves a statistical oxidation state probability model[2] to evaluate the likelihood of a compound to be charge neutral, based on the likelihood of individual elemental states. A workstation with 16-core CPU and 128GB RAM has been used to train this model. A few hours are required for 1 ternary system typically. The software package is available online at https://github.com/maungthway/synthesizability-ranking-filter. 
- The third step involves a data-driven synthesis planning model, aiming at searching for highly selective and thermodynamically spontaneous reaction pathways[3], [4]. The calculation speed depends on the complexity of the phase diagram, which typically takes a few hours for a target ternary candidate. The software package of the reaction network is available online at https://github.com/maungthway/synthesizability-ranking-filter. 
Detailed system requirements and installation guides can be found at respective repositories. 


# SC_model

SC Model is an inorganic material crystal materials synthesizability score prediction model

## Installation

Please use Python 3.7.7 to run the model.

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

   

## Authors
The code was primarily written by Ruiming Zhu, under supervision of Prof. Kedar Hippalgaonkar.
