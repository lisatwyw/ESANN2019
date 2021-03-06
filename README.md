# ESANN2019

**Updated Repo [TheRensselaerIDEA/synthetic_data](https://github.com/TheRensselaerIDEA/synthetic_data)**

Supplemental Material for the ESANN 2019 Submission "Preserving privacy using synthetic data models and applications in health informatics education". This includes a supplemental section to the paper located at `supplemental_material.pdf`. There is also code for all of the generative methods and metrics.

## Generative Methods Code

### Gaussian Multivariate

The code for this method is located in the `generators/gaussian_multivariate.py` file. It uses the sci-kit learn Gaussian mixture method.

### HealthGAN (WGAN)

The code for this method is located in the `generators/wgan.py` file. This method uses tensorflow to create the GAN. It is based on the methods from the paper "Improved Training of Wasserstein GANs" and the repository from the author [https://github.com/igul222/improved_wgan_training](https://github.com/igul222/improved_wgan_training).

#### Architecture

The architecture of the HealthGAN is as follows

- Generator
  - Input: 100 nodes of noise from the latent space of a normal distribution
  - Dense Layer of 2 x number of features in the data nodes
    - Rectified linear unit activation
  - Dense Layer of 1.5 x number of features in the data nodes
    - Rectified linear unit activation
  - Dense Layer of number of features of the data nodes
    - Sigmoid activation
- Discriminator
  - Input: number of features in the data
  - Dense Layer of 64 nodes
    - Leaky rectified linear unit activation
  - Dense Layer of 128 nodes
    - Leaky rectified linear unit activation
  - Dense Layer of 256 nodes
    - Leaky rectified linear unit activation
  - Dense Layer of 1 node
    - No activation function
- Batch size is computed to be the size of the training data divided by the number of critic iterations

### Additive Noise Model

The code for this method is located in the `generators/additive_noise_model.py` file. It uses the random forest classifiers from sci-kit learn.

### Parzen Windows

The code for this method is located in the `generators/parzen_windows.py` file. It uses the kernel density method from sci-kit learn.

### Copy Original Data

This method just copies the original data and therefore there isn't any code included.

### Privacy-preserving Data Obfuscation

This method was done using the open source software [ARX](https://arx.deidentifier.org/). 

### Synthetic Data Vault Converter

The `generators/sdv_converter.py` file contains code to convert the data into values from 0 to 1 as described in the supplemental material. This is used for the Wasserstein GAN method to ensure the values generated are reasonable.

## Metrics

### Adversarial Accuracy

The nearest neighbor adversarial accuracy is calculated using the `metrics/nn_adversarial_accuracy.py` file.

### Utility

The nearest neighbor utility is calculated using the `metrics/nn_utility.py` file.
