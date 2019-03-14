
# Project: Classifying Subreddit Posts
_Author: Daniel Stern_

## Problem Statement

Since as long as the internet has existed, people have been discussing (and/or arguing about) movies on it. And as the internet has grown in prominence as a media consumption platform, so to has its influence on the film industry at large. Not only have Netflix, Amazon Prime and Hulu (among others) emerged as major studios and distributors, but the internet has become an increasingly relevant advertising platform, as well as perhaps the most cost-efficient.

For more artistically-inclined films with smaller advertising budgets, the internet can be particularly benficial as an publicity tool, as it allows for targeted, relatively inexpensive advertising compared to more traditional mediums (TV, billboards, etc). But is there a way to distinguish between fans of certain types of films, based on the way they discuss (and/or argue about) films online?

Reddit has become the most popular discussion forum on the internet, with upwards of 11 million posts being generated every month, on average. Reddit is composed of specific "subreddits" about specific subject matter, which users can subscribe to. When it comes to movies, there are dozens of subreddits ranging from specific genres to the most popular subreddit, r/Movies, which currently has 3.6 million subscribers. Reddit can be an up-to-the-minute gauge for people's opinions on a particular subject, and it is also a relatively easy site to acquire data from via its API.

For this project, I will gather user posts and comments from r/TrueFilm and r/flicks, the 2nd and 3rd most popular movie subforums, and which appear to discuss distinctly different types of movies: More artistically-inclined "films" in the case of r/TrueFilm, and more popular "flicks", in the case of r/flicks. I will then train classification models on the data, and determine if the model can effectively distinguish whether a post was made in the "r/TrueFilm" forum.


## Executive Summary

The enclosed technical report analyzes posts and comments from the r/TrueFilm and r/flicks subrredits, to see whether there are patterns related to the text most commonly used within each subreddit, as well as whether or not a post/comment can be positively identified as being from the r/TrueFilm subreddit.

The classification problem suffered from an inherent class inbalance problem, meaning that there were significantly more samples with one label (in this case, r/TrueFilm posts). This meant that the most common classification metric, accuracy, was not relevant for this case, and the model instead would be optimized for precision score.

Ultimately, Logistic Regression was chosen as the best model (compared to Naive Bayes and Random Forest), as its probabalistic approach lead to co-efficients that seemed to make the most sense compared to the project's domain. The relationship between Precision (the target metric) and the confidence threshold also appeared to be more linear than with Naive Bayes or Random Forest, which seemed to exploit the class inbalance problem, and would likely be overfit when it came to unseen data.

### Contents:
- [Notebook 1 (Downloading JSON files from reddit)](./code/DownloadingJSONs_Notebook1.ipynb)
- [Notebook 2 (Combining JSON files for subreddit 1)](./code/CombineJSONsFlicks_Notebook2.ipynb)
- [Notebook 3 (Combining JSON files for subreddit 2)](./code/CombineJSONsTrueFilm_Notebook3.ipynb)
- [Notebook 4 (Merging text from subreddits)](./code/MergeTwoDatasets_Notebook4.ipynb)
- [Notebook 5 (Text Pre-processing)](./code/Preprocessing_Notebook5.ipynb)
- [Notebook 6 (Text Lemmatizing)](./code/Lemmatizing_Notebook6.ipynb)
- [Notebook 7 (EDA Dataset)](./code/EDAWordCount_Notebook7.ipynb)
- [Notebook 8 (Modeling with Logistic Regression)](./code/LogisticRegression_Notebook8.ipynb)
- [Notebook 9 (Modeling with Naive Bayes)](./code/NaiveBayesMultinomial_Notebook9.ipynb)
- [Notebook 10 (Modeling with Random Forest)](./code/RandomForest_Notebook10.ipynb)
- [Notebook 11 (Comparing Performance of Models)](./code/ModelAnalysis_Notebook11.ipynb)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)


## Conclusions & Recommendations

After analyzing the data, while there do appear to be patterns in how text is discussed between the two subreddits, the class imbalance problem makes it an inherently inconclusive use case.

Although the Random Forest did not appear to be a better choice than the Logistic Regression in this particular context, its high computational cost meant that it could only accept a limited amount of variables. It is possible that with more variables and/or hyperperameter tuning, that the Random Forest could be more effective.

I would also be interested in exploring web data from other sources, namely Letterboxd (marketed as a social media platform specifically for film fans), IMDB and twitter, which seems to be a thriving medium for film discussion.
