### Introduction:
This script uses pandas DataFrame structures and the Yahoo Finance api to identify potentially profitable securities for purchase and future sale.
The stock market is inherently chaotic and unpredictable, but we can use the tendency of chaotic variables to revert to their historical means to create generate predictions about the behavior of such variables.
The more extreme a variable's deviation from the norm, the more likely it is to return to a typical state, and the project uses this idea to identify securities with the greatest deviation and are therefore most likely to revert.
If you'd like to know more about the motivation behind this project and Mean Reversion generally, watch [this](https://www.youtube.com/watch?v=GMhVuZa6VtY) great youtube video from Fractal Manhattan.
### Script Overview:
The script begins by importing our libraries and loading the current date into a pandas Timestamp variable. We then define three functions, which, fetch stock data from yahoo finance, calculate moving averages, and calculate deviations from each moving average, respectively. We then load our ticker file (found in the repository) into a DataFrame and display its head to get a sense of the data. We briefly clean the data and define a final method, which consolidates the first three and returns a new DataFrame which contains the tickers and deviations for each symbol in the screener file. Finally, we sort the DataFrame to identify the most extreme deviations at a given window and display the head of the DataFrame.
### Future Additions
This script is not a full algorithmic trading strategy and still requires analysis on the part of the trader. Eventually this process can be streamlined through the implementation of several items:
#### 1. Machine Identification of Probable Reversion:
Not all stocks displayed by the script will revert, and implementation of ML classification models like Scikit-Learn, TensorFlow, or other libraries may be able to identify those with the greatest likelihood of reversion. We would also ideally account for error by diversifying our portfolio across many securities, proportionate to their probability of reversion.
#### 2. Implementation of Trading Apis:
In order to automate the trading process based on daily information, trading apis must be introduced in order to execute trades from the script environment.
#### 3. Implementation of Trade Exits: 
We also need to implement a trade exit point that will trigger a security to be sold. This issue will be discussed more in the applications & use section, but more research and experimentation should be done to determine where trade exit points should be set and what factors go into a reasonable exit point. This is also subject for future exploration with ML and neural networks.
### Installation & Execution
Execution of the script is as simple as loading the .ipynb file into a python notebook editing software such as Google Colab or Jupyter Notebook, loading the screener file into the environment (or accessing the file from local storage) and running the code. 
### Application & Use
Implementation of the script for practical trading purposes still requires human analysis of several factors. Firstly, not all securities identified by the algorithm will revert. Generally, there seem to be two classes of stocks with large magnitude deviations that are identified by the script. The first are stocks which are greatly deviated below their moving average because of a longer downtrend. The chance of reversion is within our ideal time frame is low because the fall in price is gradual, and the price remains below the moving average because of constant losses. The second class, which is appealing for our purposes, are stocks which are highly deviated below their moving average because of a sudden crash and have had an upward or horizontal trend. This is usually not too hard to identify from the graphs (I use graphs all the way from 1d to 5y), but it may take some practice, so make sure your trading strategy is solid in a simulator before trying anything with real money. Another issue that requires scrutiny from the trader is when to execute a trade exit. I've found that when there is an upward we can exit when the price reaches the pre-crash price. Justification for this is that we could hold securities for longer and hope for further growth and a continuation of the upward trend, but if we identify newly crashed stocks, their upward velocity will be greater and we can achieve greater returns than if we held our other positions for a longer time frame. When the price trend is downwards, exiting is harder, but we typically exit at anywhere from one eighth to one half the difference of pre and post-crash prices above the crash minimum. 
## License
This project is licensed under the terms of the MIT license.
