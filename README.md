# ML_LinearRegression
## **Stock price prediction using linear regression**

This is a project built to predict the stock price using linear regression ML algorithm. It makes use of a completely free open source library - yahoo_fin to get the historical data for any stock. This library is developed by the author of https://theautomatic.net/. The uniqueness of this project is that it allows you select the stock name(ticker name), the start date from which the data must be considered and the number of days after which the price of stock is to be predicted (Max 365, Min 0).

The complete steps in which the project is divided is as under :

#### 1. Importing the necessary libraries
The yahoo_fin library needs certain dependencies like requests_html. I have made use of the stock_info module of the yahoo_fin library. All the necessary imports are done at the start of the project.

#### 2. Get input from the user for the ticker(stock) name
I take the ticker input from the user and if the user types "none", the default value is set to "amzn"(Ticker for Amazon)

#### 3. Get input from the user for the start date to be considered for the dataset
The differences in the graphs of different stocks makes this input vital. For eg., while predicting the stock prices for "Amazon" including data from 2015 gives a 92% accuracy in the predicted data whereas in case of "Google", on including data from 2015, reduces the accuracy to 82%.

#### 4. Fetch data using yahoo_fin library
Using the yahoo_fin library, getting historical data is easy. We use the "get_data" function to do this. The get_data function takes parameters like: the ticker name, start date, end date, time interval (we collected data for each day)

`stock_data = get_data(ticker, start_date=startDate, end_date=datetime.today().strftime('%m/%d/%Y'), index_as_date = True, interval="1d")`

#### 5. Preprocessing the data
Imputation is the way of replacing the missing values in data with the substitute values. I have checked if there are any NaN values in the data. If yes, I replaced them with the median of all non NaN values.

#### 6. Plot original data
I have plotted the graph for the original data as a visual of the data is helpful in analyzing how much data must be taken for training and testing.

#### 7. Build the Linear Regression Model
In case of our model, I predict the stock price as a function of time. Thus just one dependant variable is involved in the prediction and hence it is an example of simple linear regression.
To build the model, we do the following things:

  - Convert the dates and prices to numpy array as the sklearn library needs numpy arrays
  - Split the data into training and testing datasets. Usually a 80:20 ratio is used.
  - We try to get the best accuracy by training the model multiple times

#### 8. Save the regression model
We can save our model using pickle and then load it again for further predictions.

#### 9. Find the accuracy of the model
The model makes use of RMSE to find the accuracy. The RMSE acts as a measure to check if the model fits the data well.

#### 10. Predict the stock price
The user can predict a stock price for number of days between 0 to 365

#### 11. Plot the predicted and the actual values
This plots the regression line and helps to visually analyse if the model is a good fit for the data.
