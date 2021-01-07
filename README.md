# HACKATHON - Project 4: John Lawless
---
The data used:
### Classification

- [Predicting a Biological Response](https://www.kaggle.com/c/bioresponse/data)


# Methods/findings
- Briefly, it can be stated that this was a very enjoyable dataset! Upon brief analysis, it appears that most of the features were very weak learners. I decided to apply a multitude of different classifiers, to evaluate what worked best and what did not, before turning my attention to fine tuning. My initial thought was to focus on a neural network. The reason for this is that I wanted a high powered estimator that would have a decent chance to find signal among a group of weak learners. This worked tolerably well.

- A large breakthrough came about after recognizing that more is not always better - I decided to sort my features by strength of correlation, take the 15 with a correlation closest to 1, and 15 closest to -1, with my target feature. This improved the scoring of all of my models, particularly becuase the metric given to me in the competition was log_los (the same as binary crossentropy), which is a metric evaluation of the accuracy of probabilities in a classification model. 

- To my surprise, at the end of the day, a Gradient Boosted Classifier proved to be the best estimator of all of the ones I used. Given that high variance and bias was a constant battle, it appears that fitting a model on the residuals of a previous decision tree was the best method of maximizing accuracy on unseen data, and minimizing the log_loss.

[my_scores](Kaggle.png)

My best score, using a Gradient Boosted Classifier on my "best" learners, yielded a log_loss of 0.46944. The good news is that this is only about 0.11 off from the best Kaggle score!! ...The more realistic news, of course, is that this was sufficient to put me in about 500th place. Still, this was a great exercise in learning how to find signal when it isn't immediatley obvious where to look.