### Introduction
This script uses pandas DataFrame structures and the Yahoo Finance api to identify potentially profitable securities for purchase and future sale.
The stock market is inherently chaotic and unpredictable, but we can use the tendency of chaotic variables to revert to their historical means to create generate predictions about the behavior of such variables.
The more extreme a variable's deviation from the norm, the more likely it is to return to a typical state, and the project uses this idea to identify securities with the greatest deviation and are therefore most likely to revert.
If you'd like to know more about the motivation behind this project and Mean Reversion generally, watch [this](https://www.youtube.com/watch?v=GMhVuZa6VtY) great video from Fractal Manhattan.
### Script Overview
The script begins by importing our libraries and loading the current date into a pandas Timestamp variable. We then define three functions, which, fetch stock data from yahoo finance, calculate moving averages, and calculate deviations from each moving average, respectively. We then load our ticker file (found in the repository) into a DataFrame and display its head to get a sense of the data. We briefly clean the data and define a final method, which consolidates the first three and returns a new DataFrame which contains the tickers and deviations for each symbol in the screener file. Finally, we sort the DataFrame to identify the most extreme deviations at a given window and display the head of the DataFrame.
### Future Additions
This script is not a full algorithmic trading strategy and still requires analysis on the part of the trader. Eventually this can be eliminated through the implementation of several items:
#### 1. Identification of Probable Reversion:
Not all stocks identified by the script will revert, and implementation of ML classification models like scikit-learn, TensorFlow, or other libraries may be able to classify those with the greatest likelihood of reversion. 
#### 2. Implementation of Trade Cut-off

### Installation & Execution
### Application & Use
