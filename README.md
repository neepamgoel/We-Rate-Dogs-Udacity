# We-Rate-Dogs-Udacity
Performing Data Wrangling on a twitter account weratedogs. Scraping data from twitter, online host server, assessing issues providing in depth quality and tidiness issues with the dataset to finally get a clean dataset for performing analysis.

## Data Wrangling
First step for our project is to gather the data required through different sources. We access the twitter archive data using pandas, read the image prediction data through the Udacity servers and finally scrape data through twitter API.
We then move on to our next task of assessing the data. Through some initital exploration of our data via Visual Assessment we found that twitter_id is the common attribute among our three tables. We would be merging them together later to correct one of the tidiness issue in our dataset and make it more viable for analysis later. We further identified 9 Data Quality issues and 2 Tidiness issues in our Dataset through Programmatic assessment using functions like info(), describe() and Visual assessment like reading through our csv files and through sample().

The issues identified were –

### Quality issues

For twitter archive data(tw_arch)
1. Completeness - Missing values of dog names and stages.
2. Completeness- Missing expanded url values.
3. Validity- timestamp, retweeted_status_timestamp should be datetime instead of string.
4. Validity- tweet_id is integer instead of string
5. Accuracy- invalid dog names(all,one,the,a) in some rows
6. Consistency- Removing tweet_ids which are retweets
7. Completeness-  in_reply_to_status_id, in_reply_to_user_id , retweeted_status_id			      retweeted_status_user_id variables not essential to our analysis

For Image prediction(image_pred)

8. Validity- tweet_id should be string instead of integer.

For additonal twitter data(add_data)

9. Accuracy - Although the retweet_count is not zero, favorite_count(number of likes for a tweet) is zero in some rows which is an unlikely scenario for a tweet.

### Tidiness issues

1. Each variable forms a column- All columns dogger, floofer, pupper, puppo must be converted into a single attribute as they all represent a dog stage.
2. Each type of observational unit forms a table - We need to merge all 3 tables to get useful insights (all duplicated columns must be removed)

After identifying the issues, we started cleaning our data. We used replace() to replace certain values in the data like invalid dog names, astype() to convert data into different data types to make it more valid, drop() to delete the rows and columns which are not useful for our analysis to make our data more complete.
We further removed the retweeted user ids since we only wanted to keep the original tweet ids and only kept those tweet ids which had images and were present in the image_pred table to make data more tidy without any duplicated rows.
After this we store our master data as a csv file and proceed to Data Visualisation and providing insights through it.

## Data Analysis and Visualization 

After cleaning our dataset we proceed to visualising our data and to gain useful insights from it. We had four research questions which we wanted to answer.

### Research Question 1: What are the most common dog names?

To answer this question, we chose the top 10 most common dog names through value_counts() since there are a lot of different dog names to simplify our visualisation. We plotted a bar chart for our analysis.

**Insight**: We saw that Lucy, Oliver and Cooper are the most common dog names. Each was named 10 times in this dataset.
 
### Research Question 2: What is the trend of number of likes and retweets in a tweet?

For this we wanted to see the trend of likes and retweets in a tweet by Weratedogs and if it has increased or decresead over the last 2 years. We plotted a Line chart to show this trend using plot.line().

**Insight**: We could see that number of likes and retweets have increased on an average over the last 2 years

### Research Question 3: What is the average number of likes and retweets for a tweet?

We wanted to see that if the page tweets a post, on an average how many likes and retweets is it expected to get. We used describe() and mean() on our dataset to give us the possible results.

**Insight**: Average number of likes and retweets in a tweet by Weratedogs were 8896 and 2767 respectively.

### Research Question 4: What is the most viral tweet?

Here we wanted to identify the most viral tweet this page has seen over this 2-year period from Nov 2015 – Sep 2017. For this we again make use of describe() and further queried the post with most likes.

**Insight**: The most viral tweet was the one that got 132,810 likes and was a post about a supportive puppo getting a 13/10 rating.

