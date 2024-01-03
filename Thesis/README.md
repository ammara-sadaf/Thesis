## COCHLEAR CONDUCTIVITY PREDICTION
give introduction here
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

WRITE DATA PROCESSING METHODS...

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
* n_hidden_dim -> the dimension of the LSTM hidden layer

* n_features -> the number of input features for the drilling data

* n_layers -> number of LSTM layers

* dropout -> dropout layer
* proj_layer -> the projection layer that maps every timestep hidden dimension to final prediction (in our case is 1)


## LSTM multi timestep

#### usage
navigate to the 'lstm_multitimestep.ipynb' file and run each cell of the code, each cell is guided with comments. the notebook containes everything needed to run the mdoel as well.


## Parameters
* n_hidden_dim -> the dimension of the LSTM hidden layer
* n_features -> the number of input features for the drilling data
* n_layers -> number of LSTM layers
* dropout -> dropout layer
proj_layer -> the projection layer that maps every timestep hidden dimension to final prediction (in our case 1)


## VISUALIZATION
