# Interpretability Project
## Setup
To use this template you can generate a Conda environment using `environment.yml` by running
```sh
conda env create -f environment.yml  --name <custom_name>
```
## Dataset
### Pyradiomics
To retrieve train and test set for the pyradiomics features we provide the function `get_radiomics_dataset()` in `data.py`. The function returns both datasets as numpy arrays.
```sh
from data import get_radiomics_dataset
train_data, train_labels, test_data, test_labels = get_radiomics_dataset()
```
### Images
The image train and testsets are provided as pytorch [ImageFolders](https://pytorch.org/vision/main/generated/torchvision.datasets.ImageFolder.html) through `get_img_dataset(transform=None)` in `data.py`. Note that, in order to incorporate data augmentation, you are able to pass a list of [transforms](https://pytorch.org/vision/0.9/transforms.html) to this function.

```sh
from data import get_img_dataset
from torchvision import transforms
transform = [transforms.RandomRotation(90), transforms.RandomHorizontalFlip()]
train_dataset, test_dataset = get_img_dataset(transform)
```

## Baseline
We provide a simple Baseline CNN based on pytorch in `data.py` through `BaselineClf()`. To use it, simply do
```sh
from model import BaselineClf
model = BaselineClf()
```