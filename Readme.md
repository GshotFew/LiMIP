
## Dependencies
To install SCIP and other dependencies, follow the instructions of https://github.com/ds4dm/learn2branch/blob/master/INSTALL.md

 We use the following python packages for python version 3.6.13.
```sh
torch==1.9.0+cu111
torch-geometric==2.0.3
torch-scatter==2.0.9
torch-sparse==0.6.12
torchaudio==0.9.0
torchvision==0.10.0+cu111
scipy==1.5.2
numpy==1.18.1
networkx==2.4
Cython==0.29.13
PySCIPOpt==2.1.5
scikit-learn==0.20.2
```

## Generating training instances
* To generate dataset for SC_0.05
* ` python scripts/Cont_generate_instances.py setcover_densize --density 0.05`

 Similary can be done for other datasets
* `python scripts/Cont_generate_instances.py setcover_densize --density 0.2`
* `python scripts/Cont_generate_instances.py indset --affinity 4 --indnodes 750` 
`

## Generating training samples
* ` python Cont_generate_dataset.py setcover_densize --density 0.05 -j 20`


## Training
To train for sequence [SetCover_0.05,SetCover_0.075, SetCover_0.1,   SetCover_0.125, SetCover_0.15, SetCover_0.2]


` python3 -u train.py -g 1 --data_path data/samples_1.0/ --prob_seq setcover_densize_0.05-setcover_densize_0.075-setcover_densize_0.1-setcover_densize_0.125-setcover_densize_0.15-setcover_densize_0.2 `


The prob_seq consists of different tasks separated by `-`

# Evaluation

To evaluate the model on test instance of setcover with density 0.05, run the following

* ` python3 -u evaluate.py setcover_densize --g 1  --path_load trained_models/MODEL_setcover_densize_0.05_setcover_densize_0.1_setcover_densize_0.15_setcover_densize_0.2/GAT_baseline_torch/0/ --density 0.05 --epoch_load checkpoint.pkl `


