# GalaxyZoo

The above notebook is my solution to the Kaggle Galaxy Zoo competition (https://www.kaggle.com/c/galaxy-zoo-the-galaxy-challenge), as my final project for the class ASTR 31200 Computational Techniques in Astrophysics at the University of Chicago. The notebook contains the code with some explanatory notes. 

The architecture of the CNN used here is summarized in this plot:

![alt text](CNN_diagram.pdf)


<!-- <img src="CNN_diagram.pdf"></img> -->

This model achieves \~85% accuracy:

![alt text](accuracy.pdf)

## Some additional thoughts: ##

Data augmentation is extremely helpful. I cropped out the central region of the image that contains only the galaxy of interest in most cases, eliminating confusion by including unnecessary noise/nearby objects in the data.  The rotation and shifting transformation of original images helped to significantly increase the size of the training sample.

I have also tried different architecture design for the network, including a different number of convolutional/dense layers, different size choices for the filter map, different number of nodes in the dense layers, etc. Increasing the size of the network and the number of parameters doesn't always lead to a higher accuracy.  The model I showed in the notebook has the best performance among my attempts. 

I have been using the binary_cross_entropy loss function, the default training rate from the adam optimizer, the softmax activation function for the output dense layer, and a dropout of 0.5 after each fully connect dense layer (except for the last one) to limit overfitting. I originally thought that KL divergence could also be a good loss function for this data set and I didn't try it out due to the time limitation. However according to one of my classmates experience, KL divergence does not work for this problem and made it hard for models to train. 

The learning rate could also be adjusted and time varying learning rate could potentially be applied to achieve a better result. Additional regularization (e.g., L2) could also be applied to better limit the overfitting present in some of the models I tried. Due to the time limitation and the fact that the model I showed above already has a satisfactory performance, I did not experiment with all these factors. 

If retraining some of the existing architecture from scratch with this data set (e.g., Xception), it's also possible to increase the accuracy further more.