
# Introduction:
With this project, it is aimed to classify the stars using machine learning algorithm, based on their spectral characteristics. These classes are as follows:
 
  * Galaxies
  * Quasars (QSO)
  * Stars

Every observation is described by 17 feature columns and 1 class column which identifies it to be either a star, galaxy or quasar. The data is provided by SDSS (Sloan Digital Sky Survey) and is named SDSS17 because it describes 17 properties of stars. You can find more detailed information about the dataset from the Kaggle link below.

https://www.kaggle.com/datasets/fedesoriano/stellar-classification-dataset-sdss17

## Approach

1. Data representation and description
2. Pre-processsing and future extractions steps
  * Feature selection
  * Detecting Outliers
  * Dealing with Imbalancing
3. Learning Approach and Systems Structure
  * XGBoost Classifier with No Hyperparameter Tuning
  * Grid Search for XGBoost
  * Random Search for XGBoost
  * Bayesian Optimization for XGBoost
4. Implementation Details
5. Evaluation Details and Results
  * Dataset Splits
  * Evaluation Metrics
  * Results

## Baseline Algorithms

Different machine learning algorithms were tested on the data set with default parameters. As can be seen below, Bagging Classifier, XGB Classifier and Random Forest Classifier algorithms are very close to each other and performed very good results. Accuracy scores are used to compare algorithms for this quick test. According to the relevant results, these 3 algorithms were selected to perform hyperparameter tuning.

1. LogisticRegression: 0.7524687954283422
2. KNeighborsClassifier: 0.797633966614868
3. BaggingClassifier: 0.9782946513609705
4. XGBClassifier: 0.9799989974434808
5. DecisionTreeClassifier: 0.9669156348689157
6. RandomForestClassifier: 0.9796982304877437
7. LinearSVC: 0.734573161561983
8. SVC: 0.5959697227931224
9. MLPClassifier: 0.3606697077547747
10. GradientBoostingClassifier: 0.9770414557120658
   
## Background about the Topic

Before start the modeling, it will be useful to know more about the classification of the stars.
When an object is heated, it can begin to glow, dull red at first, then brighter, the color changing from red to yellow to blue as the temperature rises, its peak radiated wavelength gets smaller. Wien’s Displacement Law illustrates this as follows:

> λmax = b / T

Where,

>λmax = Wavelength at which the blackbody dominantly radiates,

>b = Wien’s constant and its value is 2.897 × 10-3 m K,

>T = Temperature (kelvin).

This theory has practical relevance for this problem because the intensity profile of the spectrum provides information about the temperature of the radiator. The radiation distribution of different stars shows bell-shaped curves, whose peak intensity shifts to shorter wavelength, respectively higher frequency with increasing temperature (Planck’s Radiation Law). [2] So that, it would be possible to get information of stellar bodies and, at the same time, find relationships between them. Wien’s Displacement Law can be used to measure the temperature of stars by looking at the wavelength where their spectrum peaks. One way of doing this is to use a spectrograph (instrument used to measure properties of light over a specific portion of the electromagnetic spectrum). Another way is to use precise color filter scheme that can be used to quickly form a measure of star’s temperature. Star color magnitudes are measured through these filters (U, B, and V filter transmission curves are shown below), and the star color index (the difference of two-color magnitudes) can be used to determine the star's color temperature.

![image](https://github.com/user-attachments/assets/ebfc551a-11ab-4a7f-bc79-84985cc99770)

The image below, taken from SDSS's website, is of a galaxy. You can also see the spectral features of the galaxies in the image. The aim of this study is to classify stars using these features. 

![image](https://github.com/user-attachments/assets/9feccd26-348c-4e7f-b6fd-a75553a41f0d)

First, we will describe the data and remove unrelated feature columns from data. Secondly, we will try to detect outliers and whether there is an imbalancing in target column or not. Then, we will split the data to train and test set to perform different machine learning algorithm with different hyperparameter tuning technics. Lastly, we will compare them by using their accuracy score and select the best algorithm with highest score.


## Abstract:
Stellar classification in astronomy is the classification of stars according to their spectral properties. One of the most basic classification systems used in astronomy is that of galaxies, quasars, and stars. Following the discovery that Andromeda was a different galaxy from our own and the recognition that stars in the early cataloguing of stars and their distribution in the sky made up our own galaxy, a number of galaxies started to be investigated as more potent telescopes were constructed. The purpose of this dataset is to categorize stars, galaxies, and quasars according to their spectral properties. The data set used in this study consists of 100,000 SDSS (Sloan Digital Sky Survey) observations of space. Each observation is defined by 17 feature columns, and a single class column designates whether it is a star, galaxy, or quasar. During exploratory data analysis phase, outliers are detected and removed from dataset and SMOTE methodology is performed to deal with class imbalancing but decided to not use since it is not affected the accuracy score of baseline models. XGBoost classifier is selected as main model in this study and three different hyperparameter tuning technic is used to select best parameter combinations. 3-Fold cross-validation results show that the model adjusted using random search methodology is the best, according to the accuracy score results. It is received a score of approximately 98.03%, which can be assumed very good. However, we can say that the results obtained with other methods are comparable and of high level.
