# Data Mining on A Bank’s Phone Call Marketing Campaign

## The problem to solve:
  In this project, I would like to find a great way to predict whether the phone call marketing campaign would be successful based on the clients’ personal information, such as education and economic situation, and on the campaign information, such as call time and duration. Another result could be shown is that which piece of information would have a relatively more important effect on the success of phone call marketing campaign.  

## Potential client and why would they care: 
  The client could be a bank that would like to use phone call as a marketing campaign method. They want to reach out to people who have a higher campaign success rate and save time from reaching to the group of people that have a very low campaign success rate. They also care which specific way of phone call campaign tends to let people say yes to their products. This project could help them do a more targeted phone call campaign and help them understand which approach ways are in clients’ favor. 

## Data Set Information: 
  I am going to use the bank marketing data set from UCI Machine Learning Repository. It records clients’ personal information as well as direct phone call marketing campaign information and results of a Portuguese banking institute. It can be downloaded directly from the website. http://archive.ics.uci.edu/ml/datasets/Bank+Marketing

## Approach: 
  I am going to use the bank-additional.csv with 20 inputs. For the string type inputs, I will first explore the data and delete some categories that is underrepresented or barely have any effect on campaign success as well as combine some similar categories together, then I will use dummy variables method in pandas to separate the left categories in each column, leaving each of them only with 1 for “yes” and 0 for “no”. Then I will split the data to 70% training data, 20% validation data and 10% test data. I plan to use around three algorithms such as support vector machine, artificial neural network and random forest to train the data, then tune the hyper parameters use validation data, and finally compare the performance by running test data among the three.  

## Deliverables: 
  The deliverables of this project will be the code for data exploration, data cleaning and rearrangement as well as data training, validation and testing. A report or paper explaining the project idea, process, final results and applications will also be written.  
