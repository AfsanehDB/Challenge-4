Analyzing Portfolio Risk and Return
In this Challenge, you'll assume the role of a quantitative analyst for a FinTech investing platform. This platform aims to offer clients a one-stop online investment solution for their retirement portfolios that’s both inexpensive and high quality. (Think about Wealthfront or Betterment). To keep the costs low, the firm uses algorithms to build each client's portfolio. The algorithms choose from various investment styles and options.

You've been tasked with evaluating four new investment options for inclusion in the client portfolios. Legendary fund and hedge-fund managers run all four selections. (People sometimes refer to these managers as whales, because of the large amount of money that they manage). You’ll need to determine the fund with the most investment potential based on key risk-management metrics: the daily returns, standard deviations, Sharpe ratios, and betas.

Instructions
Import the Data
Use the risk_return_analysis.ipynb file to complete the following steps:

Import the required libraries and dependencies.

Use the read_csv function and the Path module to read the whale_navs.csv file into a Pandas DataFrame. Be sure to create a DateTimeIndex. Review the first five rows of the DataFrame by using the head function.

Use the Pandas pct_change function together with dropna to create the daily returns DataFrame. Base this DataFrame on the NAV prices of the four portfolios and on the closing price of the S&P 500 Index. Review the first five rows of the daily returns DataFrame.

Analyze the Performance
Analyze the data to determine if any of the portfolios outperform the broader stock market, which the S&P 500 represents. To do so, complete the following steps:

Use the default Pandas plot function to visualize the daily return data of the four fund portfolios and the S&P 500. Be sure to include the title parameter, and adjust the figure size if necessary.

Use the Pandas cumprod function to calculate the cumulative returns for the four fund portfolios and the S&P 500. Review the last five rows of the cumulative returns DataFrame by using the Pandas tail function.

Use the default Pandas plot to visualize the cumulative return values for the four funds and the S&P 500 over time. Be sure to include the title parameter, and adjust the figure size if necessary.

Answer the following question: Based on the cumulative return data and the visualization, do any of the four fund portfolios outperform the S&P 500 Index?

Analyze the Volatility
Analyze the volatility of each of the four fund portfolios and of the S&P 500 Index by using box plots. To do so, complete the following steps:

Use the Pandas plot function and the kind="box" parameter to visualize the daily return data for each of the four portfolios and for the S&P 500 in a box plot. Be sure to include the title parameter, and adjust the figure size if necessary.

Use the Pandas drop function to create a new DataFrame that contains the data for just the four fund portfolios by dropping the S&P 500 column. Visualize the daily return data for just the four fund portfolios by using another box plot. Be sure to include the title parameter, and adjust the figure size if necessary.

Hint Save this new DataFrame—the one that contains the data for just the four fund portfolios. You’ll use it throughout the analysis.

Answer the following question: Based on the box plot visualization of just the four fund portfolios, which fund was the most volatile (with the greatest spread) and which was the least volatile (with the smallest spread)?

Analyze the Risk
Evaluate the risk profile of each portfolio by using the standard deviation and the beta. To do so, complete the following steps:

Use the Pandas std function to calculate the standard deviation for each of the four portfolios and for the S&P 500. Review the standard deviation calculations, sorted from smallest to largest.

Calculate the annualized standard deviation for each of the four portfolios and for the S&P 500. To do that, multiply the standard deviation by the square root of the number of trading days. Use 252 for that number.

Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of the four fund portfolios and of the S&P 500 index. Be sure to include the title parameter, and adjust the figure size if necessary.

Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of only the four fund portfolios. Be sure to include the title parameter, and adjust the figure size if necessary.

Answer the following three questions:

Based on the annualized standard deviation, which portfolios pose more risk than the S&P 500?

Based on the rolling metrics, does the risk of each portfolio increase at the same time that the risk of the S&P 500 increases?

Based on the rolling standard deviations of only the four fund portfolios, which portfolio poses the most risk? Does this change over time?

Analyze the Risk-Return Profile
To determine the overall risk of an asset or portfolio, quantitative analysts and investment managers consider not only its risk metrics but also its risk-return profile. After all, if you have two portfolios that each offer a 10% return but one has less risk, you’d probably invest in the smaller-risk portfolio. For this reason, you need to consider the Sharpe ratios for each portfolio. To do so, complete the following steps:

Use the daily return DataFrame to calculate the annualized average return data for the four fund portfolios and for the S&P 500. Use 252 for the number of trading days. Review the annualized average returns, sorted from lowest to highest.

Calculate the Sharpe ratios for the four fund portfolios and for the S&P 500. To do that, divide the annualized average return by the annualized standard deviation for each. Review the resulting Sharpe ratios, sorted from lowest to highest.

Visualize the Sharpe ratios for the four funds and for the S&P 500 in a bar chart. Be sure to include the title parameter, and adjust the figure size if necessary.

Answer the following question: Which of the four portfolios offers the best risk-return profile? Which offers the worst?

Diversify the Portfolio
Your analysis is nearing completion. Now, you need to evaluate how the portfolios react relative to the broader market. Based on your analysis so far, choose two portfolios that you’re most likely to recommend as investment options. To start your analysis, complete the following step:

