# API for DeepDrugCoder (DDC)

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/pcko1/Deep-Drug-Coder) [![License: GPL v3](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT) [![Python 3.6](https://img.shields.io/badge/python-3.6-yellow.svg)](https://www.python.org/downloads/release/python-367/) [![Open Source Love svg1](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/) [![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

Code for the purposes of [Direct Steering of de novo Molecular Generation using Descriptor Conditional Recurrent Neural Networks (cRNNs)](https://chemrxiv.org/articles/Direct_Steering_of_de_novo_Molecular_Generation_using_Descriptor_Conditional_Recurrent_Neural_Networks_cRNNs_/9860906).

Also part of [A De Novo Molecular Generation Method Using Latent Vector Based Generative Adversarial Network](https://chemrxiv.org/articles/A_De_Novo_Molecular_Generation_Method_Using_Latent_Vector_Based_Generative_Adversarial_Network/8299544).

Currently only GPU version of the model is supported. You need access to a GPU to use it.

*More detailed instructions are to be pushed soon. Please refer to the demo notebooks for usage details.*
___
### Custom Dependencies
- [molvecgen](https://github.com/EBjerrum/molvecgen)

### Installation
- Clone the repo and navigate to it.
- Create a predefined Python3.6 conda environment by `conda env create -f env/ddc_env.yml`. This ensures that you have the correct version of `rdKit` and `cudatoolkit`.
- Run `python setup.py install` to install remaining dependencies and add the package to the Python path.
- Add the environment in the drop-down list of jupyter by `python -m ipykernel install --user --name ddc_env --display-name "ddc_env (python_3.6.7)"`.

### Usage
``` bash
conda activate ddc_env
```
```python
from ddc_pub import ddc_v3 as ddc
```

### API
- `fit()`: Fit a DDC model to the dataset.
- `vectorize()`: Convert a binary RDKit molecule to its One-Hot-Encoded representation.
- `transform()`: Encode a vectorized molecule to its latent representation.
- `predict()`: Decode a latent representation into a SMILES string and calculate its NLL.
- `predict_batch()`: Decode a list of latent representations into SMILES strings and calculate their NLLs.
- `get_smiles_nll()`: Back-calculate the NLL of a known SMILES string to be sampled by the biased decoder.
- `get_smiles_nll_batch()`: Back-calculate the NLLs of a batch of known SMILES strings to be sampled by the biased decoder.
- `summary()`: Display essential architectural parameters.
- `get_graphs()`: Export model graphs to .png files using `pydot` and `graphviz` ([might fail](https://github.com/AppliedDataSciencePartners/DeepReinforcementLearning/issues/3)).
- `save()`: Save the model in a .zip directory.

### Future
- Add support for `tensorflow==2.0.0` and `keras==2.3.0`.
- Add CPU support.

### Issues
Please report all installation / usage issues by opening an [issue](https://github.com/pcko1/Deep-Drug-Coder/issues) at this repo.
