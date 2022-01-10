# Twitter-Sentiment-Analysis:
[Twitter-Sentiment-Analysis Database](https://www.kaggle.com/paoloripamonti/twitter-sentiment-analysis/data)
- This project is a Twitter sentiment analysis with natural language processing. Our database includes 1.6 million tweets and each one is labeled as negative or positive. (800000 negative tweets and 800000 positive tweets). I used 200k to train our model. 
- First of all, I cleaned the data to exclude the useless vocabulary, symbols, numbers… `Script Line 78-281`
```
Data cleaning includes:
-Making statement text in lower case
-HTML decoding: for  ‘&amp’,’&quot’,etc.
-Removing ‘@’ users
-Removing URL links
-Removing Encoding Errors
-Removing hashtag/numbers
-Clearing the Personal Pronoun, ‘the’, and other common words that with no meanings
-Removing short words that less than 1 letter (I feel ‘hmm’ and ‘oh’ may be useful for the test, so I am going to keep them)
-Applying Stemming
-Applying Lemmatization
```
- I did a data visualization and exploratory analysis then. I checked the frequency of the words appearing in the 200k tweets and find the more useless words from the word cloud. And then, I excluded more words, having 77701 different words totally.`Script Line 285 can load the cleaned data directly, data analysis is from Line 298-337`
- To vectorize the text, I used three types of representations: `Script Line 341-365`
```
-One-Hot text data representation: (frequency is 0 or 1)
-CV: transform a given text into a vector-based on the frequency (count) of each word that occurs in the entire text.
-TF-IDF: evaluates how relevant a word is to a document in a collection of documents, the value is not an integer.
```
- Apply models include: `Script Line 399-1257`
```
-Naive Bayes: I used each of one-hot, cv, and TF-idf text representation (feature extraction) methods to do a BernoulliNB and MultinomialNB comparison.
 These two are most common in NLP. Using multinomial for binary classification is not recommended though, I did it to see the difference. (Script Line 399-463)
-KNN                	                  (Script Line 479-617)
-CART               	                  (Script Line 621-770)
-Random Forest	                          (Script Line 773-809)
-Linear Logistic Regression with/without PCA: (L2 regularization with the SAG optimization method, L1 lasso regularization with SAGA optimization method). 
 PCA reduced features from 2500 to 875.   (Script Line 812-1090)
-Neural network with/without PCA:          (Script Line 1121-1257)
```
