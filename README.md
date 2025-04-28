# Sales Forecasting for E-Commerce Retailer

## Task Overview
The goal of this project is to forecast the next 7 days of total revenue for an online UK retailer that sells unique all-occasion gifts. The data spans transactions from December 1, 2010, to December 9, 2011.

### Dataset
The dataset contains the following columns:
- **InvoiceNo**: Unique identifier for each transaction.
- **StockCode**: Product code.
- **Description**: Product description.
- **Quantity**: Quantity of items purchased.
- **InvoiceDate**: Date and time of the transaction.
- **UnitPrice**: Price per unit of product.
- **CustomerID**: Identifier for the customer.
- **Country**: Country of the customer.

The task involves analyzing sales patterns, forecasting daily revenue for the next 7 days, and providing insights and predictions based on the historical transaction data.

## Approach

### 1. Data Preprocessing
- **Data Loading**: The dataset was loaded using `pandas` from a CSV file.
- **Handling Missing Values**: 
  - We handled missing `InvoiceDate` values by removing rows with missing dates.
  - Negative or zero quantities were filtered out to avoid incorrect data points.
- **Revenue Calculation**: A new column, `Revenue`, was created by multiplying the `Quantity` and `UnitPrice` for each transaction.
- **Daily Revenue Aggregation**: The data was grouped by `InvoiceDate` to calculate the total revenue for each day.

### 2. Forecasting
To forecast the next 7 days of total revenue, we used **Prophet**, a time series forecasting model.

#### Why Prophet?
Prophet was chosen for the following reasons:
- **Ease of Use**: Prophet is designed to work with time series data, and it is user-friendly, requiring minimal data preparation.
- **Handles Seasonality**: The model is capable of handling daily, weekly, and yearly seasonality, making it a good choice for forecasting sales.
- **Robustness**: Prophet is known for its robustness in handling missing data and outliers, which is essential for real-world business data.
- **Flexibility**: Prophet allows for easy customization to include holidays or special events, though they were not necessary in this case.

### 3. Model Training & Prediction
- The data was passed to Prophet with the necessary columns (`ds` for dates and `y` for revenue).
- Prophet was trained on the historical data (from 01/12/2010 to 09/12/2011) to capture trends and seasonal patterns.
- We used `model.make_future_dataframe(periods=7)` to generate 7 future dates starting from 10/12/2011.
- The model was used to forecast total revenue for the next 7 days.

### 4. Results and Visualizations
- The forecasted revenue for the next 7 days was visualized using Prophet's built-in plotting functions.
- The predicted revenue values were presented along with confidence intervals (upper and lower bounds).

### 5. Forecast Output
- The predicted values for the next 7 days were shown, starting from `10/12/2011` (the day after the last available data).
- The forecast includes predicted revenue (`yhat`), with lower and upper confidence bounds (`yhat_lower`, `yhat_upper`).

## Files in the Repository
- **`notebooks/solution.ipynb`**: The Jupyter Notebook containing the full code implementation.
- **`data/sample.csv`**: A sample of the dataset used for the task.
- **`outputs/forecast_plot.png`**: The plot visualizing the forecasted daily revenue.

## Conclusion
This project demonstrates how time series forecasting can be used to predict sales revenue for an e-commerce retailer. Using Prophet, we successfully predicted future daily revenue based on historical transaction data.

## Libraries Used
- **pandas**: Data manipulation and preprocessing.
- **matplotlib**: Visualization of sales trends and forecasts.
- **prophet**: Time series forecasting model.


   
