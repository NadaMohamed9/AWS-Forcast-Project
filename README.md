# AWS-Forcast-Project
Household energy consumption forecast

Previously, we leveraged the Amazon Forecast console to predict household energy consumption. We are now going to leverage the high level APIs from this service to achieve the same: this notebook takes approximately an hour to run.

The overall process for using Amazon Forecast is the following:

Create a Dataset Group, this is the large box that isolates models and the data they are trained on from each other. You can see that as an independant forecasting "project".
Create a Dataset: in Forecast there are 3 types of dataset, Target Time Series, Related Time Series, and Item Metadata. The Target Time Series is required, the others provide additional context that certain algorithms can leverage.
Import data, this moves the information from S3 into a storage volume where the data can be used for training and validation. You can see this as the ingestion process into the Forecast dataset.
Train a model, Forecast automates this process for you but you can also select particular algorithms, and you can provide your own hyper parameters or use Hyper Parameter Optimization (HPO) to determine the most performant values for your data.
Deploy a Predictor, here you are deploying your model so you can use it to generate a forecast.
Query the Forecast, given a request bounded by time for an item, return the forecast for it. Once you have this you can evaluate its performance or use it to guide your decisions about the future.
