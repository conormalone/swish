# Swish Analytics Project

Predict when a soccer player will win a foul on a possession based on EPL 15/16 event data

## model selection

For this model I used LSTM to predict foul won on a sequence of events.
LSTM are commonly used in text generation to predict the next word in a sentence, in this context a possession is a sentence of football events.
feature selection

for features I wanted a simple model that used the events most likely to lead to a foul.

the final features selected were:

    *pressure event (binary)
    *dribble event (binary)
    *dribble past event (binary)
    *event duration (float)

I also looked at event flags for Carry and Euclidean distance of start and end point of carry but these both reduced model quality.
model architecture

as the population of possessions with a foul won is a tiny fraction of the total,
accuracy **(true positive + true negative/all predictions)** would bias towards marking every possession as No Foul for that reason the best metrics to use are Precision **(true positive/true postive + false positive)** and Recall **(true positive/true positive + false negative)**

## Results

the model was tuned to maximise F1-Score or Balanced Accuracy and the best result in this case was 30%. However the model could be tuned to increase Recall (capture more of the population of fouls won) at the expense of increasing false positives. 
![ROC Charts](https://github.com/user-attachments/assets/fbb2013e-7ab2-4af7-93ca-71b8b52fe488)

