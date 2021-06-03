# MRI-Geder_Classification

### Dataset:

I have used the IXI Brain MRI dataset that each image has 150 slices and it is available [here](https://brain-development.org/ixi-dataset/). I downloaded the T1 images and used 80% percent of them for training and 20% for test/validation. Since the data only contains 566 images I had to keep the test set at 20% and had to use the test set for both validation and test. Since the data has a high number of channels (150 channels) it could not be loaded into the RAM all at once, so for the training of the first model, I created a data generator that yields 4 images at a time. I used Nibabel library for reading the .nii images in this dataset. 

### Model:

I tested 3 different models for this classification task:

* DenseNet169_3D
* DenseNet121_2D
* DenseNet169_2D

The first Model can be downloaded from [this](https://github.com/GalDude33/DenseNetFCN-3D) repository, and the two others are available through TensorFlow. The 3D model was trained from scratch while the two others had pretrained weights.

### Challenges:

* The images in this dataset have a high number of channels and processing them requires a huge amount of RAM and GPU
* Using 3D convolutions requires more GPU and they are the calculations are more time consuming
* Lack of examples projects about feeding .nii files to Keras models on the internet

### Results:

The 3D model used 80 slices from 150 (slices 35 to 115), the training took about 74 minutes on google Colab, and it reached 83% on the training set and 75% on the test set. However, DenseNet121 managed to reach reached 88% on the training set and 93% on the test set and DenseNet169 94% on the training set and 90% on the test set. The 2D models only used 3 slices from 150 slices (slices 74,75,76) and they achieved better results which indicates the importance of pretraining when the dataset is small. DenseNet121 has underfitting which is the result of whether weakness of the network or the learning rate value at final epochs, also Densenet 169 results can be improved by training for a longer time or better hyperparameters.
