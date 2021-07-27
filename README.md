# MSE491_Project
 Application of Machine Learning Techniques to Analyze EEG Data of Epileptic and Non-Epileptic Patients
MSE 491 Final Project
Analyzing EEG Dataset of Epileptic Patients
MSE491 Machine l earning
School of Mechatronic Systems Engineering
Ricardo Bravo 301282697
Jonathan Kiing 301276654
April 22, 2021
1 Introduction 3
2 Background 3
3 Methods 4
4 Results 5
4.1 Basic Neural Network 5
4.2 Logistic Regression 6
4.3 K-Nearest Neighbors (KNN) 6
4.4 Decision Tree 8
4.5 Naive Bayes 9
4.6 Support Vector Machine (SVM) 10
5 Discussion 10
6 Conclusion 11
REFERENCES 12
1
1 Introduction
Despite advancements i n modern medicine, the scientific community still has a very l imited
understanding of how the brain works and functions. One method that has had i ts popularity
grow i n recent decades i s using a particular sensor, an EEG sensor (electroencephalography
sensor). These sensors can measure electrical activity of the brain, therefore using multiple
EEG sensors i n an array throughout the head can provide an electrical activity map of the brain
which can provide doctors and scientists with physical and measurable data that could be used
to diagnose various diseases and i njuries and aid i n the recovery process. Epilepsy i s a
categorized condition where all subjects experience epileptic seizures with some and some
unknown causes. Very l ittle i s understood about the disease, i n particular how to properly
diagnose or detect early warning signs i n various patients.
2 Background
According to the CDC, a person i s diagnosed with epilepsy i f they have more than two or more
seizures. Epilepsy i s a relatively common condition, affecting roughly 1% of the population i n the
United States [1] and up to 9% of the population will have a seizure during their l ifetimes.
Epilepsy i s categorized as a brain disorder, where epileptic seizures are i nduced when the
electrical signals i n the brain begin to behave i rregularly, causing a surge i n brain activity.
Seizures are sporadic, i nstantaneous and i nstantly i ncapacitates a person, causing muscle
spasms, l oss i n speech and control over their entire body. Currently i t i s known that any
permanent damage to the brain, whether from high i mpact collisions, strokes, brain tumors,
oxygen l oss can cause seizures to occur, however i t has also been noted that a person may
also be genetically predisposed to seizures and therefore epilepsy. Given our knowledge about
epilepsy, i t can be noted that, despite known causes, epilepsy i s a disease that i s difficult to
diagnose.
Machine l earning can be used to diagnose and i dentify certain traits and aspects about seizures
and epilepsy that could help doctors give a more thorough diagnosis. By l ooking at l arger and
larger datasets describing epilepsy, the scientific community can better l ook at potentially
making greater discoveries that could l ead to better treatments and potential cures for the
disease. One current and wide-spread method i s using electroencephalography (EEG)
technology to record electrical signals below the skull.
2
3 Methods
Since EEG technology has been a popular method for analyzing brain activity, there are many
studies and databases with robust datasets. Despite EEG being popular, there i s very l ittle data
available to the public. While other databases are available such as Neural Engineering Data
Consortium [4] which provides data collected and certified by neurologists of various patients,
however the data proved to be too cumbersome to work with and required too much filtering
before attempting to analyze. Therefore for this project, the goal for the data was to be a l arge
data pool pre-organized and l aid out, making the transition to setting up a machine l earning
algorithm smooth and simple.
The data used i n this project i s available on Kaggle, an online community of data scientists. One
particular database provided EEG data from over 500 patients, all using the same configuration
and l ayout for the EEG collection, providing a l arge yet controlled dataset. The data used comes
from a UCI study conducted i n 2002 [2], where i t gathered and classified the data i nto 5 different
categories. The first three categories (labelled 1, 2 and 3) were from epileptic patients. Patients
in the first set recorded EEG data during an active seizure, set twos and three were EEG
readings from within the brain at varying l evels, collected from patients pre surgery. Set two was
taken within the epileptogenic zone whereas set three was from the hippocampal zone. The l ast
two stages (4 and 5) are from volunteers i n a relaxed and awake state with eyes open or closed.
The raw data was taken using the same 128-channel amplifier system, using an average
common reference [2]. In total, there are 178 EEG values read per second. Each person’s
readings l asted for 23 seconds where each data point taken was an average EEG reading over
a 1/23rd of a second. A total of 500 patients were used equating to over 11500 data points. The
data provided from this experiment has been preprocessed by taking the amplitude difference
between the first and l ast data points that were within the range of amplitude difference of
consecutive data points, which avoids the use of window functions for a calculation of the power
spectrum [2]. While i t provided this project with consistent and smooth data, upon further
analysis i t would have been more i nsightful i f the preprocessed data was also provided.
Lastly, for this type of classification problem, multiple machine l earning techniques were chosen
to analyze the dataset. Basic Neural Network Model, Binary Classification (Logistic Regression),
Multi-Class Classification Models (KNN, Decision Tree, Naive Bayes, and Support Vector
Machine). The focus of the analysis will be K-Nearest Neighbors since there are 4 l abels for this
set while the other models will be used to explore and compare with the results of the KNN
model.
3
4 Results
4.1 Basic Neural Network
The neural network model created for this analysis i s a basic neural network consisting of 178
input nodes (corresponding the amount of eeg readings per second), an activation function of
ReLU for the hidden l ayer, and a softmax activation for the 4-node-output l ayer. The accuracy
of the model after 10 epochs i s 83.30% and a l oss of 39.04%.
Figure 1: Accuracy vs Epoch Number
Figure 2: Loss vs Epoch Number
4
4.2 Logistic Regression
In order to use Logistic Regression, the l abels were simplified. Eyes open, eyes closed, Tumour
location, and health brain readings were all grouped and l abeled as Non-Epileptic, as seen i n
the figure below. It can be seen i n the result below that the model failed to classify l abels
properly.
Figure 3: Confusion Matrix of the Logistic Regression Model
For this dataset, i t can be seen that grouping the 3 other l abels i nto one does not present an
advantage to the analysis since the predictions for Epileptic i s close to 0% accuracy.
4.3 K-Nearest Neighbors (KNN)
Four KNN models of varying size (i.e. K = 2, 3, 4, and 10) were created to analyze this dataset.
The values were chosen such that the i mprovements on the model can be shown. As expected,
increasing the numbers i mproved the accuracy of the model. Below are the results. Note that
EP, TL, HL, and EM corresponds to epileptic seizure readings, tumour l ocation readings, healthy
brain l ocation readings, and eye movement readings, respectively.
5
Table 1: Accuracy, Precision, and Recall values of the KNN Model with K = 10
Figure 4: Confusion Matrix of KNN, K = 10
6
K = 10 Accuracy Precision Recall
Epileptic Seizure 0.98 0.61 0.76
Tumour Location 0.34 0.59 0.
Healthy Brain
Location
0.30 0.60 0.40
Eye Movement
Location
0.87 0.30 0.45
Figure 5: Confusion Matrix of KNN, K = 2
Figure 6: Confusion Matrix of KNN, K = 3
Figure 7: Confusion Matrix of KNN, K = 4
4.4 Decision Tree
In addition, the group has decided to also use a Decision Tree classifier to analyze this dataset.
Below i s the result. It can be seen i n the data below that the eye movements and epileptic
seizure readings were predicted with a higher and medium accuracy when compared to
7
previous model attempts to i dentify the correct outcome. On the other hand, the presurgery
results were predicted with a subpar accuracy.
Figure 8: Confusion Matrix of the Decision Tree Model
4.5 Naive Bayes
Naive Bayes i s known for having an advantage on datasets that contain many i ndependent
variables. It can be seen i n the result below that outside of the seizure readings, all three
variables can’t be predicted with high accuracy. Similar to the result from the l ogistic regression
model, there i s l ittle i ndependence between the three variables due to the presence of eye
movement signals. This i ndicates that naive bayes could be used to detect i f one were having a
seizure or not.
Figure 9: Confusion Matrix of Naive Bayes
8
4.6 Support Vector Machine (SVM)
Lastly, the group decided to use a support vector machine model to see other possibilities. It
can be seen i n the figure below that despite having very accurate predictions on epileptic
seizure readings, the model failed to classify other types (i.e. tumour and healthy brain
readings). All eye movement predictions were falsely predicted to be a healthy or tumour
location. The reason for this i s the nature of the SVM model being i naccurate for datasets that
have l arge noise components and target classes overlapping (i.e. TL, HL, and EM).
Figure 10
5 Discussion
One main l imitation that we encountered i n this project i s the availability of usable data. Due to
the nature of the topic, the amount of free data online i s close to none. One option that we had
was a raw EEG data set that required extensive EEG analysis, which i s out of the scope of this
course. Thus, the dataset we used i s a preprocessed data, ready for machine l earning
purposes, offered by the University of California, Irvine. [3].
It can be seen i n the results that the most accurate models for this analysis were the KNN of
K=10 and the Decision Tree Model. The l ogistic regression model failed i n this analysis due to
the noisy nature of the data. On the other hand. The Naive Bayes and SVM model also are not
that accurate for non-epileptic readings.
As seen i n the KNN models, i ncreasing the k-value (i.e. the number of neighbours), helped i n
increasing the accuracy of the models. KNN provides a fairly cheap and quick method of
learning about datasets with multilabel data. KNN also has the ability to classify overlapping
variable pools. This feature i s useful given the nature of this dataset where many EEG readings
had similar or i dentical correlations between each of the variables.
9
6 Conclusion
The KNN model with a k-value of 10 had the most accurate predictions for the model. While the
decision tree also has a high accuracy for seizure and eye movement. To build a more robust
model, more dataset i s needed i nvolving more participants i n all classifications to solidify the
findings of this research. Some further notes to take away from this project was, EEGs of
current design may not be capable of providing robust enough i nformation. EEGs collect
electrical activity from thousands or millions of neurons and sums up the activity as a single data
point. It i s currently unproven whether this mass l umping of neural activity can provide
researchers with thorough enough information to delve deeper into the inner workings of brain
activity. Lastly, having more knowledge on EEGs and the nature of i t, as well as access to an
EEG software can help to pick the best features for i mproving the model.
10
