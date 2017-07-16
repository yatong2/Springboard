# Data Mining on Bank Clients’ Personal Information

## The problem to solve:
  In this project, I would like to know if we could predict whether a person has a typical loan or not from other personal information such as his/her age, education, marital status and economic situation, and which would have a relatively more important effect on having the typical loan or not. 

## Potential client and why would they care: 
  The client could be a bank that would like to market on their loans. They want to reach out to people who does not have loans yet because if he/she already has one then there might be a lower probability he/she would get another loan. If they know a typical group of people tend to not have loans, they can reach out to them. 

## Data Set Information: 
  I am going to use the bank marketing data set from UCI Machine Learning Repository. It records clients’ personal information as well as direct phone call marketing campaign information and results of a Portuguese banking institute. It can be downloaded directly from the website. http://archive.ics.uci.edu/ml/datasets/Bank+Marketing

## Approach: 
  I am going to use the bank-additional.csv with 20 inputs and drop the inputs that are related to the phone call campaign. For the string type inputs, I will use dummy variables method to separate the categories in each input, leaving each column only with “yes” and “no”, and then convert “yes” and “no” to 1 and 0. I would need to combine or delete some categories of some inputs after data exploration. Then I will split the data to 70% training data, 20% validation data and 10% test data. I plan to use around three algorithms such as support vector machine, artificial neural network and random forest to train the data and tune the hyper parameters, and then compare the performance among the three. 

## Deliverables: 
  The deliverables of this project will be the code for data cleaning and rearrangement as well as for data training, validation and testing and a report or paper explaining the project idea, process, final results and applications. 
