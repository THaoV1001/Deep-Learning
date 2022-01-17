# LSTM Stock Predictor

![deep-learning.jpg](Images/deep-learning.jpg)

Due to the volatility of cryptocurrency speculation, investors will often try to incorporate sentiment from social media and news articles to help guide their trading strategies. One such indicator is the [Crypto Fear and Greed Index (FNG)](https://alternative.me/crypto/fear-and-greed-index/) which attempts to use a variety of data sources to produce a daily FNG value for cryptocurrency. You have been asked to help build and evaluate deep learning models using both the FNG values and simple closing prices to determine if the FNG indicator provides a better signal for cryptocurrencies than the normal closing price data.

In this assignment, you will use deep learning recurrent neural networks to model bitcoin closing prices. One model will use the FNG indicators to predict the closing price while the second model will use a window of closing prices to predict the nth closing price.

You will need to:

1. [Prepare the data for training and testing](#prepare-the-data-for-training-and-testing)
2. [Build and train custom LSTM RNNs](#build-and-train-custom-lstm-rnns)
3. [Evaluate the performance of each model](#evaluate-the-performance-of-each-model)

- - -

### Files

lstm_stock_predictor_closing.ipynb

lstm_stock_predictor_fng.ipynb

- - -

## Analysis 

Below is the shared inputs of both models: 

Epochs = 80
Batch Size = 10

1. LSTM Model using previous Closing Price

With Window Size = 10, the MSE is 0.0026

A number of Window Size has been iterated through to assess whether there are any significant changes in MSE as Window Size changes. 

Result is summarised below: 

Window Size = 10 -> MSE = 0.0026
Window Size = 8  -> MSE = 0.0072
Window Size = 6  -> MSE = 0.0053
Window Size = 4  -> MSE = 0.0102
Window Size = 2  -> MSE = 0.0040

From the above iterations, it seems that Window Size = 10 offer the most accurate prediction with lowest MSE

2. LSTM Model using previous Fear and Greed Index FNG

With Window Size = 10, the MSE is 0.1339

A number of Window Size has been iterated through to assess whether there are any significant changes in MSE as Window Size changes. 

Result is summarised below: 

Window Size = 10 -> MSE = 0.1339
Window Size = 8  -> MSE = 0.1389
Window Size = 6  -> MSE = 0.1276
Window Size = 4  -> MSE = 0.1330
Window Size = 2  -> MSE = 0.1309

From the above iterations, it seems that Window Size = 6 offer the most accurate prediction with lowest MSE

## Conclusion

Question: Which model has a lower loss?
Answer: After comparing multiple iterations of Window Size, the LSTM Model using previous Closing Price has a much lower loss. This indicates a better fit. 

Question: Which model tracks the actual values better over time?
Answer: From the line chart plot at the end of each analysis notebook, the LSTM Model using previous Closing Price track the actual values better over time because the predicted values are closer to actual values. 

Question: Which window size works best for the model?
Answer: After comparing multiple interations of Window Size, Window Size = 10 works best when previous Closing Prices are used whereas Window Size = 6 works best when previous FNG Values are used in the LSTM Model. 