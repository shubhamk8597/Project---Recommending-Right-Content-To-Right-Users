# Project---Recommending-Right-Content-To-Right-Users
## Introduction
In this notebook I have taken a old kaggle comepetition of Careervillage.org. The problem statement was to recommend relevant questions to relevant professionals. Referring to already solved solutions I have combined edited and tried to make my solution concise effective and efficient. Going through the datasets we clearly see that "questions", "answers", "professionals" and "tags" are important and relevant for our goal.
Starting with loading the data and doing some feature extraction to add some new interesting columns for future analysis we continue our EDA(Exploratory Data Analysis . After getting the required insights we use LDA for our Topic Modelling. With this we build our recommendations which solve only a specific question.
**How to recommend relevant questions to relevant professionals so that they are motivated to answer.**

## EDA - Explotary Data analyisis
### Tag relation
Th The x-axis is how many professionals have subscribe the tag and the y-axis is in how many students have subscribed to the tag. The Size of he bubble indicates how many questions have these tags. The most related tags used by many of the users is college with 15.6 % of questions containing it. Around 4 % of professionals and 1.5 % of students use it. Even though the numbers are ow they are high relatively The top tag for professionals is telecommunications on the right site with about 11% but the tag doesn't appear in many questions or students subscription.
