# Milestone Report: Data Mining on Airbnb New User Bookings
## Define the problem
The problem in this project is that where would the new users book their first booking based on their personal information (gender, age, etc.) and web activity information (signup method, affiliate channel, first browser, etc.). This is a multiclass classification problem.
## Identify the client
Airbnb or other websites for vacation rentals would be the potential client. They would like to predict the places that new users mostly likely would book for first booking so that they could push notifications or send promotions about this specific place. In this case, because these places interest the new users, the new users would have a higher possibility to book in their website or to start their first booking in a shorter time.
## Describe the data set
The data set is obtained from the Airbnb new users booking Kaggle competition website. Only the train_users_2 csv file is used. It records 213,451 new users’ personal information and their web activity information as well as their country destination of first booking. It can be downloaded directly from the website: https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings. There are categorical variables, numerical variables and time series variables in this data set. The output country destination contains multiple classes. A detailed information on variables is given below: 
-	id: user id
- date_account_created: the date of account creation
-	timestamp_first_active: timestamp of the first activity, note that it can be earlier than date_account_created or date_first_booking because a user can search before signing up
-	date_first_booking: date of first booking
-	gender
-	age
-	signup_method
-	signup_flow: the page a user came to signup up from
-	language: international language preference
-	affiliate_channel: what kind of paid marketing
-	affiliate_provider: where the marketing is e.g. google, craigslist, other
-	first_affiliate_tracked: whats the first marketing the user interacted with before the signing up
-	signup_app
-	first_device_type
-	first_browser
-	country_destination: target variable 
## Data wrangling
Before starting the data wrangling, I did some exploration on the data. I used bar charts, distribution plots and tables to explore the categories in each categorical variable and the relationship between some input variables and the output. Then data wrangling was done based on the results found from data exploration. 

For categorical variables, dummy variable method is used for separating categories and the first category is dropped to avoid high correlation among features. Each category is usually left alone unless the size of the category is very small and it is reasonable to combine with another or some other categories. In the first device variable, desktop(other), mobile(other) and other/unknown are combined as one group. 

There are three time series variables in the dataset. At first, I considered to add them into the features. For first active time and account create time, I calculated the gap between these two and did a value count. For the first booking time, I extracted the year and month for each entry and appended to two separate lists. For the data that does not have first booking time, I left them as nan values. However, the value count result showed that even I counted for gap days, most of the entries are still zero. The year and month for first booking should also be removed since the problem here is to predict where would a new user’s first booking be and at that time the first booking time would not be known. Hence, all the three time series variables are not included in the features. 

There is only one numerical variable: age in the input variables. Consider that about half of the entries are nan values, I did not leave this variable as numerical values but rearranged them as categories. Ages higher than 95 or lower than 18 are grouped with nan values, ages between 18 and 29 are grouped as young people, ages between 30 and 54 are grouped as middle age people and ages between 55 and 95 are grouped as old people. 
## Other potential data sets that could use
In this Kaggle competition, Airbnb also gives out the session data set which includes a lot more web activity information for new users. This data set could be concatenated with the train data set to have more features for prediction.
## Initial findings using statistics methods
Firstly, I calculated what percentage of the data set is nan values and found that nearly 60% of the new users do not have first booking dates, about 45% of the new users do not have gender values and about 42% of the new users do not have valid age values. The other variable that has nan values is first affiliate tracked but it only contains about 2% nan values. 

From the bar chart of country destination value counts, it is shown that more than half of the entries are NDF, which means the new user has not booked yet. Also, for all the new users that had their first booking, about half of them went to United States. 

For age variable, I first plotted the distribution of age for new users that went to three different country destinations: Australia, Canada and Germany. From the distribution, it is shown that these three country destinations have about the same right skewed distribution with the mode at around 30 years old. Then I also plotted the boxplots for each country destination and it also shows that the age distributions are similar. Moreover, Spain and Netherland tend to attract younger people while Germany and France tend to attract older people. 

For the time series variables, there is not much sense on keeping first active time and account create time as features. Instead, the gap between first active and account create could be an interesting feature to look at. However, more than 99% of the calculated gap month or gap days are zero. It shows that most new users created account at the same day of their first active date. First booking dates are separated as first booking years and first booking months. Value counts show that there are no extreme values or highly skewed distributions in years or months. 

For gender variable, since the category “other” has a small size, it is combined with 44% of the variable that are nan values. From the bar chart of value counts for each category in gender variable versus different country destinations, the new users that chose unknown or other as gender have much higher possibility to not have first bookings yet. Other relationships are not obvious. 

For language variable, from the bar chart of value counts for English and all other language versus different country destinations, it is shown that all country destinations were chose by a lot more new users that speak English than new users that speak other language. This could because that Airbnb is very popular in United States but might not have the same popularity in other countries that does not speak English. 

For the other categorical variables, some of them have very small category size (smaller than 100) but most of the categories have their own meanings and are not suitable to combine with other categories. 

Above all, my initial findings are that: 
1.	There are many unknown values in this dataset. 
2.	More than half of the new users do not have their first bookings and it might be appropriate to build sequential models to first predict whether the new users would make first booking and then take the new users who predicted positive to further predict where would their first booking be. 
3.	Input variables have some relationships with the output variable. 
