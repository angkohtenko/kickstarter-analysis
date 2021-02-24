# Kickstarting with Excel

## Overview of Project
The playwriter Louise is going to create crowdraising campaign for her new play Fever. She wants to know how different campaigns fared in relation to their launch dates and their funding goals.

### Purpose
I analyzed Kickstarter dataset in order to figure out what is the best time to start a campaign to get a goal amount and what funding goal should be set to be successful.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
At first, I decided to look at launch dates. I created a pivot table and filtered it by category Theater as Plays are included in that parent category. Also, I sorted pivot table by month so it is easy to track seasonality. 

The best way to visualize the result is using line chart. On the chart below, we clearly see that May and June are the best months to start a campaign. There are 111 successful campaigns vs 52 failed in May and 100 successful vs 49 failed in June. 
On the other hand, the worst choice will be to start campaign in December. It will likely be failed. Probably, people aren’t lavish enough and spend money on gifts for relatives.
![Theater Outcomes Based on Launch Date](https://github.com/angkohtenko/kickstarter-analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals
What funding goal should be set? I built additional table to answer this question. I created ranges with $5000 step to look how many successful and failed campaigns of plays are within every range. Then I calculated the percentages of successful, failed and canceled projects in each range.

First of all, I realized that the goal for 2/3 of campaigns is less than $5000. So, people are used to see that amount. They become cautious when amount is significantly greater. To make it clear I built a line chart with percentages of successful and failed campaigns.

![Plays Outcomes Based on Goals](https://github.com/angkohtenko/kickstarter-analysis/blob/main/Resources/Outcomes_vs_Goals.png)

We see that it’s easy to raised less than $1000. You will likely do it with 80% probability. It is quite easy to get $4999. 73% of campaigns has done that. 

Everything above $5000 are disputable. The red line, which stands for failed campaigns, is higher then green here. We can be misleading by successful campaigns in the range between $35000 and $44999, but there are too few campaigns to make any positive conclusions (6 successful vs 3 failed). 


### Challenges and Difficulties Encountered
During the analysis I met two main challenges: unix timestamp and merged parent category and subcategory.

All dates in the dataset were written in the unix timestamp: 1449766261, so there were number of seconds from Jan.1 1970 instead of normal date. To solve the problem I created new columns and calculated dates with formula =(((A1/60)/60)/24)+DATE(1970,1,1) . It’s important to set a date format to these columns. To extract year from the date became a piece of cake.

Category and Subcategory were merged in one column in the original dataset, so it was hard to filter only Theater category. I should select all subcategories manually to do that.  I used Text to columns feature in Excel. I set the sign / as a delimiter to divide text into two columns: parent category and subcategory. Now, I could easily filter dataset either by parent category or subcategory.

## Results

- The best months to start a campaign are May and June.
- The worst months for launch date is December.
- The funding goal should be less than $5000.
- It's important to keep in mind that used Kickstarter dataset contains data for 2009-2017 years only. Some trends might have changed since 2017.
- It’s definitely useful to build a chart with quantity of campaigns in every goal range. As I mentioned, most of the campaigns have a funding goal less than $5000.
- It's good idea to create a table with campaign durations to figure out short or long campaigns are more successful.
