### Purpose
The idea behind the presented project was to see if there was a substantive difference between the content posted on two sub-reddits, r/AskMen and r/AskWomen. The differences could manifest in various ways, but a few that I sought to look at were language, sentiment, and content of both questions asked and answers given. This information could prove valuable in a variety of ways depending on the goals of the reader. For more concrete uses, discovering which language to use to target each gender for marketing purposes, the optimum amount of emotion to embue titles with for maximum appeal, and which items/topics would make for good marketing ideas due to buyer uncertainty. More conceptually, this project could prove interesting for highlighting which are the most common topics of misunderstanding between men and women and whether or not the way men and women communicate digitally is different.

### Data Gathering
To gather the data for this research, I used Jupyter Notebooks and the Praw library to scrape Reddit's API. From r/AskMen and r/AskWomen, I collected the text from the top 1000 posts from the past month and the top comment from each respective post. This represented the top questions asked to Men or Women (from either gender) and the top responses from the gender to which the question was posed. Thus we cannot assume the questions are posed solely across genders (women to men or men to women), but we can reasonably assume that the top comment was made by gender of the corresponding subreddit (men on r/AskMen, women on r/AskWomen).

### Data Cleaning
During the data cleaning, there were a few hiccups that caused the number of posts and comments to drop slightly below 1000. Several threads were reposts and has to be excised, and a number of threads had no top comments due to comments being locked. However, the number of each remained above 950.

### Modeling
To quantify the differences between r/AskMen and r/AskWomen, I attempted a number of different classification models. I created four different Pipelines that utilized GridSearch with three cross validations to trial the optimum hyperparameters. The Pipelines used either a Count Vectorizor or TF-IDF to isolate the individual words, then used either Logistic Regression or Random Forest methods to classify the data. Ultimately the best result utilized TF-IDF with 5000 max features and (1, 1) n-gram range and Logistic Regression with an l2 penalty, and scored 0.637. This means that the model has a 63.7% chance to correctly identify if a post or comment is on r/AskMen or r/AskWomen.

### Interesting Finds
The most interesting find in my opinion is that since the best model only scored .637 and the baseline score is .502, there isn't a substantive difference in the language or topics between the two subreddits. However, given the other findings of exploring the data, it isn't very surprising. After performing sentiment analysis, the amount of emotion used in the questions asked on each subreddit is almost identical. The responses of men are a little more neutral than the responses of women, but once again are almost the same. Unsurprisingly men and women were in the top 3 words used in r/AskMen and r/AskWomen respectively. Otherwise, the top 20 words used in the questions and answers were the same in the both subreddits. Though, interestingly 'sex' was one of the most used words in the questions in r/AskMen, while not in r/AskWomen, and 'love' was the same for r/AskWomen but not r/AskMen. When looking at words that were the best predictors for if the post/comment was in r/AskMen, some interesting top results were 'shit', 'sex', 'fix', 'respect', and 'wrong'. Some of the best predictors for whether a post was in r/AskWomen were 'experience', 'love/loved', 'period', 'white', 'black', 'free', 'career', and 'buy'. 