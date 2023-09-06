# LSTM-Forecasting
# Forecasting Mars Dust Storms

**Overview**

This notebook formulates a forecasting model using Long-Short Term Memory (LSTM) model to forecast features that influence the dust storms on Mars using the data available from Mars Science Laboratory Mission (MSL) in Gale Crater.

**Installation**
To run this notebook the data set is the only material required. The file containing data set is provided along with the notebook. It is also available in my GitHub profile along with the complete code. I have provided the link to the data set in the data section.

**Usage**

The project is written in python. I have written this notebook in a straightforward and concise manner. The code can be run on any platform supporting python. It may require you to install some libraries depending on the platform you are using.

**Data**

The data set used in this project is Mars weather data from Mars Science Laboratory Mission. Raw and processed data is provided by Planetary Data System which is a data archive of data products from all NASA’s planetary missions. I have also used data from USRA Houston Repository which provides the processed data. I have collected data from these data providers and combined it into a comma separated values format for this project.

Following are the links to all data sets mentioned above:

Planetary Data System:

https://atmos.nmsu.edu/data_and_services/atmospheres_data/MARS/curiosity/curiosity.html

USRA Houston Repository:

https://atmos.nmsu.edu/data_and_services/atmospheres_data/MARS/curiosity/curiosity.html

Data set:

https://github.com/milanhub007/LSTM-Forecasting/blob/main/Gale_Crater.csv

**Reading data set**

Used Pandas library to read the data.
![alt text](https://github.com/milanhub007/LSTM-Forecasting/blob/main/Images/data.jpg?raw=true)

**Preparing the data**

Basic preprocessing methods are used:

Cleaning data: The missing values are managed using fillna method with rolling window and interpolate method.

Exploratory Data Analysis: Visualization methods such as plots and heatmap to find the correlation between features.

Features: As a part of analysis to features are set as the input features, which are Ultraviolet flux and optical depth.

Scaling: Min max scaler is used to transform the features.

Splitting the data: Entire data set is of 2500 Martian days. The data is split into 70 percent training, 10 percent validation and 20 percent testing set. The data set used previous 10 data points for
prediction on each batch size.

![alt ext](https://github.com/milanhub007/LSTM-Forecasting/blob/main/Images/shape.jpg?raw=true)

**Model** 
A function build_model with optimizer as input parameter is made. The architecture consists of the first LSTM layer with 128 batch size and second layer with 64 batch size. The final output layer has 2 units for two features. The return sequence is set for returning full sequence of hidden state on first layer and return sequence as false on second layer. Mean Squared Error is used as loss function. Keras regressor method is used which allows GridSearchCV for hyper tuning. I have provided batch size, number of epochs and optimizers as tuning parameters. Cross validation is set as 2. Adam and Adadelta is given as optimizers. In cv = 2, the data is divided into two equal-sized subsets. The model is trained on one subset and evaluated on the other, then the process is repeated with the roles of the two subsets reversed. The performance of the model is then averaged over the two folds to provide an estimate of its performance on unseen data.
