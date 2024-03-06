
# PWC Power BI Virtual Internship Task 1 - Call Centre Trends
![PwC Power BI Virtual Case Experience (1)](https://user-images.githubusercontent.com/118357991/227764081-750f7560-c9f7-4563-9cb3-74186769cb42.png)

## Problem Statement :
Claire, the call center manager at PhoneNow sent a mail requesting to create a dashboard in Power BI visualizing relevant Key Performance Indicators (KPIs) and metrics in the dataset provided.

Possible KPIs include (but not limited to):

- Overall customer satisfaction
- Overall calls answered/abandoned
- Calls by time
- Average speed of answer
- Agent’s performance quadrant -> average handle time (talk duration) vs calls answered

## Datasource :

Dataset: [01 Call-Center-Dataset.xlsx](https://github.com/sonali-guptaa/call_center_trend_analysis/files/14495884/01.Call-Center-Dataset.xlsx)

## Data Preparation:

Complete Data transformation is done in Power Query and then the dataset is loaded into Microsoft Power BI Desktop for visualization. 

Also, I have renamed the given Call Center trends dataset to callcenterdataset which has 10 columns and 5000 rows of observation.

## Data Cleaning:

Data Cleaning for the dataset was done in the power query editor as follows:

- Replaced all null values with 0 throughout the dataset.
- Replaced N with No and Y with Yes in Answered(Y/N) and Resolved columns.
- Each of the columns in the table were validated to have the correct data type.

![1](https://github.com/sonali-guptaa/call_center_trend_analysis/assets/151986702/3ee0eae5-b6cb-495d-9cc6-0ec07eae7331)


- Created a new column named name of the week day.

Name of the week day = `FORMAT('callcenterdataset'[Date], "dddd")`

![2](https://github.com/sonali-guptaa/call_center_trend_analysis/assets/151986702/1238c807-040e-4b87-acd4-519f39fec333)

## Calculated Measures created using DAX:

Measures used in all visualization are:

- Average speed of answer in seconds = `AVERAGE('callcenterdataset'[Speed of answer in seconds])`

- Count of satisfaction rating = `COUNT('callcenterdataset'[Satisfaction rating])`

- Overall satisfaction rating = `DIVIDE('callcenterdataset'[Positive satisfaction rating], 'callcenterdataset'[Count of satisfaction rating])`

- Positive satisfaction rating = `CALCULATE(COUNT('callcenterdataset'[Satisfaction rating]), FILTER('callcenterdataset', 'callcenterdataset'[Satisfaction rating] In {4,5}))`

- Total Calls = `CALCULATE('callcenterdataset'[Total calls answered] + 'callcenterdataset'[Total calls unanswered])`

- Total calls answered = `COUNTX(FILTER('callcenterdataset', 'callcenterdataset'[Answered (Y/N)] = "Yes"),'callcenterdataset'[Answered (Y/N)])`

- Total calls unanswered = `COUNTX(FILTER('callcenterdataset', 'callcenterdataset'[Answered (Y/N)] = "No" ), 'callcenterdataset'[Answered (Y/N)])`

- Total resolved calls = `COUNTX(FILTER('callcenterdataset', 'callcenterdataset'[Resolved] = "Yes"), 'callcenterdataset'[Resolved])`

- Total unresolved calls = `COUNTX(FILTER('callcenterdataset', 'callcenterdataset'[Resolved] = "No" ), 'callcenterdataset'[Resolved])`

## Data Visualization (Dashboard) :

Call Centre Trend Dashboard createwd in Microsoft Power BI Desktop:

![3](https://github.com/sonali-guptaa/call_center_trend_analysis/assets/151986702/c0ce1839-82ab-45b2-b0b5-5ef034226f10)

## Insights :

As shown by Data Visualization, It can be deduced that:

- Stewart had the least satisfaction rate because he was slow in response to calls.
- Jim has the highest satisfaction rating among other agents.
- Also, people had more issues with streaming, that is why it has the highest number of calls.
- The below image is showing how much work each agent has done.

![4](https://github.com/sonali-guptaa/call_center_trend_analysis/assets/151986702/abacf6e0-5b06-43d8-8347-45398207da79)

---
