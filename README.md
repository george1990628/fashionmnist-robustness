# FashionMNIST robustness

**Status: historical Lumiere Research project; source notebook prepared for public sharing.**

Experiments with a multilayer perceptron on FashionMNIST, examining architecture and learning-rate choices alongside clean and corrupted images. This repository contains the original implemented workflow with redundant tutorial warm-ups and saved outputs removed.

## Run

```bash
python -m pip install -r requirements.txt
```

Open [the experiment notebook](notebooks/fashionmnist_experiments.ipynb) in Jupyter or Colab and run it in order. FashionMNIST downloads through TorchVision. The original default runs 50 epochs on CPU; reduce the epoch count for a software check.

| Setting | Included default |
| --- | --- |
| Model | Four hidden layers, 512 units each, ReLU, ten output logits |
| Optimizer | SGD, learning rate 0.001 |
| Batch size | 64 |
| Epochs | 50 |
| Noise | Additive uniform [0, 0.5), redrawn on sample access, no clipping |
| Selected run | Clean training / clean testing |

Set `TRAIN_WITH_NOISE` and `TEST_WITH_NOISE` to choose the clean/noisy input combination. Change hidden-layer depth in `NeuralNetwork` and learning rate in the training cell. These are manual experiment controls; no automated sweep is claimed.

## What the notebook establishes

The code defines clean and noisy loaders, a configurable-by-editing MLP, training/testing loops, and accuracy curves. The original notebook does not include a complete experiment table, a pinned environment, a fixed corruption set, or repeated-seed results. No headline accuracy or robustness improvement is asserted from the uploaded output. Model selection should use a separate validation set before final test evaluation.

This packaging step checked notebook structure and code syntax. Full training was not rerun.

## Attribution

Dataset/model/training scaffolding is adapted from the [PyTorch Learn the Basics tutorials](https://docs.pytorch.org/tutorials/beginner/basics/intro.html), especially datasets, model building, and optimization. Their [BSD license](LICENSES/PYTORCH_TUTORIALS.txt) is preserved. My research work used that foundation to experiment with hidden layers, learning rates, and noisy images; it is not a claim to have originated the tutorial architecture.

FashionMNIST is provided by its original authors; data is downloaded separately. No new blanket license is assigned to third-party material.
