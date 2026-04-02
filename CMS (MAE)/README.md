# CMS (MAE)

## Overview

This folder contains notebooks, model weights, and sample data for experiments using Masked Autoencoder (MAE) pretraining and finetuning with a Linear-Attention Vision Transformer on the CMS dataset (CERN medical/physics images). The materials include pretraining, finetuning, inference notebooks, a sample raw image array, and a pretrained/finetuned model checkpoint.

## Contents

- Creating_Image_.ipynb — Notebook used to create or preprocess image examples used in the experiments.
- MAE-CERN(pretrian).ipynb — Notebook for MAE pretraining on CERN/CMS data.
- Finetune_CMS_(MAE)_dup.ipynb — Notebook for finetuning the MAE-pretrained model for classification tasks (duplicate copy present).
- inference.ipynb — Notebook demonstrating how to run inference with the trained model on sample images.
- best_mass_classifier_finetune_linearvit_dup.pth — Saved PyTorch model weights (finetuned classifier).
- raw_image_3459.npy — Example raw image saved as a NumPy array to test preprocessing and inference.
- checkpoints/ — Directory intended to store intermediate training checkpoints.
- .ipynb_checkpoints/ — Jupyter checkpoint metadata.

## Requirements

- Python 3.8+ recommended
- PyTorch (version compatible with saved checkpoint)
- torchvision
- timm (if used by the model implementation)
- numpy
- matplotlib
- jupyter / JupyterLab or Google Colab to run notebooks

## Running the notebooks

1. Open the notebooks in Jupyter or upload to Google Colab.
2. Make sure you have the required dependencies installed (pip install torch torchvision timm numpy matplotlib).
3. Update file paths in the notebooks if your working directory differs from the repository root.

## Loading the finetuned model (example)

Use the following snippet in a Python cell to load the saved PyTorch weights and run inference (adapt the model class import to your implementation):

```python
from pathlib import Path
import torch

checkpoint_path = Path("CMS (MAE)") / "best_mass_classifier_finetune_linearvit_dup.pth"
ckpt = torch.load(checkpoint_path, map_location='cpu')
# model = YourModelClass(...)  # instantiate your model architecture
# model.load_state_dict(ckpt['model_state_dict'] if 'model_state_dict' in ckpt else ckpt)
# model.eval()
```

## Using the sample image

The file raw_image_3459.npy is a small example NumPy array you can use to test preprocessing and inference pipelines. Load it with:

```python
import numpy as np
img = np.load("CMS (MAE)/raw_image_3459.npy")
```

## Notes

- The repository contains a duplicate finetune notebook (Finetune_CMS_(MAE)_dup.ipynb). Keep or remove duplicates as desired.
- The pretrained/finetuned checkpoint file is relatively large — avoid committing additional large files unless necessary. Consider using Git LFS for large binaries.
- Check the root repository LICENSE for licensing terms that apply to files in this folder.

## Contact

For questions about these experiments or files, open an issue in the repository or contact the maintainer (rahulkate173).