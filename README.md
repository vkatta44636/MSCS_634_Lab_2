# MSCS 634 – Lab 2

**Purpose of the Lab**

The goal of this lab is to conduct and compare the performance of two classification algorithms – K-Nearest Neighbors (KNN) and Radius Neighbors (RNN) – on the Wine Dataset provided in the Python `sklearn` library.

There are 3 wine classes and 13 numerical features in the Wine Dataset and a total of 178 samples. Each of the features corresponds to different chemical features of wine. The data set was split into 80% training data and 20% testing data for model development and evaluation.
The primary goal of the experiment is to understand the impact of various values of k in KNN and varying radius values in RNN on the classification accuracy. 

**K-Nearest Neighbors (KNN)**

The following numbers of k were tested on the KNN classifier:
- k = 1
- k = 5
- k = 11
- k = 15
- k = 21

The results indicated that the least accurate result was around 77.78% for k = 1. The accuracy improved to 80.56% at k = 5 and stabilized around that level for k = 11, 15 and 21.
From the tested values 'k=5' was found as the first parameter value where maximum KNN accuracy is 80.56%.

**Radius Neighbors (RNN)**

The following radius values were used to test the Radius Neighbors classifier:
- Radius = 350
- Radius = 400
- Radius = 450
- Radius = 500
- Radius = 550
- Radius = 600

The highest RNN accuracy was 72.22% at radius = 350. This accuracy reduced to about 69.44% or the radius values of 400, 450 and 500. It dropped further to about 66.67% for the radius value of 550 and 600.
The results show that the radius was not improving the classification results for this dataset and test split.
So, KNN had the highest test accuracy of all the models, surpassing the test accuracy of Radius Neighbors. The best KNN result was **80.56% at k = 5**, while the best RNN result was **72.22% at radius = 350**.
The relative stability of the results obtained using KNN also revealed after k>5. However, the accuracy of RNN normally declined with the increase of radius. A larger radius enables more distant observations to be involved in the classification process, sometimes even observations from other classes which results in a decrease in classification accuracy.
The experiment shows that the choice of the parameters does have a significant effect on the performance of distance-based classification algorithms. If the number of nearest observations is fixed, then KNN might be better suited for the predictions; if the observations that occur within a certain distance are more significant, then RNN could be more useful.

**Challenges and Decisions**

A problem with the Radius Neighbors classification is that there may be observations in the neighborhood that do not contain any training points. In order to cope with this, the value outlier_label="most_frequent" was added.
Feature scaling was also an important aspect. As KNN and RNN are distance-based algorithms, the magnitudes of the numerical features can influence the distance computation. In this lab, the original feature values were retained for evaluation of the needed values of the radius which are 350, 400, 450, 500, 550 and 600.
The data set was divided with `random_state=42` to ensure results were reproducible and `stratify=y` was used to keep the class distribution same across the training and testing sets.

**Conclusion**

In this lab, the effect of neighborhood parameters on KNN and Radius Neighbors classification was illustrated. The best accuracy obtained by KNN was 80.56% and the best accuracy obtained by RNN was 72.22%. The results emphasize the need to set the parameters properly for distance based machine learning algorithms.