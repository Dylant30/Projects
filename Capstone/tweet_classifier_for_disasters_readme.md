**<u>Tweet Classifier for Disasters</u>**

**Goal**: Creating a filter to sieve through twitter for disaster-related tweets.

**Intended use**: For government agencies/emergency response teams to filter through social media for information that would be relevant for their use

**Outline**: Classifier models will be used to filter through tweets and assign a label whether a tweet is related to disasters or not (binary classification). Model will be trained on a dataset and evaluated based on their accuracy score (number of correct predictions).

<u>Dataset</u>

Source: Kaggle (https://www.kaggle.com/c/nlp-getting-started), which is sourced from FigureEight (https://www.figure-eight.com/data-for-everyone/)

Train data contains <u>7613</u> tweets with labels (whether it is a disaster or not).

Test data contains <u>3263</u> tweets.

<u>Models</u>

Classification Models: Logistic, Multinomial Naive-Bayes, RandomForestClassifier

Neural Network Model: Bidirectional Encoder Representations from Transformers (BERT)

<u>Cleaning & Preparation</u>

For classification models: Tweets are stripped of their URLs, stopwords (from nltk.corpus) are removed and only the words which are 2 characters long are kept. It is then vectorized using Count Vectorizer and TF-IDF Vectorizer separately, which is then split into the training and validation data before being sent to the model. The best performing vectoriser/model combination will be selected.

For BERT: Tweets are stripped of their URLs and twitter handles before being sent to BERT's tokenizer to be tokenized. Once tokenized, the token IDs are returned and then padded so that all the inputs will have the same length. The attention masks are then created before being split into the training and validation dataset. After splitting, the inputs (tweets as token IDs and the attention masks) are then converted to tensor data before being loaded into a dataloader file, ready for modelling.

<u>Running the models</u>

For classification models: For each model, a Gridsearch is performed to obtain the best parameters for the model and the vectorizer (Count Vectorizer or TF-IDF Vectorizer), where the parameters with the highest score for each model will be kept (results shown below)

| Model:            | Logistic Regression | Multinomial Naive-Bayes | RandomForestClassifier |
| ----------------- | ------------------- | ----------------------- | ---------------------- |
| Count Vectorizer  | 79.22%              | 80.43%                  | 60.31%                 |
| TF-IDF Vectorizer | 80.43%              | 80.43%                  | 63.65%                 |

For BERT: The pre-trained sequence classification model from HuggingFace is loaded. Model is fine-tuned to the training data and its labels on a Google Colab Notebook (GPU required for tensor data) where it returned a validation score of **<u>83.6%</u>**.

<u>Training Validation</u>

The Logistic Regression and Multinomial Naive-Bayes model obtained eerily similar best accuracy scores, though the sensitivity and specificity rates are slightly different. RandomForestClassifier on the other hand, falls short. BERT trumps both Logistic Regression and Multinomial Naive-Bayes in classification accuracy, so it will be the model selected.

<u>Testing</u>

Another seperate dataset, CrisisLexT6 (https://crisislex.org/data-collections.html), will be used to test the models predictive performance.

| Model                   | Score             |
| ----------------------- | ----------------- |
| Logisitic Regression    | 74.31%            |
| Multinomial Naive-Bayes | 72.99%            |
| BERT                    | **<u>85.45%</u>** |



<u>Conclusion</u>

BERT has been the most outstanding performer for all scenarios, returning the highest accuracy score on the training validation and for the CrisisLex T6 test dataset. As it is a pre-trained model, the ease of just being able to download and run a state-of-the-art language model fine tune it for a specific tasks is way easier and more effective than building a language model from scratch, knowing that it will have a tough time dealing with unseen data. 

