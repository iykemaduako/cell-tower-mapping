
This repository contains all the necessary code to:
- Train an image classifier using [PyTorch](https://pytorch.org/) to detect cell towers in high-resolution satellite imagery
- Explore model's outputs explanations using Gradient Class Activation Maps ([grad-CAM](https://github.com/vickyliin/gradcam_plus_plus-pytorch)) and SHapley Additive exPlanations ([SHAP](https://github.com/slundberg/shap))
- Extract the last feature vectors from the Convolutional Neural Network trained model and cluster them to find underlying cell tower patterns
- Also, it's possible to georeferenciate some outputs to be imported into a Geographic Information System (GIS) for an easy visualization of the spatial data

## cell tower classifier

The classifier will be capable of classify an image in two different categories:

- **cell tower**: image with a cell tower 
- **not_cell tower**: image without a cell tower 

The goal of the [original project](https://github.com/developmentseed/unicef-cell towers/) was to train an image classifier to detect if a cell tower was present in a high-resolution satellite imagery. We migrated the training part of the original code that was done with Keras + Tensorflow to Pytorch. 

## Installation

1. Clone this repository or download it as a zip file
2. Inside the project folder, create a python virtual ennvironment called *venv*

```bash
virtualenv -p /usr/bin/python3 venv
```

3. Activate the virtual environment

```bash
source venv/bin/activate
```

4. Install required python libraries

```bash
pip install -r requirements.txt
```

You are ready to go!

## Usage

### Important notebooks

The scripts below can be used as an interactive Jupyter Notebook using [VScode](https://code.visualstudio.com/docs/python/jupyter-support-py) capabilities.

1. The file `training/cell_classifier_training.py` is a python script that trains the classifier, save the best model and send some information to tensorboard. 
2. The file `explainability/explainable_cell_classifier_gradcam_gbp.py` is a python script that takes the best saved trained model stored in step 1 and explains its outputs using grad-CAM.
3. The file `explainability/explainable_cell_classifier_shap.py` is a python script that takes the best saved trained model stored in step 1 and explains its outputs using SHAP values. 

### Tensorboard

To use Tensorboard and watch the learning curves and the predictions on the test set:

1. Run Tensorboard

```bash
source venv/bin/activate
tensorboard --logdir=training/runs
```

- Note: if you are running this scripts in a remote server and you are connecting through `ssh` you can access tensorboard by port forwarding:

```bash
ssh -N -L 6006:localhost:6006 user@server
```