Use the Pandas var function to calculate the variance of the S&P 500 by using a 60-day rolling window. Visualize the last five rows of the variance of the S&P 500.
Next, for each of the two portfolios that you chose, complete the following steps:

Using the 60-day rolling window, the daily return data, and the S&P 500 returns, calculate the covariance. Review the last five rows of the covariance of the portfolio.

Calculate the beta of the portfolio. To do that, divide the covariance of the portfolio by the variance of the S&P 500.

Use the Pandas mean function to calculate the average value of the 60-day rolling beta of the portfolio.

Plot the 60-day rolling beta. Be sure to include the title parameter, and adjust the figure size if necessary.

Finally, answer the following two questions:

Which of the two portfolios seem more sensitive to movements in the S&P 500?

Which of the two portfolios do you recommend for inclusion in your firm’s suite of fund offerings?

Import the Data
Step 1: Import the required libraries and dependencies.
import numpy as np
# Import the required libraries and dependencies
Step 2: Use the read_csv function and the Path module to read the whale_navs.csv file into a Pandas DataFrame. Be sure to create a DateTimeIndex. Review the first five rows of the DataFrame by using the head function.
# Import the data by reading in the CSV file and setting the DatetimeIndex 
# Review the first 5 rows of the DataFrame
Step 3: Use the Pandas pct_change function together with dropna to create the daily returns DataFrame. Base this DataFrame on the NAV prices of the four portfolios and on the closing price of the S&P 500 Index. Review the first five rows of the daily returns DataFrame.
()
# Prepare for the analysis by converting the dataframe of NAVs and prices to daily returns
# Drop any rows with all missing values
# Review the first five rows of the daily returns DataFrame.
Quantitative Analysis
The analysis has several components: performance, volatility, risk, risk-return profile, and portfolio diversification. You’ll analyze each component one at a time.

Analyze the Performance
Analyze the data to determine if any of the portfolios outperform the broader stock market, which the S&P 500 represents.

Step 1: Use the default Pandas plot function to visualize the daily return data of the four fund portfolios and the S&P 500. Be sure to include the title parameter, and adjust the figure size if necessary.
figsize=(10, 7), title=
# Plot the daily return data of the 4 funds and the S&P 500 
# Inclue a title parameter and adjust the figure size
Step 2: Use the Pandas cumprod function to calculate the cumulative returns for the four fund portfolios and the S&P 500. Review the last five rows of the cumulative returns DataFrame by using the Pandas tail function.
# Calculate and plot the cumulative returns of the 4 fund portfolios and the S&P 500
# Review the last 5 rows of the cumulative returns DataFrame
Step 3: Use the default Pandas plot to visualize the cumulative return values for the four funds and the S&P 500 over time. Be sure to include the title parameter, and adjust the figure size if necessary.
# Visualize the cumulative returns using the Pandas plot function
# Include a title parameter and adjust the figure size
Step 4: Answer the following question: Based on the cumulative return data and the visualization, do any of the four fund portfolios outperform the S&P 500 Index? Answer No, none of the funds outperform S&P500.
&P500. 
**Question** Based on the cumulative return data and the visualization, do any of the four fund portfolios outperform the S&P 500 Index?
Analyze the Volatility
Analyze the volatility of each of the four fund portfolios and of the S&P 500 Index by using box plots.

Step 1: Use the Pandas plot function and the kind="box" parameter to visualize the daily return data for each of the four portfolios and for the S&P 500 in a box plot. Be sure to include the title parameter, and adjust the figure size if necessary.
# Use the daily return data to create box plots to visualize the volatility of the 4 funds and the S&P 500 
# Include a title parameter and adjust the figure size
Step 2: Use the Pandas drop function to create a new DataFrame that contains the data for just the four fund portfolios by dropping the S&P 500 column. Visualize the daily return data for just the four fund portfolios by using another box plot. Be sure to include the title parameter, and adjust the figure size if necessary.
figsize=(10, 7)
# Create a new DataFrame containing only the 4 fund portfolios by dropping the S&P 500 column from the DataFrame
# Create box plots to reflect the return data for only the 4 fund portfolios
# Include a title parameter and adjust the figure size
Step 3: Answer the following question: Based on the box plot visualization of just the four fund portfolios, which fund was the most volatile (with the greatest spread) and which was the least volatile (with the smallest spread)?
Question Based on the box plot visualization of just the four fund portfolios, which fund was the most volatile (with the greatest spread) and which was the least volatile (with the smallest spread)?

Answer Most volatile is Lakeshire Hathaway inc and least volatile is Tiger Global Management

Analyze the Risk
Evaluate the risk profile of each portfolio by using the standard deviation and the beta.

