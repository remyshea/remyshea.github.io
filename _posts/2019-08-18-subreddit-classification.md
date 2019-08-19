---
title: "Subreddit Classification"
date: 2019-08-18
tags: [natural language processing, classification, data science]
excerpt: "Subreddit Classification"
mathjax: true
---
# Subreddit Classification
## Distinguishing between AITA and TIFU posts

Remy Shea, April 2019

This was analysis was performed during my time at General Assembly Seattle's Data Science Immersive program. The code for this project can be seen on my GitHub, [here](https://github.com/remyshea/subreddit-classification).

---

<iframe src="{{ site.url }}{{ site.baseurl }}/assets/pdfs/Subreddit Classification.pdf" frameborder="0" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true">
</iframe>

---
## Abstract
In this project, the Reddit API was used to gather text-based data for a classification problem. Two corpora were assembled, consisting of documents which were individual user-made submissions to one of the two popular, and somewhat similar subreddits `/r/amitheasshole` and `/r/tifu` respectively.<br> Of the many classification algorithms used to model the data, a Adaptive Boosting model with 60 estimators and a learning rate of 0.8 performed best. The model achieved an accuracy score of 96.1% on testing data, which was about a relative 2% increase in performance compared to the average model which achieved 94.3% accuracy.

---
## Libraries
- `numpy`
- `pandas`
- `matplotlib.pyplot`
- `seaborn`
- `requests`
- `time`
- `regex`
- `stopwords` from `nltk`'s `corpus` library
- `CountVectorizer` & `TfidfVectorizer` from `sklearn`'s `feature_extraction.text` library
- `Pipeline` from `sklearn`'s `pipeline` library
- `train_test_split`, `GridSearchCV` & `RandomizedSearchCV` from `sklearn`'s `model_selection` library
- `LogisticRegression` from `sklearn`'s `linear_model` library
- `DecisionTreeClassifier` from `sklearn`'s `tree` library
- `GradientBoostingClassifier`, `AdaBoostClassifier`, `RandomForestClassifier` and `BaggingClassifier` from `sklearn`'s `ensemble` library
- `KNeighborsClassifier` from `sklearn`'s `neighbors` library
- `MultinomialNB` from `sklearn`'s `naive_bayes` library
- `SVC` from `sklearn`'s `svm` library
- `accuracy_score`, `roc_auc_score` and `confusion_matrix` from `sklearn`'s `metrics` library

---
## Outline
The challenge was to build a model that could correctly predict whether a document belonged to one of the two corpora based upon its text features. In layman's terms, the question we are trying to answer is this:
> Could we tell the difference between a TIFU post and a AITA post?
---
## Background

If we are to interpret results from this analysis, it is necessary for us to understand the differences between the two subreddits in the first place.
### /r/tifu
The subreddit `/r/tifu` is a very popular subreddit whose name is an acronym for the humble admission: "Today, I F***ed Up". The sub has 14.2 million subscribers at the time of the analysis, and can see hundreds of posts a day. Posters to this subreddit seek comfort in their darkest, most embarassing hour by trying to put on a good show; partaking in the fanciful retelling of their most recent cringe-inducing moments to an audience of Schadenfreude-hungry redditors. The posts are lengthy text segments, detailing every step of the build up to the OP's (original poster) disasterous mess-up and they typically describe the painfully awkward aftermath as well. The tone is characterized by a notable humility, and a light-heartedness that befits a situation where the catastrophe is so bad, all that you can do is step back and laugh at yourself.


### /r/amitheasshole
The subreddit `/r/amitheasshole`, often abbreviated 'AITA', is in some ways the opposite of `/r/tifu`. The sub has a much smaller 632 thousand subscribers. Posters to this subreddit typically come seeking an ostensibly impartial third party council of random internet strangers to adjudicate on a recent situation in the OP's life that could not be solved through conventional means like logic, and conversation. These are almost always in interpersonal relationships, and forms an interesting divergence from TIFU in that way (posts to TIFU can often be embarassing incidents that happen alone, when no one is watching. Doesn't make the embarassment sting any less, however). The posts also tend to be much lengthier, with the OP laying out their side of an argument or difficult situation, and in the comments, redditors weight in on whether or not they think the OP is the 'a**hole' in that situation. The mood is characterized often by a confrontational, defensive, and sometimes accusatory tone. This forms the basis for the comparison carried out here.

---
## Process

The project followed a relatively simple datascience workflow
1. Define the Problem
  - Can we classify between posts belonging to the subreddits /r/tifu and /r/amitheasshole?
2. Obtain the Data
  - Using Reddit's API, collect and extract text documents from .JSON files
  - Tokenize and clean the data, apply appropriate preprocessing steps
3. Explore the Data
  - Examine the efficacy of the two preprocessing method, choose one
  - Compare the relative frequencies of words in the common vocabularies of both subreddits
4. Model the Data
  - For each model, fit to the training data using a grid search or randomized search
5. Evaluate the Model
  - Score the model's performance over a series of metrics on the 'unseen' training data
6. Answer the Problem
  - Examine the models, extract the best performer, and answer the question: Can we classify between posts belonging to the subreddits /r/tifu and /r/amitheasshole?

---
## Results
The ultimate result is an emphatic yes: we can indeed determine whether a document of text belongs to one of /r/tifu or /r/amitheasshole. We can do so with around 96% accuracy using an adaptive boosting classifier comprised of 60 decision trees and a learning rate of 0.8. That being said, many alternative models also performed rather well, and the reason for choosing the AdaBoost classifier over other models was purely because of it's slightly better performance, with not much regard to interpretability.

---
## Discussion

I think this project was an interesting exploration of interacting with an API, being responsible for the gathering of data all the way through to the very end in answering the question we pose ourselves. I would have liked more time to examine the effect of different types of inputs beyond merely text features into our models, as well as perhaps taking a closer look at the overlap, and interesting divergence in the vocabularies of the two very similar subreddits.

Additionally, using these models to predict entirely novel sources of text, like for example entirely different subreddits to estimate their proximity to either one or the other of the two examined subreddits would have been indeed very interesting. Finally, I would be interested in taking a closer look at the posts that the model incorrectly classified; perhaps there is some common theme among them, whose nature can be capture by another input to my model? I may return to this project at another time.
