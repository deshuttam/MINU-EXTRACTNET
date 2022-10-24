# MINU-EXTRACTNET: Automatic Latent Fingerprint Feature Extraction System Using Deep Convolutional Neural Network

By Uttam Deshpande et. al.,




a simple Deep Convolutional
Neural Network (DCNN) model called “Minu-ExtractNet”. Firstly, latent fingerprint pre-processing is implemented using a Convolutional Neural Network (CNN)
model called “Pre-ProcessNet”. This model enhances the quality of the latent and
produces the orientation information along with different segmentation masks.
Secondly, pre-processed information is then used to extract the minutiae feature
points using another CNN model called “ExtractNet”. This feature extractor model
performs the image quality assessment to determine the threshold value to filter
out spurious minutiae points. A dynamic thresholding algorithm is developed to
achieve this goal.
