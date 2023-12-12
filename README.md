
# Ovarian Cancer Subtype Classification and Outlier Detection

A solution for Kaggle Competition, training auto-encoder for outlier detection and multiple deep learning models for cancer subtype classification. 

By building the integrated model of auto-encoder and classifion neural network, successfully identify potential outliers and subtypes.

<img width="1520" alt="OCEAN-Optional-Figure" src="https://github.com/manyuzhang1996/Ovarian-Cancer-Subtype-Classification-and-Outlier-Detection/assets/111943220/cdcaa810-0120-46ea-9710-3a3250ff507a">

## Tech Stack
* Python
* TensorFlow
* VGG19
* EfficientNetV2S
* ResNet50
* Auto-encoder


## Data Source
<img width="1520" alt="OCEAN-Optional-Figure" src="https://github.com/manyuzhang1996/Ovarian-Cancer-Subtype-Classification-and-Outlier-Detection/assets/111943220/fbeb09a2-6a21-4bb6-9318-7eea94899650">

**train/test_images**: A folder containing the relevant images. There are two categories of images: whole slide images (WSI) and tissue microarray (TMA). Whole slide images are at 20x magnification and can be quite large. The TMAs are smaller (roughly 4,000x4,000 pixels) but at 40x magnification.

The test set contains images from different source hospitals than the train set, with the largest area images almost 100,000 x 50,000 pixels. We strongly recommend taking an expansive approach to thinking about the scenarios your error handling should manage, including differences in image dimensions, quality, slide staining techniques, and more. Expect roughly 2,000 images in the test set, the majority of which are TMAs. 

The total size is 550 GB so simply loading the data will be time consuming. Be warned that the test set was specifically constructed to assess how well models generalize.

**train/test.csv**: Labels for the train set.

image_id - A unique ID code for each image.

label - The target class. One of these subtypes of ovarian cancer: CC, EC, HGSC, LGSC, MC, Other. The Other class is not present in the training set; identifying outliers is one of the challenges of this competition. Only available for the train set.

image_width - The image width in pixels.

image_height - The image height in pixels.

is_tma - True if the slide is a tissue microarray. Only available for the train set.

**train/test_thumbnails**: A folder containing smaller .png copies of the whole slide images. Thumbnails are not provided for TMAs.

## Problem formation and solution
_**1.Subtype Classification:**_

  Subtype classification is a multi-class (5-classes) classification problem.
  
  **Difficulties**:
  1) Number of images is less
  2) Class distribution is imbalanced
  3) Image size is too large, high resolution
     
  **Solution**: 
  Train multi-class classification neural network based on balanced and processed images.

_**2.Outlier Detection:**_

Outlier detection is predicting if a given image is one of the subtypes or not.

**Difficulties**:
1) No “outlier” image sample given
2) No clear model selection guidance

**Solution**: 
Train autoencoder to learn non-outliers’ pattern and predict outliers, no need of “outlier” image.

 
## Project Architecture

1. Process the image data
2. Balance the data distribution among subtypes while augmenting them
3. Build auto-encoder to differentiate outliers and known subtypes
4. Fine-tuned VGG19-based, ResNet50-based and EfficientNetV2S-based model to predict subtypes
5. Integrate auto-encoder with best performing classification model to predict test images

<img width="1520" alt="OCEAN-Optional-Figure" src="https://github.com/manyuzhang1996/Ovarian-Cancer-Subtype-Classification-and-Outlier-Detection/assets/111943220/cdcaa810-0120-46ea-9710-3a3250ff507a">




## Run Locally

1. Clone the project

```bash
git clone https://github.com/manyuzhang1996/Ovarian-Cancer-Subtype-Classification-and-Outlier-Detection.git
```

2. Navigate to the project directory
```bash
cd Ovarian-Cancer-Subtype-Classification-and-Outlier-Detection
```

## Contact Authors
Manyu Zhang (zhangmanyuzmy@gmail.com)

Hui Yun

Richard Lu

Jason Djuandy
