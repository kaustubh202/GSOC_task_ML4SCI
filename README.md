# Quark/Gluon Jet Analysis and Modeling

This repository contains the submission for our three-task project on quark/gluon jet events. We provide Jupyter notebooks and accompanying PDF reports demonstrating our methods, results, and observations for each task.

## Overview

The project addresses three main tasks:
1. **Autoencoder for Quark/Gluon Events**  
   An autoencoder is trained to learn a latent representation of jet images (with three channels: ECAL, HCAL, and Tracks). We provide side‑by‑side comparisons of the original and reconstructed images.

2. **Jets as Graphs**  
   Jet images are converted into graph representations by extracting nonzero pixels as nodes (with spatial coordinates and intensity features) and connecting them via a k‑nearest neighbor (kNN) approach. A Graph Neural Network (GNN) is then used for quark/gluon classification.

3. **Learning the Latent Structure with Diffusion Models**  
   We explored diffusion models to represent and reconstruct jet events. In our experiments:
   - **Normal (Pixel‑Space) Diffusion:** We initially implemented a diffusion model directly in pixel space. However, due to the extreme sparsity and dimness of the images, the results were not satisfactory.
   - **Latent Diffusion:** We then adopted a two‑stage pipeline:
     - A Variational Autoencoder (VAE) with a custom weighted reconstruction loss was trained to compress the images into a latent space.
     - A diffusion model was then trained on these latent representations. The reverse diffusion process generates latent codes, which are decoded back into images.
   We provide notebooks with both approaches, along with visualizations (multiple generation samples per channel).

## Repository Structure
The repository contains two folders, one for the .ipynb files and another for PDF files of the Jupyter notebook. Each folder has 4 files for
1. Common task 1 - Autoencoder training
2. Common task 2 - GNNs for predictions
3. Specific Task - Latent Diffusion training via VAEs

## Key Observations and Results

- **Autoencoder:**  
  The autoencoder was able to learn a latent representation of the three jet channels, though some channels required custom loss weighting to prevent trivial reconstructions.

- **GNN for Jets as Graphs:**  
  Converting images to graphs allowed us to leverage spatial and intensity features for classification, although performance varied across channels.

- **Diffusion Models:**  
  - **Normal Diffusion:** Direct pixel-space diffusion did not perform well due to the extreme sparsity and low brightness of the jets.
  - **Latent Diffusion:** By shifting the diffusion process into the latent space of a VAE with a weighted loss, we achieved more meaningful reconstructions, although there is scope for better results. Visualizations show multiple diffusion generations per channel for qualitative assessment, and quantitative metrics (MSE) were used for evaluation.

## Future Directions

- Further tuning of loss weighting and thresholds.
- Exploration of alternative architectures for both the VAE and the diffusion model.
- Enhanced pre-processing (e.g., gamma correction, histogram equalization) to improve signal-to-noise in the input images.
- Looking for interpretable architectures for the pipeline.
---




