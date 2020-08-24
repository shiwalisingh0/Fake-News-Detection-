# Fake News Detection Using Natural Language Processing (NLP) and Classification Modeling
## *Distinguishing Between Subreddit Posts From the r/TheOnion & r/nottheonion*
--------
 - [Abstract](#Abstract)
 - [Methodology](#Methodology)
 
 
## Abstract
Early in 2019, WhatsApp announced it was deleting over 2 million accounts a month to prevent the rampant spread of fake news.<sup>[1](https://www.theguardian.com/technology/2019/feb/06/whatsapp-deleting-two-million-accounts-per-month-to-stop-fake-news)</sup> Their decision came after incidents of violent attacks in India were triggered by the spread of fake news on the messaging platform.<sup>[2](https://wired.com/story/how-whatsapp-fuels-fake-news-and-violence-in-india/)</sup> I was curious about how WhatsApp created their fake news filter, so I made one myself using open source data from Reddit. I scraped around 30,000 posts from subreddits [r/TheOnion](https://www.reddit.com/r/TheOnion/) and [r/nottheonion](https://www.reddit.com/r/nottheonion/) and built a classification model that could distinguish between fake news from r/TheOnion and absurd news from r/nottheonion. While building this model, I optimized for accuracy. That is, I wanted to have the highest possible outcomes of True Negatives and True Positives, and least amount of False Positives and False Negatives. The worse scenario is deleting an account or post that shares authentic news, mistaking it for fake news. After cleaning, analyzing, and performing NLP functions to the data, I created optimal classification models using Pipeline and GridSearch to help me determine the best parameters for my model. The classification model with the highest accuracy score of 90% vectorized the data using `CountVectorizer(ngram_range= (1, 3))` and trained the data using `MultinomialNB(alpha = 0.36)`. Additionally, to interpret coefficients of the model, I used `CountVectorizer(stop_words = custom)` & `LogisticRegression(C = 1.0, solver='liblinear')`. See more of my findings in the Model Evaluation section of this Readme.   

## Methodology
To build a classification model to distinguish between Subreddit posts from r/TheOnion and r/nottheonion, I implemented a nonlinear data science workflow.<br>

| Data Science Workflow       | Description                                                                                                                                                                         |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Data Acquisition**            | Scrape ~15k posts from r/TheOnion & r/nottheonion, total of ~30k posts. Used pushshift.io API wrapper to acquire data. Clean the data.                                              |
| **Exploratory Data Analysis**   | Create data visualizations to observe trends about the data. What are distinguishing characteristics about each subreddit?                                                          |
| **Natural Language Processing** | Prepare text for modeling. Count Vectorize the data and analyze trends among posts.                                                                                                 |
| **Modeling**                    | Using Pipeline and GridSearch, find the best combination of vectorizers and models to achieve the best accuracy when designating a post as either from r/TheOnion or r/nottheonion. |
