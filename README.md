# MINU-EXTRACTNET: Automatic Latent Fingerprint Feature Extraction System Using Deep Convolutional Neural Network

By Uttam Deshpande et. al.,







A Deep Convolutional Neural Network  (DCNN) model called “Minu-ExtractNet” performs pre-processing using “Pre-ProcessNet”. This model enhances the quality of the latent and produces the orientation information along with different segmentation masks. Later, pre-processed information is then used to extract the minutiae feature points using another CNN model called “ExtractNet”. This feature extractor model performs the image quality assessment to determine the threshold value to filter out spurious minutiae points. A dynamic thresholding algorithm is developed to achieve this goal.
To refer to this paper: https://doi.org/10.1007/978-981-16-0507-9_5

### Pre-ProcessNet: 
A residual learning-based CNN model. It is a Robust image enhancement model that takes input as a fingerprint image and enhances the image for further operation. This model also generates orientation estimates and segmentation masks as output.

![image](https://user-images.githubusercontent.com/107185323/197522777-6b5991b8-8298-4074-9994-980655d3377f.png)

Due to the lack of ground truth dataset, we generate weak labels from the approach used by Nguyen et.al. [5]. Pre-ProcessNet uses minutiae location and orientation generated from this method. These weak labels are used for training segmentation and orientation modules

![image](https://user-images.githubusercontent.com/107185323/197522845-bf57054a-ebc2-4799-955f-1075693f959c.png)

### ExtractNet: 
It’s a CNN based minutiae extractor model that takes the output of the robust image enhancement model as input and extracts feature points from the fingerprint image. Feature points could be ridge ending, bifurcation, core points, etc. The model gives output feature points as X and Y coordinates, the orientation angle θ, and the confidence score of each feature point.

![image](https://user-images.githubusercontent.com/107185323/197522897-1a7ab288-8cb3-4d25-bace-a15df0f09980.png)

The confidence level of minutiae points as predicted by ExtractNet directly depends upon the quality of the image. ExtractNet extracts both true and spurious points that have to be filtered before passing it to further operation. The presence of a significant number of spurious points or lost true minutiae points affects the accuracy of the future matching process. Hence, an efficient filtering process has to be implemented. 

![image](https://user-images.githubusercontent.com/107185323/197522970-d2ac88c0-5261-4e6f-ad6c-53cedf91571f.png)

A static thresholding mechanism is applied then true minutiae points will be filtered out. This is because the degraded image will detect a true minutia point with a lower confidence level. Hence to overcome these drawbacks we propose a dynamic thresholding algorithm.

![image](https://user-images.githubusercontent.com/107185323/197523031-ce380111-a7fe-4345-81fa-a9a181d10f76.png)

The precision-recall curves for FVC 2004 and NIST SD27 database by different state-of-art work are shown in Fig. 6. The obtained results are found similar to the ground truth minutiae of FVC 2004 and NIST SD27 databases. The proposed work can work well with partial fingerprint images and images with noisy backgrounds.

![image](https://user-images.githubusercontent.com/107185323/197523104-714b2ffd-d315-4b57-a524-2fc9121f99bd.png)



The repository includes:

* Source code of MINU-EXTRACTNET.
* Training code for MINU-EXTRACTNET.
* Pre-trained weights for MINU-EXTRACTNET, FineNet and CoarseNet.
* Jupyter notebooks to visualize the minutiae extraction pipeline at every step.

### Citing
@inproceedings{10.1007/978-981-16-0507-9_5, 
Author={Deshpande, Uttam U. Deshpande},
Editor={Santosh, K. C. and Gawali, Bharti},
Title={MINU-EXTRACTNET: Automatic Latent Fingerprint Feature Extraction System Using Deep Convolutional Neural Network},
Book Title={Recent Trends in Image Processing and Pattern Recognition},
Year={2021},
Publisher={Springer Singapore},
Address={Singapore},
Pages={44--56},
DOI={ https://doi.org/10.1007/978-981-16-0507-9_5 },
ISBN={978-981-16-0507-9},
}


### Contents
1. Requirements: software
2. Installation
3. Demo
4. Usage

## Requirements: software
`Python 2.7`, `Tensorflow 1.7.0`, `Keras 2.1.6`.

## Installation
To make life easier, use Anaconda for easy installation. Version using pip is similar.
`conda install cv2, numpy, scipy, matplotlib, pydot, graphviz`

Download models and put into Models folder.

* MINU-EXTRACTNET: https://drive.google.com/file/d/1e-fvLhwvw8Sg1uVkM6oBT6QncWZgloap/view?usp=sharing

* CoarseNet: https://drive.google.com/file/d/1bU3T-XQRlKy6C77e5eD-DOD_QlNlAIjR/view?usp=sharing

* FineNet: https://drive.google.com/file/d/1rQw6hs-3hv_7WqJQ8ZYhJhi4laa-9qbY/view?usp=sharing

## Usage
# MINU-EXTRACTNET
`MINU-EXTRACTNET.ipynb` can be called to generate minutiae as well as masks and orientation.


