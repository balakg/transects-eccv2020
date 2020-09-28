# Transects-ECCV2020

## Overview
This is a dataset of real and synthetic human faces along with attribute annotations acquired through Amazon Mechanical Turk experiments. The synthetic **transects** in this repository vary faces along skin color, hair length and gender attributes while attempting to hold other attributes constant. Unlike datasets collected ''in the wild,'' transects offer better control and balance over facial attributes, allowing for [***experimental rather than observational***](https://en.wikipedia.org/wiki/Observational_study) analyses of downstream face analysis systems or human observers.  

We annotated seven attributes per face: age, facial hair, gender, hair length, makeup, skin color, and smiling. For the transect images, we also annotated 'uncanniness' to help prune out badly generated examples for analysis. We used 4-6 semantic levels per attribute -- you can find our Mechanical Turk survey layouts explaining these levels in 'turk-layouts.' 

If you use this dataset, please cite our paper:

> **Towards causal benchmarking of bias in face analysis algorithms**<br>
> Guha Balakrishnan, Yuanjun Xiong, Wei Xia, Pietro Perona<br>
> ECCV 2020<br>
> https://arxiv.org/abs/2007.06570

## Transects
We generated our transect images by traversing [StyleGAN2](https://github.com/NVlabs/stylegan2)'s latent space in controlled semantic directions (plese see our paper for more details). We generated 1000 random 'seed' latent codes, and varied them along two discretization levels for three attributes:

1. Skin color (dark and light)
2. Hair Length (long and short/medium)
3. Gender (male and female)

This results in 1000 x 2 x 2 x 2 = 8000 images.

<div align="center"><img src=./images/transect-samples.png></div>

## Bias and Fairness

Make a note about how there are still biases of the generated images.

## Repository Contents

./turk-layouts: Mechanical turk survey screenshots. Contains our instructions to Turkers as well as the semantic levels of attributes and their descriptions.

./data: Images and Mechanical Turk responses for four datasets:

1. 3000 random CelebA-HQ images
2. 3000 random [FFHQ](https://github.com/NVlabs/ffhq-dataset) images
3. 5000 randomly generated synthetic images from [StyleGAN2](https://github.com/NVlabs/stylegan2)
4. 8000 synthetic transect images

read-sagemaker-responses.ipynb: Reads sagemaker annotator responses and saves them into pickled numpy files for easy analysis.

make-violin-plots.ipynb: Plots attribute distributions for each dataset similar to the violin plots found in our ECCV 2020 paper:

<div align="center"><img src=./images/dataset-comparison.png></div>
