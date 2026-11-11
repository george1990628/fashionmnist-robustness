# FashionMNIST robustness

During my Lumiere research, I tested how learning rates, hidden-layer depth, and noisy images affect a FashionMNIST classifier. I experimented with different combinations of clean and noisy training and test data.

This notebook contains the model, training and testing loops, and accuracy plots used for those experiments.

## Run the notebook

```bash
python -m pip install -r requirements.txt
```

Open [the notebook](notebooks/fashionmnist_experiments.ipynb) in Jupyter or Colab and run the cells in order. It downloads FashionMNIST through TorchVision. The default runs for 50 epochs on CPU. You can lower the epoch count to try it out first.

| Setting | Default |
| --- | --- |
| Model | Four hidden layers with 512 units each, ReLU, and ten output logits |
| Optimizer | SGD with a learning rate of 0.001 |
| Batch size | 64 |
| Epochs | 50 |
| Noise | Uniform noise from [0, 0.5), added to the image without clipping |
| Training and testing | Clean images for both |

Set `TRAIN_WITH_NOISE` and `TEST_WITH_NOISE` to choose the input combination. Edit `NeuralNetwork` to change the number of hidden layers and the training cell to change the learning rate. The notebook runs one configuration at a time.

## Notes on the experiments

Noise is sampled again each time an image is loaded. The original notebook does not include a full results table, fixed corruption set, or repeated-seed comparison. It also does not set aside a validation set for tuning. If you extend it, use a separate validation set to choose hyperparameters before evaluating on the test set.

## References

I built on the [PyTorch Learn the Basics tutorials](https://docs.pytorch.org/tutorials/beginner/basics/intro.html) for the dataset loading, model setup, and training loops. The tutorial's [BSD license](LICENSES/PYTORCH_TUTORIALS.txt) is included. My experiments focused on changing the hidden layers, learning rates, and input noise.

FashionMNIST comes from its original authors and is downloaded separately.
