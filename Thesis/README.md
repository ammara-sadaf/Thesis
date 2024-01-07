## COCHLEAR CONDUCTIVITY PREDICTION
This repository addresses the problem of predicting thermal conductivity of bone equivalent material from temperatures curves and acquistic signals recorded during bone drilling . This repository contains a pipeline for data preparation as well as four different machine learning models to predict the thermal conductivity. Random forest, Xgboost,and LSTM with single and multiple timestamp are trained on feeding single drill as single time stamps and 70 percent of data as training, 20% as testing and 10 % as validation, Drilling parameters feedrate, RPM, and drilling depth aling with time series of temperature and audio has been used as input features and thermla conductivty of bone is used as label.  because we wanted to predict single drill in real process   only conductivity of 4 layers (equivalent to real bone) at time during surgery we cant feed random dividion of data so we had to feed one sequnece at a time this limited the model to remeber previous states for that we deisgned the LSTM with multiple steps is used in our method because The LSTM model was trained using a single time step approach, meaning it could only observe one data sample at a time for making predictions and had no capacity to retain information from past data samples
## VISUALS
put some visuals here

# TECHNOLOGIES AND FRAMEWORKS
- python
- pandas
- numpy
- scikit-learn
- pytorch
  
## INSTALLATIONS

firstly, you need to clone the repo and install the dependencies needed
```
git clone https://github.com/ammara-sadaf/Thesis.git
```

then you will need to navigate to the directory

```
cd Thesis/Thesis
```

and install the dependencies
```
pip install -r requirements.txt
```

after succesfully installation, then download the models here (....) and move them to the directory. then you can navigate through the notebook and run them, every notebook is guided with a comment

## DATA PROCESSING AND PREPARATION
Data preprocessing, including data cleaning, is essential before using the data to train an algorithm. This involves cleaning the data for outliers and missing values, as well as processing the data to be fed into the algorithm and train the system. The given paragraph describes the process of data preprocessing in the context of a specific dataset containing outliers and noise, and the steps taken to clean and process the data for effective use in training an algorithm.
### Mathematical Preprocessing:
A proper mathematical approach was adopted to refine the dataset by carefully trimming the data to capture the relevant drilling intervals, starting when the drill hits the material and ending when it is pulled out. The mathematical approach used for determining the start and end points of drilling involved the calculation of the theoretical time of drilling, which corresponds to the drilling depth divided by the feed rate. The endpoint was determined by adding the drilling time to the starting point, taking into account the manual start and stop of the measurement process. Additionally, logic was applied to determine the endpoint, involving a case discrimination with three cases, such as identifying the last point where the previous point is smaller by at least 0.5°C and determining the endpoint based on the time of reaching the initial position after the completion of drilling
### Segmenting Data into Layers:
The data was segmented into distinct layers based on the material's thickness, and the endpoint for each layer was determined mathematically explained above .
### Data Point Calculation: 
Data points for each layer were calculated based on the relative calculated time for each layer to ensure correct data trimming. Missing data points were not filled but deleted because the calculated time interval relied solely on recorded data.

## MACHINE LEARNING ALGORITHM
We train all our model in a supervised machine learning methods, i.e we have features and target labels for the model to learn from. the deep learning part is implemented in pytorch. in this section, i'll explain the architecture for each of the models.

## RANDOM FOREST REGRESSOR

The random forest regressor is a type of an ensemble methods that employs multitude of decision trees at training time and perform averaging of all the decision tree prediction, this type of ensembles reduces the problem of overfitting of decision tree models in the training data. we train the model to predict at every time step the conductivity of the drill from starting of the drill until finished. mean squared error and mean absolute error was employed on test data to assess how the model is performing.

# Parameters
* bootstrap (we set bootstrap to true)
* n_estimators (we set number of estimators to 200)


## XGBOOST MODELS
the xgboost model is another efficient gradient ensemble methods that sequentially builds and ensemble of weak learners to correct errors made by previous models, we train the model to predict at every time step the conductivity of the drill from starting of the drill untill finished. means squared error and mean absolute error is employed on held out data to assess how the model is performing.


## LSTM MODEL 



in our case, we developed two types of LSTM based model, the first model utilises one timestep to perform prediction of drilling conductivity i.e it only use the current timestep information to predict cochlear conductivity at every timestep untill drilling stop. the second model makes prediction based on current and previous timestep information of the drilling data i.e at every timestep, the model perform prediction based on previous information and the current informmation. 

# ----->> put LSTM architecture picture here

## LSTM single time step

#### usage 
navigate to the 'lstm_single_stimestp.ipynb' file and run each cell of the code, each cell is guided with comments. the notebook contains everything needed to run the model, you just have to make sure the model is paste on the appropriate path.


## Parameters
* n_hidden_dim -> (we set hidden dimension to 200)

* n_features -> (the number of input features for the drilling data is 8)

* n_layers -> (the number of LSTM layers is 1)

* dropout -> (dropout layer is 0.1)
  
* proj_layer -> the projection layer that maps every timestep hidden dimension to final prediction (in this case is 1)


## LSTM multi timestep

#### usage
navigate to the 'lstm_multitimestep.ipynb' file and run each cell of the code, each cell is guided with comments. the notebook containes everything needed to run the mdoel as well.


## Parameters
* n_hidden_dim -> (we set hidden dimension to 200)

* n_features -> (the number of input features for the drilling data is 8)

* n_layers -> (the number of LSTM layers is 1)

* dropout -> (dropout layer is 0.1)
  
* proj_layer -> the projection layer that maps every timestep hidden dimension to final prediction (in this case is 1)


## VISUALIZATION
