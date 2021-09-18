# Kickstarter Analysis

## Analysis of Kickstarter Campaign Fundraising Data

### Purpose: To help Louise understand how different theater campaigns fared based on their launch dates and funding goals to inform how she manages her campaign


## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

I performed this analysis by first breaking out the Category and Subcategory columns of the Kickstarter campaign data. From there I created a pivot table filtered specifically for theater campaigns and categorized them by the month they launched and their outcomes:

![image1](https://github.com/JFoArlas/kickstarter-analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png)

One challenge I enountered here was that the launch date in the data was formatted as Unix timestamps. To convert those to readable dates, I used for following formula, where J2 was the launch date: `=(((J2/60)/60)/24)+DATE(1970,1,1)`. This allowed me to create the above graph with valid months on the x-axis.

### Analysis of Outcomes Based on Goal

I performed this analysis by first creating a row of different goal ranges to be able to visualize play campaign outcomes based on their goal. I then used `CountIFs` formulas that pulled the count of successful, failed, and canceled play campaigns into a table for each goal range. Then I calculated the percentage of each outcome for each of the goal ranges:

![image2](https://github.com/JFoArlas/kickstarter-analysis/blob/main/Resources/Outcomes_vs_Goals.png)

One challenge I encountered was that it would have been time consuming to manually write out all of the different `CountIFs` formulas. So instead I wrote the formulas for the "Number Successful" column using some copy and pasting so that I only needed to edit a piece of the formula in each cell. I made sure to include anchors in those formulas so that I could copy the entire column over to the next two columns vs. writing them out again. Then highlighted the cells in the "Number Failed" column and used the `CTRL+F` function to search those formulas for the word "successful" and replaced it with the word "failed." This updated all 12 formulas in that column to reflect failed play campaigns instead of successful play campaigns for each goal range. I repeated that step once more for the "Number Canceled" column.

## Results

### Conclusions: Outcomes based on Launch Date
- The month with the *highest* number of successful campaign launches is May
- The month with the *lowest* number of successful campaign launches is December

### Conclusions: Outcomes based on Goals
- Play campaigns with a goal of $45k and up have the lowest success rates
- Play campaigns with a goal of less than $5k, or a goal of $35-45k have the highest success rates

### Dataset limitations
Even though play campaigns with a goal of $45k and up have the lowest success rates, there is a much smaller sample size of play campaigns in that goal range. In fact, 92% of play campaigns in the dataset had a goal of under $15k. So for goal ranges above that, just one failed play campaign could drastically lower the success rate and means we likely don't have enough data in those ranges for that conclusion to be totally reliable.

### Other possible tables/graphs to consider
To demonstrate the above limitation of the dataset, a graph of the total percentage of play campaigns by goal range shows just how much less data there is for play campaigns with higher goals:

  ![image3](https://github.com/JFoArlas/kickstarter-analysis/blob/main/Resources/%25%20of%20Play%20Campaigns%20by%20Goal%20Range.png)
  
Another possibly helpful graph is if you view the Theater Outcomes Based on Launch Date by percentage instead of count. This allows you to view the success rate of play campaigns by month vs. by raw count. May still has the best success rate and December still has the lowest success rate, but other months rank differently when viewed by percentage vs. count. For example, October has more successful play campaigns than March, but March's success rate is higher than October's.

  ![image4](https://github.com/JFoArlas/kickstarter-analysis/blob/main/Resources/%25%20Theater_Outcomes_vs_Launch.png)
