# Project---Recommending-Right-Content-To-Right-Users
## Overview
In this notebook I have taken a old kaggle comepetition of Careervillage.org. The problem statement was to recommend relevant questions to relevant professionals. Referring to already solved solutions I have combined edited and tried to make my solution concise effective and efficient. Going through the datasets we clearly see that "questions", "answers", "professionals" and "tags" are important and relevant for our goal.

Starting with loading the data and doing some feature extraction to add some new interesting columns for future analysis we continue our EDA(Exploratory Data Analysis) . After getting the required insights we use LDA for our Topic Modelling. With this we build our recommendations which solve only a specific question.
**How to recommend relevant questions to relevant professionals so that they are motivated to answer.**

#### LDA Visualization
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/17.PNG)
#### Topic Similarity
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/18.PNG) 
### Data Description
CareerVillage.org has provided several years of anonymized data and each file comes from a table in their database.

**answers.csv**: Answers are what this is all about! Answers get posted in response to questions. Answers can only be posted by users who are registered as Professionals. However, if someone has changed their registration type after joining, they may show up as the author of an Answer even if they are no longer a Professional.

**comments.csv**: Comments can be made on Answers or Questions. We refer to whichever the comment is posted to as the "parent" of that comment. Comments can be posted by any type of user. Our favorite comments tend to have "Thank you" in them :)

**emails.csv**: Each email corresponds to one specific email to one specific recipient. The frequency_level refers to the type of email template which includes immediate emails sent right after a question is asked, daily digests, and weekly digests.

**group_memberships.csv**: Any type of user can join any group. There are only a handful of groups so far.

**groups.csv**: Each group has a "type". For privacy reasons we have to leave the group names off.

**matches.csv**: Each row tells you which questions were included in emails. If an email contains only one question, that email's ID will show up here only once. If an email contains 10 questions, that email's ID would show up here 10 times.

**professionals.csv**: We call our volunteers "Professionals", but we might as well call them Superheroes. They're the grown ups who volunteer their time to answer questions on the site.

**questions.csv**: Questions get posted by students. Sometimes they're very advanced. Sometimes they're just getting started. It's all fair game, as long as it's relevant to the student's future professional success.

**school_memberships.csv**: Just like group_memberships, but for schools instead.

**students.csv**: Students are the most important people on CareerVillage.org. They tend to range in age from about 14 to 24. They're all over the world, and they're the reason we exist!

**tag_questions.csv**: Every question can be hashtagged. We track the hashtag-to-question pairings, and put them into this file.

**tag_users**.csv: Users of any type can follow a hashtag. This shows you which hashtags each user follows.

**tags.csv**: Each tag gets a name.

**question_scores.csv**: "Hearts" scores for each question.

**answer_scores.csv**: "Hearts" scores for each answer.




## EDA - Explotary Data analyisis
### 1 - Tag relation
Th The x-axis is how many professionals have subscribe the tag and the y-axis is in how many students have subscribed to the tag. The Size of he bubble indicates how many questions have these tags. The most related tags used by many of the users is college with 15.6 % of questions containing it. Around 4 % of professionals and 1.5 % of students use it. Even though the numbers are ow they are high relatively The top tag for professionals is telecommunications on the right site with about 11% but the tag doesn't appear in many questions or students subscription.
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/1.png)
### 2 - Word cloud for students, professionals and question tags 
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/2.png) ![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/3.png)
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/4.png)

### 3 - Question response time
We have to see how many days do professionals take to respond to answer questions and how has it changed over the years. We see that most answers get answered in the first day and they drop as the week passes/ Over the year the question respone time drops till 2018 and we see a sight increase in 2019.
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/5.png)
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/6.png)

### 4 - Email response time
Here we see how effective are the emails for engaging the professionals. We only include the questions that were answered. As we can see ven though the professionas have a weekly email they respond to the questions instantly as soon as they recieve the email. So sending emails is an effective way for professionals to be engaging.
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/7.png)

### 5 - Mean Respose Time
Here We see how over the years the mean respose time has graduallly decreased even thoug the response time in days has increased. It can be because old questions are geting answered or due to increase in the user base
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/8.png)

## Topic Modelling using LDA
Searching libraries to solve our problesm we had a few different approaches like LSA(Latent Semantic Analysis) and PLSA(Probabilistic Latent Semantic Analysis), but as of now LDA is best suited for our problem statement. We can use it to see how topics are relating questions to each other and to the professionals who answered them or are subscribed to a specific tag. We will have the following steps.

**1 - NLP on the merged questions**

  a. POS tagging to get only specific meaningful words
  
  b. Document term frequencies
  
  c. TF- IDF Inverse document term frequencies
  
**2 - LDA Model.**

**3 - Headline for the topics that are obtained**

**4 - Probability of different topics in a question text**

