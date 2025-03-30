# Text-Classification
My work is about classification MeSH mapped Root of research articles from PubMed by
using Abstract Text from each article focused on only Diseases [C] label. Data source which
using in this work is from PubMed MultiLabel Text Classification Dataset MeSH, uploaded by
Owais Ahmad and access from this link [PubMed MultiLabel Text Classification Dataset MeSH](https://www.kaggle.com/datasets/owaiskhan9654/pubmed-multilabel-text-classification)

## Working process are the steps as below:
1. Importing necessary libraries.
2. Getting data by downloading from my drive (public link) and reading data from the file.
3. Drop unused columns from dataframe, I am not using MeSH mapped Root which original
data do one-hot method which are column A-Z.
4. Drop row which has null value in any column, from checking, I found only one row with
null title. After this it's remaining the data total 9,999 rows.
5. Collecting unseen data for final evaluation by getting the last 10 rows from the
dataframe. There are 9,989 rows for training and 10 rows for final evaluation.
6. Exploring the data by getting a ‘meshroot’ column and an ‘abstracttext’ column from the
first row and second row.
7. Create a new column name ‘abstracttext_length’ to collect the length of text from the
‘abstracttext’ column for each row.
8. Create a new column name ‘is_diseases’ by calculating whether the ‘Diseases [C]’ is
contained in the ‘meshroot’ column or not. if it contains this column in this row will be
‘True’, if not, will be ‘False’.
9. Check the word cloud of the ‘abstracttext’ column to find the most frequent words.
10. Cleaning and preprocessing the data by removing rows which ‘abstacttext_length’ less
than 200 characters and which more than 2,000 characters.
11. Remove punctuation by collecting only the words which are not in the punctuation in the
‘abstracttext’ column.
12. Do lemmatization by splitting text in the ‘abstracttext’ column into a list of individual
words, using whitespace as the delimiter. Applies the lemmatizer to each word in the list
to convert it to its base form and joins the lemmatized words back into a single string,
with each word separated by a space.
13. Converting the data into vectors by using count vectorizer and TF-IDF vectorizer.
14. Split data to train and test for both vectors from count vectorizer and TFIDF vectorizer.
15. Using multinomial naive bayes model and decision tree model for training and predicting
data tests.
16. Evaluating the result from both models, countvectorizer got a f1-score 0.82 and TF-IDF
vectorizer got a f1-score 0.79.
17. Using unseen data to remove punctuation, do lemmatize and convert to vectors from
count vectorizer and TFIDF vectorizer. After that, predict data using multinomial naive
bayes model and decision tree model and check the result, count vector got a f1-score
0.90 and TF_IDF vector got a f1-score 0.70.