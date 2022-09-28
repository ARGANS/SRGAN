# SRGAN - Super Resolution Generative Adversarial Network
### Exploring Generative Adversarial Networks for EO. 
#### Initial commit made 2022-09-27

This is an exploratory investigation into wielding the power of Neural Networks in order to perform super resolution on EO products.

Super-resolution GAN applies a deep network in combination with an adversary network to produce higher resolution images. During the training, A high-resolution image (HR) is downsampled to a low-resolution image (LR). A GAN generator upsamples LR images to super-resolution images (SR). We use a discriminator to distinguish the HR images and backpropagate the GAN loss to train the discriminator and the generator.

This implementation is constructed using Pytorch.

For information on the potential of this method, please read the following paper:
https://arxiv.org/abs/1609.04802

For further clarification, the code has been adapted from:
https://www.kaggle.com/code/balraj98/single-image-super-resolution-gan-srgan-pytorch

Within the Kaggle code, it was originally devised to perform SRGAN on the CelebA dataset. It has now been slightly modified to accept tri-band EO image products. Within the notebook, one will find a working example utilising an input DTM of Start Bay (tile index: Copernicus_DSM_04_N50_00_W004_00).

The input DTM has been split into 24 constituents, and the GAN interative process performed on one split tile.

### Examples of the iterative GAN procedure

The following figures showcase the evolution of the iterative learning capability of GANs, applied to attempting to super-resolve a Digital Terrain Model (DTM). The original DTM was split into 24 sub rasters of 1500x2250 pixels. Then, on the first split raster (0_0), the raster was fractured again into 54 further tiles of 256x256 pixels.

With the following settings applied:
Epochs = 100
Batch size = 16
Learning rate = 0.00008
Hr width and height = 512 (upsampling by 2)

![image](https://user-images.githubusercontent.com/26202037/192789924-39050ed1-f8d5-460a-809a-91a5c6f069da.png)
#### Figure 1. Epoch one

![image](https://user-images.githubusercontent.com/26202037/192790027-79c6158a-3714-4bab-b829-5f3c095fb314.png)
#### Figure 2. Epoch forty-four

![image](https://user-images.githubusercontent.com/26202037/192790167-840016d8-0590-4b2e-8eef-d61c30917e23.png)
#### Figure 3. Epoch Eighty-nine