### Parameters
Gensim library have the LDA model module. Exploring many parameters we came down to the ones that are relevant to our problem statement. Being an unsupervised approach we have to check the results by tuning the parameters

## Topics after LDA 
In LDA we do not get a specific topic. We only get similar topics so its upto us what topic headline we have to give.
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/11.png)![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/12.png)![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/13.png) 

As we can see

Topic 0 can be called **Medical**

Topic 2 Can be called **Law**

Topic 4 Can be called **Business Management** and so on..
### Interactive LDA Visvualization
pyLDAvis is a great tool to visvualize LDA and understand it.This is a screenshot of the following 
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/17.PNG)

### Examples of topic similarity highlighted with probability 
Here we input questions and highlight the topics in each question and map in on a pie chart
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/18.PNG)

![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/19.PNG)

## Recommending Questions to Professionals
## Similar questions
For this task it is important to identify similar questions. We have two functions
1 - Get similar text questions :
    We use NLP to filter out meaningful important words by using POS tagging       and calculating TF-IDF. And then with the help of cosine similarity we get     similar text.
2 - Get similar tag questions :
    We use the Jaccard smiliarity on the hashtags used while writing the           questions
    
## Recommendations
### Recommending Questions to Professionals
**Similar questions**
For this task it is important to identify similar questions. We have two functions  

1 - Get similar text questions : We use NLP to filter out meaningful important words by using POS tagging and calculating TF-IDF. And then with the help of cosine similarity we get similar text. 

2 - Get similar tag questions : We use the Jaccard smiliarity on the hashtags used while writing the questions

**Recommendations**
There are many questions and it is therefore currently difficult for an professional to find questions which he could answer. To recommend relevant questions to him, we look which questions he has already answered and which hashtags he has subscribed to. Scores are calculated on the basis of these to provide a better recommendation. The individual scores can be weighted differently (e.g. the similarity is more important than the number of answers), to calculate the final score.

**final_score= ∑𝑠∈𝑆(𝑠𝑤𝑒𝑖𝑔ℎ𝑡∗𝑠𝑣𝑎𝑙𝑢𝑒) **
**S= All defined Scores (similarity, question date, ...)**

**𝑠𝑤𝑒𝑖𝑔ℎ𝑡  = The weight for score s**

**𝑠𝑣𝑎𝑙𝑢𝑒  = The calculated base score for score s**

We prefer high scores, so it is necessary for some to adjust them. e.g. questions should be preferred which do not have many answers yet. The multiplicative inverse is then used for these **( 𝑠𝑣𝑎𝑙𝑢𝑒→1/𝑠𝑣𝑎𝑙𝑢𝑒 )** . We also using the logarithm (actual base 10) to normalize the scores. On some score it's helpfull to add the base self bevor calculate the logarithm. For some scores it's helpful to add the base itself before calculate the logarithm. The following scores exists:

**similarity**: How similar are the questions to the already answered questions or hashtags? score_similarty = cosine similarity between question and new question

**question date**: How old is the question?

score_date_added =  **𝑙𝑜𝑔10(𝑣𝑎𝑙𝑢𝑒)**  with value= The days that have passed since the question was asked.

**answers**: How many answers have the question already?

score_answers = **1/𝑙𝑜𝑔10(10+𝑣𝑎𝑙𝑢𝑒)**  with value= The amount of answers for the question.

**tags**: Jaccard similiarty between the question hashtags and the professional subscribed hashtags?

score_tags = **𝑇𝑞∩𝑇𝑝/𝑇𝑞∪𝑇𝑝 ** with **Tq= Question Tags and Tp= Professional Tags.**

### Example 1 - A random professional who has been registered for a while
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/20.PNG)

### Example 2 - A newly registered professional with only hashtangs and no answered questions.
![](https://github.com/shubhamk8597/Project---Recommending-Right-Content-To-Right-Users/blob/main/'/Images'/21.PNG)

## Conclusion
We started with examining the data and then extracting features to the data which would be of our use. Then we did a thorough EDA which gave more insights on the relation between different parameters. The Bubble Chart between student tags, professional tags and question tags made a basis for our further model. The email response time and the mean response time made clear that emails are good for engagement of the professionals.

After that we cleaned the data using NLP techniques using Spacy library and sorted out important words in a sentence which could now be used to determine topics for the questions or to calculate textual similarity between questions.

We then went on and built LDA model in Gebsim library for recommending questions to professionals via mail as it is the most effective and engaging way. Much more imporvement can be done but here we focused only on a specific task of recommending relevant questions to professionals via mail which will make them motivated to answer it.

## Reference and Credits
Daniel Becker - https://www.kaggle.com/danielbecker/careervillage-org-recommendation-engine/notebook
Ivan Didur - https://www.kaggle.com/ididur/nn-based-recommender-engine
