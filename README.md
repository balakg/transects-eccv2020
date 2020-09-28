# Transects-ECCV2020

## Overview
This is a dataset of real and synthetic hukan faces along with attribute annotations acquired through Amazon Mechanical Turk studies. We annotated seven attributes per face image: age, facial hair, gender, hair length, makeup, skin color, and smiling. For synthetic images, we also annotated 'uncanniness' to prune badly generated examples. 

We annotated each attribute using 4-6 semantic levels. You can find our Mechanical Turk survey layouts with these levels in 'turk-layouts'. 

The synthetic faces, which we call 'transects', vary faces along skin color, hair length and gender attributes while attempting to hold other attributes constant. We used this data to conduct bias analyses of gender classifiers with respect to these factors. 
 
If you use this dataset, please cite our paper:

> **Towards causal benchmarking of bias in face analysis algorithms**<br>
> Guha Balakrishnan, Yuanjun Xiong, Wei Xia, Pietro Perona<br>
> ECCV 2020<br>
> https://arxiv.org/abs/2007.06570


## Repository Contents

./data: Images and raw Turk responses for four datasets

1. 3000 random CelebA-hq images
2. 3000 random Flickr-Faces-HQ (FFHQ) images
3. 5000 randomly generated synthetic images from StyleGAN2
4. 8000 synthetic transect images. 

./read-sagemaker-responses: reads sagemaker annotator responses into data files for easy analysis

./make-violin-plots.ipynb: Plots attribute distributions for each dataset like the violin plots found in the ECCV 2020 paper.


