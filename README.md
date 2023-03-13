# BoVW_Classification
 

End to end implementation of Bag of Visual Words based image classification network

The model is build on Google Collab with Pytorch


<!--ts-->
Contents
<!--te-->

<!--ts-->
* [Introduction](##Introduction)
* [Algorithm Steps](##Algorithm Steps)
* [Results](##Results)
	* [Objects Data](### Objects Data)	
	* [Flowers Data](### Flowers Data)
* [Model Testing and Enviornment setting](## Model Testing and Enviornment setting)
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

The diagram attached below shows the sequence of steps

![FlowDiagram ](https://user-images.githubusercontent.com/59650991/224586868-5e4e9add-1131-4195-9dbd-4c173294c719.png)

## Results
### Objects Data

Objects data set consisted of 4 classes including Soccer Ball, Accordion, dollar bill , motor bike. The provided data set was split into training and testing data having 56 training samples and 8 testing samples. The value of k was kept to be 35. Both the classifiers caused only one miss classification in the testing samples giving and accuracy of 88\%. The confusion matrix and classification report having F1 Score , Precision etc. has been attached below for both classifiers


#### Random Forest 

![RF](https://user-images.githubusercontent.com/59650991/224587256-480910fa-e005-4911-b3a6-547fa4acab13.PNG)


#### SVM
![SVM](https://user-images.githubusercontent.com/59650991/224587261-be424556-9993-4983-bbb0-4d8e227e5307.PNG)


#### Correct Classification
![correct](https://user-images.githubusercontent.com/59650991/224587314-a2249e4b-dba7-4822-999a-793df396cbc4.PNG)


#### Wrong Classification
![wrong](https://user-images.githubusercontent.com/59650991/224587343-face4a82-92ed-40ce-a867-b7d15a53b07c.PNG)

### Flowers Data

Flowers data consisted of 5 classes including daisy, dandelion, roses, sunflowers, and tulips. There were total 3670 samples and the data was not split into training and testing samples thus while trianing it was split and 20% was kept for testing. Because of very slow clustering the value of clusters was kept to be 50. The data gave an accuracy of 58% with SVM and 55% with RF which might improve by increasing the number of clusters. The confusion matrix and classification report having F1 Score , Precision etc. has been attached below for both classifiers

#### Random Forest 
![F_RF](https://user-images.githubusercontent.com/59650991/224588499-c3996cad-9912-4e13-9683-f1f1cc084a9d.PNG)


#### SVM
![F_SVM](https://user-images.githubusercontent.com/59650991/224588492-bb45ad10-bf5e-43ce-9525-5bcb590ffbd0.PNG)


#### Correct Classification
![correct_f](https://user-images.githubusercontent.com/59650991/224588505-ee23e863-35f4-418b-bf29-e200cf2fd555.PNG)


#### Wrong Classification
![wrong_f](https://user-images.githubusercontent.com/59650991/224588517-4db2ab50-5b2e-48b3-a73c-32e5bb1f3ee3.PNG)

## Model Testing and Enviornment setting

- The model has been developed on google collab with pytorch 
- All the required libraried have been mentioned in the first cell and are all needed for succesfull execution of script
- The datasets have been read from google drive mounted with collab. The provided zip folders of dataset can be uploaded directly to google collab as well
- All the steps involved in the algorithm have been broken down into generic functions and have been initialized in the start
- Feature exraction, histogram computation, clusturing, model tesing and performace evaluation for both datasets have been implemented stepwise in sperate code blocka along with comments



