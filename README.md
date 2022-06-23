# Bitcoin Prediction

## In an exploratory analysis, the goal was to create an algorithm to predict the price of bitcoin based on an analysis of market sentiment and technical indicators.

### 1) Market sentiment analysis via NLP :
- Reddit and Twitter were used.
- The tweets were collected according to the hashtags #BTC or #BITCOIN.
- During pre-processing, URLS and emails were removed.
- The mentions have been replaced by USER. Example : @Elon becomes USER.
- Special characters have been removed except for hashtags #.
- STOPWORDS have been removed and all words have been changed to lower case.
- Hashtags are checked to make sure they are in English.
- Tweets are sorted according to the number of retweets and likes.
- Tweets that are too short and not very popular are deleted.
- Use of the VADER algorithm to obtain a score and sentiment analysis via transfer learning. The score is composed of subjectivity, negativity, positivity, and neutrality.

### 2) Technical analysis of the market :
- To obtain technical indicators for the market, the Talib library was used. https://mrjbq7.github.io/ta-lib/
- These technical indicators are used to give traders the opportunity to take short or long positions.
- Different combinations of technical indicators were used to find out which ones would fit together best.

### 3) The different algorithms tried :
- Neural networks based on simple RNN, GRU, and LSTM have been designed to attempt to predict the price of BTC (linear regression) based on X number of days or hours before the prediction. 
- Machine Learning classification models were also used such as AdaBoostClassifier, DecisionTreeClassifier, SGDClassifier, KNeighborsClassifier, RandomForestClassifier, GradientBoostingClassifier, SVC, XGBClassifier As well as StackingClassifier and VotingClassifier models. In addition, GridSearchCV was used to find the best hyperparameters for the models.

### 4) Prediction windows tried :
- Different prediction windows have been tried on BTC prediction mainly in daily or hourly. Examples of windows: the previous 3 days to predict the 4th day. In sum, a multitude of combinations of different windows have been tried in days, hours, and minutes.
- The data was split in two ways: 
1) By taking the 80% of the data from the beginning of the data set as a train set (including the validation set) and the remaining 20% from the end of the data set as a test set.
2) With a shuffling function, the time sequences were taken in a completely random way for 80% of the data set as a train set (including the validation set) and the 20% of the test set as well.
Both methods were undertaken and compared in order to avoid data leakage.

### 5) Results :
- The results obtained after various strategies and attempts were able to match some scientific papers.
- Indeed, for a daily binary classification (i.e. whether one expects a rise or a fall at the next day's close) the result obtained was 66% accuracy on the test set. This result was obtained by combining the variables of the sentiment analysis with some technical indicators on a VotingClassifier model.
- These encouraging results show that with good input variables, it seems possible to predict the BTC market in a binary way (short or long) at more than 50% (baseline). 

### 6) Coming soon :
- A bot allowing the decision to go short or long depending on the environmental conditions is still in the process of being developed. The hope is that one day it will be able to go online and allow market positions to be taken according to the algorithm's predictions.
