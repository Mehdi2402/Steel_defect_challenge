# Severstal: Steel Defect Detection (Kaggle challenge)
link : https://www.kaggle.com/c/severstal-steel-defect-detection
## Challenge presentation :
In this competition, the goal is to improve the localisation and classification surface defects on a steel sheet.


We are provided 12600 steel sheet images, and the goal is to predict the location and type of defects found in steel manufacturing. Each image may have no defects, a defect of a single class, or defects of multiple classes.

An example of what a steel sheet image looks like :

![example](https://user-images.githubusercontent.com/56029953/142926784-2d794fb4-20b8-4ded-9b14-f0cc25a4f881.jpg)


The labels given in this challenge are, for each Image Id :
* The Defect Class : **ClassId** : [1,2,3,4]
* The defect region in a run-length encoding (rle) : **EncodedPixels**

## Data augmentation :

For first data augmentation I used Brightness, Contrast, Saturation. No change in mask location were needed for these augmentations.
The second augmentation was : Vertical flip, Horizontal Flip and 180° rotation. 180° rotaion was used instead of a random degree to keep the entire image in frame not to lose the defect region.
The same changes had to be applies to mask region to be compliant with image change.

### Here are some examples of augmentation :

**Vertical flip, Horizontal flip, 180° Rotation :**

![augmentation_vhf_rot](https://user-images.githubusercontent.com/56029953/142926707-5b0f2aa9-cf66-4a0c-b5ab-6a2f681c6425.PNG)
---
**Brightness, Contrast and Saturation :**
![augmentation_bcs](https://user-images.githubusercontent.com/56029953/142926719-b9a72fed-7a62-4d87-b338-3db7ce753770.PNG)

## Chosen model and results :
For this task **-Defect Segmentation-** I chose **Detectron2** as a model. Recent papers have shown detectron2 has better results (in terms of Accuracy and Runtime) than **Mask RCNN** and so **Faster RCNN**.
### Creating a custom dataset
In orther to use detectron2 we need to put our custom dataset in a **COCO-format** than use it as input for a detectron2 that was achieved using the followig objects *(MetadataCatalog, DatasetCatalog and build_detection_test_loader)*.
### Results
**Original image**
![gd_pred_true](https://user-images.githubusercontent.com/56029953/142930037-bb04d0dd-1f3a-4174-893a-d7aa0c150c18.PNG)
**Prediction**
![gd_pred_pred](https://user-images.githubusercontent.com/56029953/142930048-46bc5b7b-1e57-4ff5-86e5-8b2ffa77141b.PNG)
---
**Original image**
![mdm_pred_true](https://user-images.githubusercontent.com/56029953/142930076-5e249087-df57-42e2-b70e-3b3050065b86.PNG)
**Prediction**
![mdm_pred_pred](https://user-images.githubusercontent.com/56029953/142930063-04c20f4c-c84e-47e6-83cb-9ab2dfd37035.PNG)
