# Final Report: Data Mining on Bank Marketing Campaign
## Define the Problem
In this project, I would like to find a precise way to predict whether a bank’s phone call marketing campaign would make a specific client buy the product or not based on the client’s personal information, the campaign method information and the social and economic context attributes where the client is at. Another resulting information that could be obtained is that which piece of the information would have a relatively more important effect on the success of the phone call marketing campaign. 

## Identify the Client
The client would be a bank that would like to use phone call as a marketing campaign method to sell products. They want to reach out to people who have a higher campaign success rate and save time from reaching to the group of people that have a very low campaign success rate. They also care which specific way of phone call campaign tends to let people say yes to their products. Once they gathered the information about the clients, the campaign method that is going to use and their social and economic environment, they would be able to predict whether they would buy this product or not before making the phone call. This project could help them do a more targeted phone call campaign and help them understand which approach ways are in the clients’ favor. 

## Describe the Data Set
My data set is obtained from the UC Irvine Machine Learning Repository. It records 41,188 clients’ personal information, information of the marketing campaign phone call that reached them, their social and economic context attributes and whether the clients subscribed a term deposit or not in the end from a Portuguese banking institute. It can be downloaded directly from the website: http://archive.ics.uci.edu/ml/datasets/Bank+Marketing. There are both categorical variables and numerical variables in this data set and the output is categorical. A detailed information on variables is given below from the UCI Repository.
 
Input variables: 

1 - age (numeric)

2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')

3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)

4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')

5 - default: has credit in default? (categorical: 'no','yes','unknown')

6 - housing: has housing loan? (categorical: 'no','yes','unknown')

7 - loan: has personal loan? (categorical: 'no','yes','unknown')

8 - contact: contact communication type (categorical: 'cellular','telephone') 

9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')

10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')

11 - duration: last contact duration, in seconds (numeric). 

12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)

13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)

14 - previous: number of contacts performed before this campaign and for this client (numeric)

15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')

16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)

17 - cons.price.idx: consumer price index - monthly indicator (numeric) 

18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric) 

19 - euribor3m: euribor 3 month rate - daily indicator (numeric)

20 - nr.employed: number of employees - quarterly indicator (numeric)

Output variable (desired target):

21 - y - has the client subscribed a term deposit? (binary: 'yes','no')

## Data Wrangling
Before starting the data wrangling, I did some exploration on the data. I used bar charts, box plots and tables to discover the relationship between each variable and the output. For numerical variables, I did box plots to explore the relationship. For categorical variables, I calculated the success rate for output in each category of each variable and compare. For variables that their different categories or values seem to vary little on the success rate of output, they are included in the data set for now and will be examined again in the models on whether the accuracy of the model will improve by excluding them. Numerical variables are left at the same. Some categorical variables are separated by each category while the others regrouped some categories and then separated. For the columns from categorical variables, 0 represents absence and 1 represents presence. One of the columns from each categorical variable is excluded because its information can be obtained from other columns from this categorical variable. 

Categories that show similar success rate of output and are reasonable to combine are grouped together to reduce the number of features. For example, the marital situation initially has four categories: divorced, married, single and unknown and from the exploration result it is shown that the success percentages of output for divorced and married are very close, so I combine these two as “married current of before”. 
Categories that have very small size are also regrouped with other categories because leaving a small size category to represent one group would be bias. For example, illiterate only has a size of 18 people, so it is combined with basic.4y, basic.6y and basic.9y as “high school below”. 

Several columns of this data set have “unknown” values. Most of the unknown categories are treated as one separate category as the size is large enough to treat as a separate group. For some columns that have very few unknown values, the unknown category is combined with other categories as it will not affect much on the result. 

Dummy variable is the method I used here to separate different categories in each categorical column. Once the categorical column fed in, it returns several columns with each column regarded to one unique category. Inside the column, 0 represents absence for this category and 1 represents presence for this category. 

## Other Potential Data Sets
Kaggle has a data set that is taken from the data set I am using but it is balanced so that the amounts of 0s and 1s are about the same in this new data set. Although this data set do not have a size that is as large as the data set I am using, it might be able to emphasize more on dealing with the problem that the data is imbalanced (a lot more 0s than 1s) and the model tends to predict 1s much less accurate. 

## Initial Findings Using Statistics Methods
To explore the data and find the relationships between the variables and output, since the output is a categorical data set, if the variable is also categorical, I calculated the successful rate (getting “1”) of output for each category, sometimes also plotted the bar chart of rates and examine whether the difference in rates among all categories is significant or not; if the variable is numerical, I used side-by-side boxplots where x-axis is the numerical variable and y-axis is the two different output results. The exploration process is shown in “Capstone_Data_Exploration.ipynb” notebook. Now let us take a closer look to some examples in exploring the relationships between variables and the output. 

I first explored the relationship between age and output. A side-by-side boxplot is graphed to observe if there is any difference between the age distribution for clients said no and clients said yes on the output. From the graph, it is obvious that the age of clients answering yes had a wider range than the age of clients answering no. The medians do not have much difference. Therefore, the age might have some effect on the output but should not be a significant one.

Then I explored the relationship between education level and output. From the table that showed sorted calculated successful rates of output for each category, there are notable differences between different categories. The largest difference between two categories is around 14%. Then I grouped the categories to high school below and high school above and plotted a bar chart of these two new categories’ successful rate. From the chart, it is obvious that the education level should have a somewhat significant effect on the output. 

