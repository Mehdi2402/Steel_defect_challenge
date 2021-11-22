# Severstal: Steel Defect Detection (Kaggle challenge)

## Challenge presentation :
In this competition,the goal is to help engineers improve the algorithm by localizing and classifying surface defects on a steel sheet.


We are provided 12600 steel sheet images, and the goal is to predict the location and type of defects found in steel manufacturing. Each image may have no defects, a defect of a single class, or defects of multiple classes.

An example of what a steel sheet image looks like :

![example](https://user-images.githubusercontent.com/56029953/142926784-2d794fb4-20b8-4ded-9b14-f0cc25a4f881.jpg)


The labels given in this challenge are, for each Image Id :
* The Defect Class : **ClassId** : [1,2,3,4]
* The defect region in a run-length encoding (rle) : **EncodedPixels**

## EDA and data augmentation :
### Exploring data :
### Data augmentation :
For first data augmentation I used Brightness, Contrast, Saturation. No change in mask location were needed for these augmentations.
The second augmentation was : Vertical flip, Horizontal Flip and 180° rotation. 180° rotaion was used instead of a random degree to keep the entire image in frame not to lose the defect region.
The same changes had to be applies to mask region to be compliant with image change.
**Here are some examples of augmentation :**
![augmentation_vhf_rot](https://user-images.githubusercontent.com/56029953/142926707-5b0f2aa9-cf66-4a0c-b5ab-6a2f681c6425.PNG)
![augmentation_bcs](https://user-images.githubusercontent.com/56029953/142926719-b9a72fed-7a62-4d87-b338-3db7ce753770.PNG)

## Chosen model and results :
For this task **-Defect Segmentation-** I chose **Detectron2** as a model. Recent papers have shown detectron2 has better results (in terms of Accuracy and runtime) than **Mask RCNN** and **Faster RCNN**.
### Creating a custom dataset
- Coco format
### Train and results
![gd_pred](https://user-images.githubusercontent.com/56029953/142926748-7555d61a-0dcf-41d1-90f3-6606606b0b3e.PNG)
![mdm_pred](https://user-images.githubusercontent.com/56029953/142926768-6f438ef9-b4d1-45bf-a194-57d61bd52d7f.PNG)
