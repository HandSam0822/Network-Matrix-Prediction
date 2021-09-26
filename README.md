# Network-Matrix-Prediction
Markov chain Monte Carlo (MCMC) is a method in statistics that comprise a class of algorithm for sampling from a probability distribution.
By constructing a Markov chain that has the desired distribution as its equilibrium distribution, one can obtain a sample of the desired distribution 
by recording states from the chain. 

In the project, I applied [CatBoost Regressor](https://catboost.ai/docs/concepts/python-reference_catboostregressor.html) on the implementation of a Network Matrix Prediction model. 
The goal of the model is to predict the sequential relationship between current states and next states of the network matrix. Simply speaking, by training the model with data
from state 0 to state t-1, we could predict state t, t + 1, ..., t + n with the pattern of data distribution.

The network matrix is defined as a N x N 2D matrix, where N is **the number of battery stations** and matrix<sub>i</sub><sub>j</sub> is the interaction probability between 
station<sub>i</sub> and station<sub>j</sub>.


## Value of the model
### For Business Intelligence (BI) team
- Business Insight
  - With more and more battery stations being built in the city, the interaction between adjacent stations is too complex to be interpreted by people. For example,
if station i is built 1km away from present station j, some users who used to visit station j will pivot to station i because it is more convenient (or any other complicated factors).
From the perspective of the Business Intelligence (BI) Team, the value of this model is to help them evaluate the potential effect of building a new battery station. 


- Data-driven metrics
  - As long as BI team calls the API with command line arguments such as expected location(longitude, latitude) of the newly built station, expected time slot..., 
  the command line parser will parse their arguments, feed them into the pre-trained method, and generate simulating the result of future network matrix. The result based on millions of training data provides more explainability and quantitative indicators for business decisions.

### For Data Science (DS) team
- Code Refactoring 
  - Originally, the some data query and processing functions are not well-structured and designed. Most of them are written by individual without integration.
  My contribution of code refacotring part including:  
  1. Replace shell script with command line arguments (so that users don't need to create new script or edit existing scripts)
  2. Design several classes to wrap those commonly used functions (e.g. DataHandler.py, FeatureEngineer.py, TransformMatrix.py.) 

- Automatic data visualization 
  - The most important thing for predicting model is to find important features to explain the relationship between stations and stations. A great way is using 
  1D and 2D histogram to observe the distribution. Therefore, with automatic data visualization (PlotPipeline.py, Draw.py, analysis_plot.py), the whole team could 
  test new features through visualization


For the detail of implementation, you could refer to [my essay](https://drive.google.com/file/d/1qcHWCHrgzYfhWVpvlE018orSmabDs3_V/view) 