I also explored the relationship between contact month and output. I calculated the successful rates of output for each category. At first, I tried to group the months from March to December as just two groups: first half (March to July) and second half (August to December). After plotting the bar chart of successful rates for each month, I believe that some specific months should have significant effect on the output, such as March, September and December. Besides grouping them, it might be better to exclude some months as they do not quite vary the output. 

When exploring the relationship between phone call duration and output, although this variable was originally numerical since it shows the phone call duration in seconds, I combined them to two categories: 0-500 seconds and more than 500 seconds since anyone talking to the sales representatives above a certain line shows their willing to talk further. The difference in successful rates between these two categories is very large: about 35%, and shows a significant effect on the output. However, it is also notable that the duration is not known before a phone call is performed and at the end of the call the output is obviously known. This variable needs some more thinking in using in the predictive model.

There are also two variables that showed nearly no difference between categories in successful rates of the output: housing loan and personal loan. The successful rate appears to be around 10% no matter the clients have loans or not. There seems to be no relationship between these two variable and the output.  
 
I also explored the relationship between some of the variables. 
For example, I explored the relationship between marital situation and housing loan because I thought that married clients would tend to have a higher possibility in having housing loans. I calculated the rates of having housing loans for different categories (single, married, divorced and unknown) in marital situation and the result is surprising: the rate varied no more than 1% and the single clients tend to have a relatively higher rate of having housing loans. 

From the exploration, my initial findings are that most input variables have strong relationships with the output variable. Input variables do not seem to have much relationships between each other.

## In-depth Analysis Using Machine Learning
### Training Algorithms: 
There are three algorithms that have been used in this project: logistic regression, decision tree and random forest. To deal with this binary classification problem, I used logistic regression model first to observe if there is any unimportant feature that could be excluded from the data. Then I used decision tree to get a sense on how this algorithm would divide the data throughout the training process. Finally, I used random forest algorithm to see if I could get better performance by training decision trees ensemble. Also, this dataset has a large group of samples and not much features, which should be suitable for random forest application. 

### Criteria Tool:
The criteria tool used to evaluate the model’s performance is classification report, which shows the precision, recall, f1 score and support numbers of both output “yes” and output “no”. 
For this typical problem, precision and recall are both important, with precision means how many percentage of people that are predicted to subscribe a term deposit by the model really subscribed and recall means how many percentage of people that actually subscribed are predicted to subscribe a term deposit by the model. Hence, f1 score is used to determine which model would be better since it represents the harmonic mean of precision and recall. Since the data is imbalanced with much fewer “yes” outputs, I focused on the improvement of f1 score for output “yes” other than the average/total f1 score or output “no” f1 score. 

### Imbalanced Data:
Because this dataset is imbalanced with only 11% output being “yes” and others being “no”, I first compared the performance when class weight is balanced in the training model with the performance when class weight is not balanced in the training model. For logistic regression, comparing the f1 score for output “yes”, the model with class weight balanced performs better than the model with class weight not balanced. For decision trees, however, the model with class weight balanced showed a worse performance than the model without class weight balanced. 

### Cross Validation: 
Since the data set is large, I randomly shuffle the data and then split the data to 70% training set, 20% validation set and 10% test set. Training set is used for fitting the model, validation set is used to validate the performance of the fitted model and test set is for the final comparison between models. 

### Data Normalization: 
In logistic regression, because it is assigning coefficients for features, the range of each features would also affect the coefficients and prediction results. Hence, StandardScaler is used to normalize the data. To ensure the validate and test sets are not seen until they are used, training set is used to fit the standard scaler and then the parameters such as mean and standard deviation for training is used to standardize the validate and test sets. 

### Hyperparameters Tuning:
In each model training, GridSearchCV method is used to tune hyperparameters. 5-fold cross validation is used in grid search and the scoring function uses accuracy classification score.

### Results Analysis: 
For logistic regression, when the class weight is balanced, the f1 score of output “yes” increases 0.09 comparing with the score when the class weight is not balanced. In the model that class weight is balanced, three most unimportant features which have very low coefficients are unemployed in job, unknown in personal loan and unknown in housing loan and three most important features are employment variation rate, duration and consumer price index. These results about features importance are similar to what I see in the data exploration before training. After excluding unimportant features that have coefficients lower than 0.02, the f1 score of output “yes” stays the same but the recall score increases 0.01 comparing with the classification report for model fitted with all the features. 

For decision tree, the f1score of output “yes” for model fitted with all the features is 0.03 higher than the score for model fitted excluding some unimportant features. In the decision tree graphs, number of employees and duration are always the first two features to be chosen to split the data. 

For random forest, theoretically it should result in better performance than decision tree as it trains individual trees in parallel and output the mode of the classes while also adds randomness in feature selection. However, in this case, random forest has a f1 score for output “yes” 0.01 lower than the score of decision tree. After printing the classification report for training data, it is shown that random forest is a bit overfitting. Max depth for classification is already tuned and some other regularization method could be used to deal with the overfitting. Another reason could be that the number of features are much smaller than the number of samples and decision tree is reasonably stable, so that adding randomness and training more trees to find the mode will not do much to the improvement of performance. 
