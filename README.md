# AvantGAN
DCGAN with adaptive discriminator augmentation for small datasets that generates avant-garde fashion in style of Rei Kawakubo; currently trained on pieces hand-traced in Adobe Fresco.

To my knowledge, no one has attempted to make a GAN that creates artistic avant-garde fashion.

## Dataset
A tiny tiny dataset of 27 avant-garde fashion pieces by Rei Kawakubo hand-traced in Adobe Fresco to reduce noise and emphasize important features. Original size: 512x512x3 but resized to 64x64x3 for training.

![Alt_text](sample_data/drawing_sample.png)
*512x512 training samples of hand-traced outfits.*

![Alt_text](sample_data/source_sample.png)
*Raw samples of Rei Kawakubo's avant-garde outfits.*

## Results
<TODO: wandb results>
<TODO: hand-picked results>

## Usage
1. Runs in Kaggle (sorry!) with 1 GPU but can be run locally with minimal changes
2. Change training params and wandb info in class Config

## Architecture/Training Setup
Deep convolutional GAN with basic binary cross entropy loss for the discriminator with following changes:
1. Added leaky ReLU to generator, too
2. AdamW optimizer for both generator and discriminator
Note: Each convolution, in both networks, is followed by batch normalization and a leaky ReLU function, except for the last layer, which uses a tanh function. 
3. Adaptive Discriminator Augmentation (ADA) per https://arxiv.org/abs/2006.06676 (Karras et al. 2020) for small datasets  
    3.1. Augmentations to the real images as per ADA
4. Basic label smoothing determined by SMOOTH in config

## Comparison to other models
<TODO: diffusion results>
<TODO: Stylegan3 results>

## Future Improvements
* increasing dataset size manually and via diffusion generation
* fine-tuning StyleGAN3
* update loss function to e.g. wasserstein loss to decrease mode collapse and improve training stability

### Acknowledgements
https://pytorch.org/tutorials/beginner/dcgan_faces_tutorial.html as base code
