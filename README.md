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
We generated 1000 random transects by traversing [StyleGAN2](https://github.com/NVlabs/stylegan2)'s latent space in controlled semantic directions (please see our paper for more details). We used two discretization levels for each of the three attributes:

1. Skin color (dark and light)
2. Hair Length (long and short/medium)
3. Gender (male and female)

This results in 1000 x 2 x 2 x 2 = 8000 images.

<div align="center"><img src=./images/transect-samples.png></div>

Note that transects may be generated for other attribute combinations. To train your own transects, please refer to our paper.

## Bias and Fairness

While out transects can be designed to mitigate sampling biases that exist in real datasets, they are not immune to biases such as:

1. The images are generated using StyleGAN2, which in turn was trained on the FFHQ dataset. Therefore, our transects will tend to generate appearances and physiognomies characteristic of those found in FFHQ. In addition, attribute combinations that are uncommon or missing in FFHQ may not be feasibly generated. 

2. Human annotators have their own biases, which also vary based on geographical location. We do show in our paper's analyses, however, that our annotators were at fairly consistent with one another.

3. Unmeasured characteristics such as ethnicity and facial structure may be strongly correlated with one of the measured attributes like skin color. This can have potentially unwanted consequences for downstream analyses. Further annotation rounds would be needed to properly account for additional attributes.


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
