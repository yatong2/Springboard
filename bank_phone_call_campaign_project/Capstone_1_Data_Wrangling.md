## Capstone project 1 – data wrangling 

Before starting the data wrangling, I did some exploration on the data. I used bar charts, box plots and tables to discover the relationship between each variable and the output. For numerical variables, I did box plots to explore the relationship. For categorical variables, I calculated the success rate for output in each category of each variable and compare. For variables that their different categories or values seem to vary little on the success rate of output, they are included in the data set for now and will be examined again in the models on whether the accuracy of the model will improve by excluding them. 

Numerical variables are left at the same. Some categorical variables are separated by each category while the others regrouped some categories and then separated. For the columns from categorical variables, 0 represents absence and 1 represents presence. One of the columns from each categorical variable is excluded because its information can be obtained from other columns from this categorical variable. 

### Regrouping: 
Categories that show similar success rate of output and are reasonable to combine are grouped together to reduce the number of features. For example, the marital situation initially has four categories: divorced, married, single and unknown and from the exploration result it is shown that the success percentages of output for divorced and married are very close, so I combine these two as “married current of before”. 

Categories that have very small size are also regrouped with other categories because leaving a small size category to represent one group would be bias. For example, illiterate only has a size of 18 people, so it is combined with basic.4y, basic.6y and basic.9y as “high school below”. 

### Unknown values: 
Several columns of this data set have “unknown” values. Most of the unknown categories are treated as one separate category as the size is large enough to treat as a separate group. For some columns that have very few unknown values, the unknown category is combined with other categories as it will not affect much on the result. 

### Dummy variable method: 
Dummy variable is the method I used here to separate different categories in each categorical column. Once the categorical column fed in, it returns several columns with each column regarded to one unique category. Inside the column, 0 represents absence for this category and 1 represents presence for this category. 