Step 1: Use the Pandas std function to calculate the standard deviation for each of the four portfolios and for the S&P 500. Review the standard deviation calculations, sorted from smallest to largest.
.
# Calculate and sort the standard deviation for all 4 portfolios and the S&P 500
# Review the standard deviations sorted smallest to largest
Step 2: Calculate the annualized standard deviation for each of the four portfolios and for the S&P 500. To do that, multiply the standard deviation by the square root of the number of trading days. Use 252 for that number.
# Calculate and sort the annualized standard deviation (252 trading days) of the 4 portfolios and the S&P 500
# Review the annual standard deviations smallest to largest
Step 3: Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of the four fund portfolios and of the S&P 500 index. Be sure to include the title parameter, and adjust the figure size if necessary.
=
# Using the daily returns DataFrame and a 21-day rolling window, 
# plot the rolling standard deviation of the 4 portfolios and the S&P 500
# Include a title parameter and adjust the figure size
Step 4: Use the daily returns DataFrame and a 21-day rolling window to plot the rolling standard deviations of only the four fund portfolios. Be sure to include the title parameter, and adjust the figure size if necessary.
# Using the daily return data and a 21-day rolling window, plot the rolling standard deviation of just the 4 portfolios. 
# Include a title parameter and adjust the figure size
Step 5: Answer the following three questions:
Based on the annualized standard deviation, which portfolios pose more risk than the S&P 500?

Based on the rolling metrics, does the risk of each portfolio increase at the same time that the risk of the S&P 500 increases?

Based on the rolling standard deviations of only the four fund portfolios, which portfolio poses the most risk? Does this change over time?

Question 1 Based on the annualized standard deviation, which portfolios pose more risk than the S&P 500?

Answer 1 S&p 500 is the most volietile investement after that BERKSHIRE HATHAWAY INC

Question 2 Based on the rolling metrics, does the risk of each portfolio increase at the same time that the risk of the S&P 500 increases?

Answer 2 not neceserly, some of the funds showing very stedy changes. just BERKSHIRE HATHAWAY INC showing some degry of following S&P 500 trend

Question 3 Based on the rolling standard deviations of only the four fund portfolios, which portfolio poses the most risk? Does this change over time?

Answer 3 BERKSHIRE HATHAWAY INC is the most risky ifund after S&P 500. yes it is changing over time. funds had more stedy time between mide 2016- mide 2018. between 1015 -2016 Soros fund was more Volitel

Analyze the Risk-Return Profile
To determine the overall risk of an asset or portfolio, quantitative analysts and investment managers consider not only its risk metrics but also its risk-return profile. After all, if you have two portfolios that each offer a 10% return but one has less risk, you’d probably invest in the smaller-risk portfolio. For this reason, you need to consider the Sharpe ratios for each portfolio.

Step 1: Use the daily return DataFrame to calculate the annualized average return data for the four fund portfolios and for the S&P 500. Use 252 for the number of trading days. Review the annualized average returns, sorted from lowest to highest.
# Calculate the annual average return data for the for fund portfolios and the S&P 500
# Use 252 as the number of trading days in the year
# Review the annual average returns sorted from lowest to highest
Step 2: Calculate the Sharpe ratios for the four fund portfolios and for the S&P 500. To do that, divide the annualized average return by the annualized standard deviation for each. Review the resulting Sharpe ratios, sorted from lowest to highest.
# Calculate the annualized Sharpe Ratios for each of the 4 portfolios and the S&P 500.
# Review the Sharpe ratios sorted lowest to highest
Step 3: Visualize the Sharpe ratios for the four funds and for the S&P 500 in a bar chart. Be sure to include the title parameter, and adjust the figure size if necessary.
tio")
# Visualize the Sharpe ratios as a bar chart
# Include a title parameter and adjust the figure size
Step 4: Answer the following question: Which of the four portfolios offers the best risk-return profile? Which offers the worst?
Question Which of the four portfolios offers the best risk-return profile? Which offers the worst?

AnswerTiger Global Management has the best risk return followed by Berkshire hathaway, Paulson& CO.INC has the worth risk return

Diversify the Portfolio
Your analysis is nearing completion. Now, you need to evaluate how the portfolios react relative to the broader market. Based on your analysis so far, choose two portfolios that you’re most likely to recommend as investment options.

Use the Pandas var function to calculate the variance of the S&P 500 by using a 60-day rolling window. Visualize the last five rows of the variance of the S&P 500.
# Calculate the variance of the S&P 500 using a rolling 60-day window.
For each of the two portfolios that you chose, complete the following steps:
Using the 60-day rolling window, the daily return data, and the S&P 500 returns, calculate the covariance. Review the last five rows of the covariance of the portfolio.

Calculate the beta of the portfolio. To do that, divide the covariance of the portfolio by the variance of the S&P 500.

Use the Pandas mean function to calculate the average value of the 60-day rolling beta of the portfolio.

Plot the 60-day rolling beta. Be sure to include the title parameter, and adjust the figure size if necessary.

Portfolio 1 - Step 1: Using the 60-day rolling window, the daily return data, and the S&P 500 returns, calculate the covariance. Review the last five rows of the covariance of the portfolio.
()
# Calculate the covariance using a 60-day rolling window 
# Review the last five rows of the covariance data
Portfolio 1 - Step 2: Calculate the beta of the portfolio. To do that, divide the covariance of the portfolio by the variance of the S&P 500.
# Calculate the beta based on the 60-day rolling covariance compared to the market (S&P 500)
# Review the last five rows of the beta information