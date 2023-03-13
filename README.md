# BoVW_Classification
 

End to end implementation of Bag of Visual Words based image classification network

The model is build on Google Collab with Pytorch


<!--ts-->
Contents
<!--te-->

<!--ts-->
* [Introduction](##Introduction)
* [Heading 3](#heading-3)
* [Heading 3](#heading-3)
<!--te-->

## Introduction
The Bag of Visual Words (BoVW) is a method for representing images in computer vision and image processing. It is based on the concept of Bag of Words (BoW) model used in natural language processing.

The BoVW model is used to represent an image as a collection of visual words, which are obtained by clustering similar image patches together. These visual words are then used to generate a histogram that represents the distribution of these words in the image. The histogram can then be used as a feature vector to represent the image for various applications such as image classification, object recognition, and image retrieval.

This project aimed to demonstrate the use of BoVW for image classification using two data sets including Objects and Flowers data. The feature detector chosen for that matter was SIFT and image descriptors and key points were extracted using it. The descriptors were then used to develop the vocabulary for BoVW using K-means clustering technique. In order to determine the optimal cluster size elbow method was used and the  values in the surrounding window of k value given by it was tested and the value with the best results was chosen. After vocabulary construction the histogram analysis was performed on all the training and testing images to extract the frequency of each visual word in the image. Lastly, based on the histogram, classification was applied on the dataset by splitting it into test and train data and the classification results were analyzed for performance measures like  F1 score, accuracy, True Positive Rate, False Positive Rates etc. for two classifiers i.e. Support Vector Machines (SVM) and Random Forest.

## Algorithm Steps

BoVW model represents images as visual words that act as describing features of the images and based on the histogram of count of each feature in an image it is classified into a specific class. Following steps are involved in performing the image classification task with the use of BoVW. 
	
- Data Preparation : The first step involves reading the dataset and processing it into a desirable form. Both datasets comprised of multiple classes having images of different dimensions thus all the images were transformed into a standard shape of 256x256. The images in the dataset were all 3 channel RGB images and thus for the sake of simplicity images were converted into single channel gray scale images. 

- Feature Extraction : Next step is to extract key points and descriptive features from the images. For that matter sift classifier is used. Two lists were maintained. One having features of all the images vertically stacked together and the other list having index wise features placed in it for each image along with its label. 

- Codebook/Vocablary Generation: Next step is the generation of clusters of similar features to develop the vocablary of all the visual words in the data set. This is done by applying k-mean clustering on the features extracted from the images. The number of clusters depends on the dataset and there are several methods to analyze the optimal value of clusters for a given dataset including elbow method , gap statistics methods etc. Here, elbow method was applied and the  values in the surrounding window of k value given by it were tested and the value with the best results was chosen.

- Histogram : In this step a histogram for each image is computed having the counts of visual words from the vocablary.

- Classification: Lastly, the histograms computed in the previous step are used to train and test the model. The model is trained to classify the image into class with which it's histogram has maximum similarity. The dataset is split into training and testing data to evaluate the model's performance

- Analyzing Performance measures: The testing results obtained by the trained model are then used to generate classification report and confusion matrix to analyze the values of model against each performance measure.


