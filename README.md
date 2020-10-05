# kickstarter_analysis_challenge
# Kickstarting with Excel

## Overview of Project

Performing analysis on Kickstarter data to uncover trends for our 'customer'Louise, who is looking to crowdfund her play write "Fever." She's come close to her goal in a short amount of time but wants to know how similar campaigns fared in relation to 'Launch Date' of their campaign and the 'Funding Goal' they set out to hit. 

### Purpose

To analyze similar campaigns to Louise's so we can understand the impact that 'Launch Date' and 'Goal Amount' has on the success rate of the campaigns.

## Analysis and Challenges

First, we created a Pivot Table to get a breakout of Theater campaigns and broke them out by their outcome of either 'successful, failed, or canceled.' Then we organized and filtered them by what month they were launched in. 

In order to do this we need to convert the Unix epoch creation timestamp into a more readable format using the formula =(((J2/60)/60)/24)+DATE(1970,1,1). 

J2 is the 'launched_at' column and the values consist of time stamps that look like this - '143493181.' This is the number of seconds that have elapsed since January 1, 1970. So we divide this by seconds in a minute (60) and then divide it by the number of minutes in an hour (60), then divide by the hours in a day (24). Then add that result with +Date(1970,1,1) which is just adding the time elapsed from the start of the Unix timestamp. 

Then we needed to group the 'Launch Dates' by month so we can see any trends and identify the best month to launch through a line graph. 

Second investigation was to see how outcomes were effected by the Goal of funding they were looking for. So we follow a similar order as we did before and create a Pivot Table showing the breakout of of the number of 'successful, failed, or canceled' campaigns and bucketed them into certain goal ranges to identify if there is a trend. 

In order to execute on this we needed to create a new tab where we used the =COUNTIFs()function to filter the data in a way we want to visualize it. 

So we create the ranges of 'Goals' starting with 'Less than 1000,' then created bucketed ranges in $5000 incremenets that eventually ended with 'Greater than 50000.' First order is to break these out by the Number of Successful Campaigns, Number of Failed, and Number of Canceled Campaigns that had a funding goal less than 1000. 

The formula to achieve this reads =COUNTIFS(Kickstarter!$D:$D,"<1000",Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays"). Using this function allows us to Count the number of times that we see a certain result. So we say count the number of times we see funding less than 1000 on the Kickstarter tab - Kickstarter!$D:$D,"<1000", that was categorized as 'successful' - Kickstarter!$F:$F,"successful", and that was part of the subcategory "plays" - Kickstarter!$R:$R,"plays". 

We needed to replicate this for the rest of the range amounts and for the different results we wanted to tally up. 

We then wanted to convert this into a format that paints us a better picture of what's happening as a result. So we needed to use the =SUM() function in order to get the 'Total Project' count for each funding goal range. We then use simple arithmetic to calculate the percentage of 'Successful, Failed, and Canceled' campaigns based on their goal. 

### Analysis of Outcomes Based on Launch Date

!()(/Theater_Outcomes_vs_Launch.png)

What we found is that summer launch dates, specifically in May and June yield the most successful Theater campaigns that met their funding goal. May led with 111 'successful' campaigns and June with 100. Followed by July with 87. The number of successes steadily decreases as the year goes on with the lowest amount of success coming in December with 37 successful campaigns. 

This could be due to a number of reasons - a hypothesis is that summer is usually a time where families and individuals are looking to have fun, spend money, and be a part of and attend events. And December, our lowest month of 'successful' campaigns is usually a month where money is being directed into things like gifts for Christmas. 

### Analysis of Outcomes Based on Goals

!()(/Outcomes_vs_Goals.png)

The next topic Louise wanted us to investigate is how a campaigns 'Funding Goal' or the funding amount they set as their target effected the rate of success. 

From our first take at diving into this, we found no distinguishable trends. 

What could be helpful in providing us better insight would've been to calculate the Central Tendencies of this data set and display it in a Box and Whisker plot. This would allow us to understand the distribution of the data in a greater capacity and may allow us to provide Louise with a stronger hypotheses of how Goals effect outcomes. 

However, given the current analysis we did find that the highest percentage of success came with the lowest goal of 'Less than 1000' with 76% chance of success. Another piece of advice we can decipher and share with Louise is that she should not be setting a Goal within the range of '45000 to 49999' as there is 0% chance of campaigns being successful within that goal range. 




