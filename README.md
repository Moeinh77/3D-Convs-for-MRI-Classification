# MRI-Geder_Classification
Gender classification on 3D IXI Brain MRI dataset 

### Dataset:

I have used IXI Brain MRI dataset that each image has 150 slices and it is available [here](https://brain-development.org/ixi-dataset/). I downloaded the T1 images and used 80% percent of it for training and 20% for test/validtion. Since the data only contains 566 images I had to keep the test set at 20% and had to use the test set for both validation and test. Since the data has a high number of channels (150 channels) it coul not be loaded into the RAM all at once, so for training of the first model I created a datagenerator that yields 4 images at the time. I used nibabel library for reading the .nii images in this dataset. 


### Model:

I tested 3 Diferent models for this classification task:

* DenseNet169_3D
* DenseNet121_2D
* DenseNet169_2D

The first Model can be downloaded from [this](https://github.com/GalDude33/DenseNetFCN-3D) repository, and the two others are avaialbe through TensorFlow. The 3D model was trained from scratch while the two others had pretrained weights.

### Results:

The 3D model used 80 slices from 150 (slices 35 to 115), the training took about 74 minutes on google colab, and it reached 83% on training set and 75% on test set. However DenseNet121 managed to reach reached 88% on training set and 93% on test set and DenseNet169 94% on training set and 90% on test set. The 2D models only used 3 slices from 150 slices (slices 74,75,76) and they achieved better results which indicates the importance of pretraining whe the dataset is small. DenseNet121 has underfitting which is the result of whether weakness of the network or the learning rate value at final epochs, but Densenet 169 shows a more regualar results which can be improved by training for longer time or better hyper parameters.
