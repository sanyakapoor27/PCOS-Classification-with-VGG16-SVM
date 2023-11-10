# PCOS-Classification-with-VGG16-SVM

The impact of PCOS on Women's health is disastrous and hinders them from living a comfortable life. The amount of misdiagnosis and lack of doctors has lessened the chances of women getting proper treatment.
Thus, there is a requirement of Computer Aided Diagnosis Systems working with Doctors so that every patient can be treated the best.

In this colab file, I have presented a new solution which uses a pcos dataset from kaggle and using Otsu Thresholding segments it into a binary mask from which further features can be extracted.
The images are augmented so that the model can converge better. The features extracted using VGG16 are then classified by two SVM classifiers with a linear and RBF kernel.
