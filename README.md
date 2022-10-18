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

From left: Original High Resolution DTM image (upsampled to 512), Low resolution image (512 downsampled by 4), Generated Image

![Figure 1 - Epoch One](https://user-images.githubusercontent.com/26202037/192791012-03eb01da-6815-4458-8407-dae8ea374804.png)
*Figure 1. Epoch one*

![Figure 2 - Epoch forty-four](https://user-images.githubusercontent.com/26202037/192792271-232263a2-39e3-40be-83dd-7309cb0a7ef3.png)
*Figure 2. Epoch forty-four*

![Figure 3 - Epoch Eighty-nine](https://user-images.githubusercontent.com/26202037/192792313-7aaf1e45-3a87-4480-9a38-ca762e7fda96.png)
*Figure 3. Epoch eighty-nine*

Consequently, better results are invariably produced by increasing the epoch count. However, this adds considerable time to the processing chain. Within the paper by Demiray et al. 2020 (https://arxiv.org/pdf/2004.04788.pdf), they showcase examples utilising epoch numbers in excess of a thousand to produce their high-resolution DEM.

### Initial suggestions for improvements

1. Locate through literature and confirm the most appropriate loss function to use that is applicable to the type of the input DTM dataset.
2. Consider adding noise to the input dataset after the generator has spooled up.
3. Experiment to locate the optimum initial start parameters - i.e., learning rate, decay rate... etc.

#### III. Optimal Parameters
A learning rate of 0.0002 has a noticable difference over the standard Pytorch 0.00008 value. The end result for a higher learning rate would best be described as more 'aggressive'.

![Learning rate 0.00008](https://user-images.githubusercontent.com/26202037/192984644-d6a87be7-efab-4d7e-a4a2-4c8162f01d59.png)

*Figure 4. Epoch 94 for learning rate 0.00008*

![Learning rate 0.0002](https://user-images.githubusercontent.com/26202037/192985235-5f58671b-d6ad-4a80-88b3-f2f0fb34af06.png)

*Figure 5. Epoch 94 for learning rate 0.0002*





### Example of 'end goal' for the GAN processor

Please see this paper for what would be an ideal end. Resolving through to upsample from 4x4 to 1024x1024.

https://arxiv.org/pdf/1903.06048.pdf
