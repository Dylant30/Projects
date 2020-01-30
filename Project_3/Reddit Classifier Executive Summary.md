**<u>Joke or not?</u>**

What would be worst than to be scrolling through jokes on reddit for a good laugh, but instead finding oneself being scared by a campfire ghost story? Regardless whether it was intentional or accidental, it would not end well for the faint hearted, or a sleepless night for the rest. 

While we have had human moderators policing these threads, it is getting tougher and tougher for the moderators to be able to keep up with the pace. With more users and posters by the day, it has been apparent that an automated system is needed to correctly classify the posts to reduce these kinds of misclassifications.



Luckily, there is the field of natural language processing (NLP) which can be used to aid us in our classification system. Recently, there has been many breakthroughs in the field and has allowed it to be widely used throughout many industries to assist in their tasks which involves interactions with texts or the spoken language, which is very similar to our posts classification problems. 

After web scraping the data from Reddit's API from our two targeted subreddits (**Jokes** and **Nosleep**), the data is combined into a single file, where the focus would be the title of the post (**Title**), the content of the post (**Self_text**) and the subreddit that it belongs to (**Subreddit**). Combining the title and the content of the text of each post a single long post (**Text_features**), the data is then split into a training and testing set which will then be fed to the models for training.



Four models are trained and tested and their results is recorded in the table below, from which we can deduce that the most accurate model would be the **Logistic Regression model with TF-IDF**.

| Model                                     | Score      |
| ----------------------------------------- | ---------- |
| Logistic Regression (Count Vectoriser)    | 0.9953     |
| **Logistic Regression (TF-IDF)**          | **0.9976** |
| Multinomial Classifier (Count Vectoriser) | 0.8957     |
| Multinomial Classifier (TF-IDF)           | 0.9004     |

With an accuracy score of **99.76%**, this model is nearly perfect when it comes distinguishing a joke from a horror story (it was incorrect twice out of 422 times). This is supported by looking at the coefficients of each word, where the model showed that it was able to identify a group of words strongly with horror stories (where the coefficients were greater than 1).

While not perfect, it would be an valuable tool to deliver near instantaneous results, which would make reddit a safer place for the faint hearted and moderation a much simpler task.