## Using Inferential Statistics Techniques to Explore Data:
### Correlation between variables and output:
To explore the data and find the relationships between the variables and output, since the output is a categorical data set, 
if the variable is also categorical, I calculated the successful rate (getting “1”) of output for each category, 
sometimes also plotted the bar chart of rates and examine whether the difference in rates among all categories is 
significant or not; if the variable is numerical, I used side-by-side boxplots where x-axis is the numerical variable and 
y-axis is the two different output results. The exploration process is shown in “Capstone_Data_Exploration.ipynb” notebook. 
Now let us take a closer look to some examples in exploring the relationships between variables and the output. 

I first explored the relationship between age and output. A side-by-side boxplot is graphed to observe if there is any 
difference between the age distribution for clients said no and clients said yes on the output. From the graph, it is obvious 
that the age of clients answering yes had a wider range than the age of clients answering no. The medians do not have much 
difference. Therefore, the age might have some effect on the output but should not be a significant one.

Then I explored the relationship between education level and output. From the table that showed sorted calculated successful 
rates of output for each category, there are notable differences between different categories. The largest difference between 
two categories is around 14%. Then I grouped the categories to high school below and high school above and plotted a bar 
chart of these two new categories’ successful rate. From the chart, it is obvious that the education level should have a 
somewhat significant effect on the output. 

I also explored the relationship between contact month and output. I calculated the successful rates of output for each 
category. At first, I tried to group the months from March to December as just two groups: first half (March to July) and 
second half (August to December). After plotting the bar chart of successful rates for each month, I believe that some 
specific months should have significant effect on the output, such as March, September and December. Besides grouping them, 
it might be better to exclude some months as they do not quite vary the output. 

When exploring the relationship between phone call duration and output, although this variable was originally numerical 
since it shows the phone call duration in seconds, I combined them to two categories: 0-500 seconds and more than 500 seconds 
since anyone talking to the sales representatives above a certain line shows their willing to talk further. The difference 
in successful rates between these two categories is very large: about 35%, and shows a significant effect on the output. 

There are also two variables that showed nearly no difference between categories in successful rates of the output: housing 
loan and personal loan. The successful rate appears to be around 10% no matter the clients have loans or not. 
There seems to be no relationship between these two variable and the output.  
 
### Correlation between variables:
I also explored the relationship between some of the variables. 
For example, I explored the relationship between marital situation and housing loan because I thought that married 
clients would tend to have a higher possibility in having housing loans. I calculated the rates of having housing loans 
for different categories (single, married, divorced and unknown) in marital situation and the result is surprising: the 
rate varied no more than 1% and the single clients tend to have a relatively higher rate of having housing loans. 
