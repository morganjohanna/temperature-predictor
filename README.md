# Temperature Predictor
*Predicting the temperature from weather data with an autoregressive model*

This project was about using autoregressive models to predict the average daily weather temperature.

The data were from a custom query of ECA&D's daily data; they were blended from the station Berlin-Tempelhof in Germany and contained only temperature data, the date, and an indication of data quality; the original dataset is included in this repo. Berlin-Tempelhof was chosen because, except for 1945, there are reliable weather data going back to 1876, providing a substantial and stable dataset. You can find more updated data from https://www.ecad.eu/

The final result I achieved was a model with a 90.8% accuracy score in test and a mean temperature of 4.6°C predicted for 01 Feb 2023. The recorded temperature at the same station for that day was also 4.6, so I consider this a happy success! 

## Modules
This repository contains:

├── ar_model.ipynb  
├── cleaning_regression.ipynb  
├── data  
│   └── TG_STAID002759.txt  
├── LICENSE  
├── output  
│   ├── weather_clean.csv  
│   └── weather_remainder.csv  
├── README.md  

Of note are the following:
- **cleaning_regression.ipynb** is where the data were cleaned and linear regression (taking trend, seasonality, and remainder into account) performed including dummy encoding months, and data stability validation with the Augmented Dickey-Fuller test. This file produces the 2 .csv files in the **output** directory: a clean dataset and one containing only the remainder. It includes the regression model utilized for the prediction.
- **ar_model.ipynb** includes a different autoregressive model with 4 lags rather than only one. This isn't really in use at the moment and is saved more as a placeholder than anything, as something for me to come back to in the future to experiment with predicting further in the future than only 1 day.

## Next
This project was focused on experimenting with different AR models, not so much on actual output. Out of curiosity, I'd love to experiment with continuing the predictions to see how far in the future my model can reliably predict recorded weather (e.g. with more lags). Other weather phenomenon like precipitation would also be fun to add in.

I'd also like to think on the issue of what constitutes an "accurate" prediction, and find ways to automatically consider a prediction within e.g. 1° Celsius of the actual recorded temperature as correct. This would need to be considered both for testing (with TimeSeriesSplit) and predictions themselves.