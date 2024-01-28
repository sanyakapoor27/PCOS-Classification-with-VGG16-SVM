# PCOS-Classification-with-VGG16-SVM

The impact of PCOS on Women's health is disastrous and hinders them from living a comfortable life. The amount of misdiagnosis and lack of doctors has lessened the chances of women getting proper treatment.
Thus, there is a requirement of Computer Aided Diagnosis Systems working with Doctors so that every patient can be treated the best.

## Dataset
Due to there being a lack of availability of PCOS datasets with sufficient data, I have compiled two datasets together, one which is available on kaggle “https://www.kaggle.com/datasets/anaghachoudhari/pcos-detection-using-ultrasound-images” and the other being Dataverse from Telkom University, Indonesia. After compiling, the total images come to be 1942 images in two folders namely, ‘infected’ and ‘not infected’. This dataset was downloaded onto my Google Drive and then loaded on my Google Colab Notebook.

## Preprocessing
For preprocessing we have gone through with a few steps, starting from reading the image through cv2 and converting it to grayscale to be further processed. Intensity transformation is
applied first to brighten the image around the ROI. This is followed by applying Gaussian Filter to minimize spectral noise. Adaptive Histogram Equalization is then used on the grayscale
image to enhance the contrast of the image equally. Morphological operations like erosion and dilation are done to remove small noise characters while preserving the image. A binary mask is created using Multi-Otsu thresholding which is further used for feature extraction.

## Train-Test Split and Data Augmentation
The images in the folders of infected and not infected are divided into a ratio of 80:20 and then separated to form train and test folders respectively. ImageDataGenerator class from Keras is used for the training directory to further diversify the images being provided to the VGG 16 model. Data is augmented by applying rotation, flip, width and height shift, horizontal flip
zooming.

## VGG16-SVM
We import the VGG 16 model from Keras and assign it with ImageNet weights. The segmented images are then fit on the model to extract features and then reshaped for the SVM classifier. SVM is imported from sklearn library. We’ve used SVM with linear kernel and soft margins and rbf kernel to classify our data. The features extracted from VGG16 go through the Chi-square
test which determines the three best features to be used.
