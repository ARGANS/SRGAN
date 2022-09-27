# SRGAN - Super Resolution Generative Adversarial Network
### Exploring Generative Adversarial Networks for EO. 
#### Initial commit made 2022-09-27

This is an exploratory investigation into wielding the power of Neural Networks in order to perform super resolution on EO products.

This implementation is constructed using Pytorch.

For information on the potential of this method, please read the following paper:
https://arxiv.org/abs/1609.04802

For further clarification, the code has been adapted from:
https://www.kaggle.com/code/balraj98/single-image-super-resolution-gan-srgan-pytorch

Within the Kaggle code, it was originally devised to perform SRGAN on the CelebA dataset. It has now been slightly modified to accept tri-band EO image products. Within the notebook, one will find a working example utilising an input DTM of Start Bay (tile index: Copernicus_DSM_04_N50_00_W004_00).

The input DTM has been split into 24 constituents, and the GAN interative process performed on one split tile.

