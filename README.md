# SRGAN - Super Resolution Generative Adversarial Network
### Exploring Generative Adversarial Networks for EO. 
#### Initial commit made 2022-09-27

This is an exploratory investigation into wielding the power of Neural Networks in order to perform super resolution on EO products.

Super-resolution GAN applies a deep network in combination with an adversary network to produce higher resolution images. As shown above, SRGAN is more appealing to a human with more details compared with the similar design without GAN (SRResNet). During the training, A high-resolution image (HR) is downsampled to a low-resolution image (LR). A GAN generator upsamples LR images to super-resolution images (SR). We use a discriminator to distinguish the HR images and backpropagate the GAN loss to train the discriminator and the generator.

This implementation is constructed using Pytorch.

For information on the potential of this method, please read the following paper:
https://arxiv.org/abs/1609.04802

For further clarification, the code has been adapted from:
https://www.kaggle.com/code/balraj98/single-image-super-resolution-gan-srgan-pytorch

Within the Kaggle code, it was originally devised to perform SRGAN on the CelebA dataset. It has now been slightly modified to accept tri-band EO image products. Within the notebook, one will find a working example utilising an input DTM of Start Bay (tile index: Copernicus_DSM_04_N50_00_W004_00).

The input DTM has been split into 24 constituents, and the GAN interative process performed on one split tile.

