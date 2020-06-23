# Tableau - Challenge

## This repository contains the files regarding a Tableau exercise conducted with data for the Citi Bike Program. 
This folder contains the following:
1.	Resources folder that contains 29 CSV iles, one each for the months Jan-2018 to May-2020.
2.	Jupyter Notebook folder that contains a Jupyetr notebook file used to clean and combine the data from the 29 CSV files into one combined Excel file. 
3.	Output folder that contains one combined Excel file generated from the Jupyter Notebook filke. 
4.	Images folder that contains teh Images used for the Tableau file. 
5.	XXXXX.

## Data Extraction:
Data was extracted for the period Jan-2018 to May-2020 from the following website. 
<br>
<br>
https://www.citibikenyc.com/system-data
<br>
The data had the follwoing columns:
* - Trip Duration (seconds)
* - Start Time and Date
Stop Time and Date
Start Station Name
End Station Name
Station ID
Station Lat/Long
Bike ID
User Type (Customer = 24-hour pass or 3-day pass user; Subscriber = Annual Member)
Gender (Zero=unknown; 1=male; 2=female)
Year of Birth. 
<br>
<br>
<br>

## Data Transformation:
We did the following to transform the data:
1.	Addressed NULL values. 
2.	Formatted the dates in a manner that would work with the flask library in python. 
3.	"Rolled-up" / summarized the dataset with actual numbers from the original level of State/County/Date to the level of State/Date.
4. Created a ranking for the states based on the Total Deaths Per Million of Population.

## Data Load: 
We then loaded the data into a SQLite database and called it covidData.db.
<br>
<br>

## Creation of a Python File with Functions:
We used SQL Alchemy to create functions in a python file called covidData.py. These functions allow us to extract the relevant data from the SQLite Database.
<br>

## Creation of a Python File with API routes:
We then used Flask to create API routes in a file called application.py. This file uses the functions created in the file called covidData.py. 
<br>

## Creation of an HTML file:
We then created an HTML file called index.html. This file contains the structure for the webpage. It also has all the relevant references / links to the underlying files that are used to format / style the webpage, as well as dynamically create the charts / graphs on the webpage.
<br>

## Creation of a Javascript file:
We then created a Javascript file called plots.js. This file contains all the logic that controls the dynamic interaction of a user with the webpage. This logic allows for dynamic updates to the charts / graphs based on the user's selection of a particular US state.
<br>

## Push to AWS:
We then zipped all the relevant files and folders and uploaded them to an environment on AWS using the service called "Elastic Beanstalk". This environment then provided us a URL for our webpage as follows:
<br>
http://project2final-env.eba-jy95kuzb.us-east-2.elasticbeanstalk.com/
<hr>

## Attached below is a screenshot of the Top Half of our webpage. 
![](images/Website_Top_Half.PNG)
<hr>

## Attached below is a screenshot of the Bottom Half of our webpage. 
![](images/Website_Bottom_Half.PNG)
<hr>

## User-driven interaction with the webpage: 
When a user selects a state from the dropdown box in the upper left hand corner, the following items update automatically with the relevant details for that state:
1.	The panel below the dropdown box. This panel shows for the selected state, the total number of cases, the total number of deaths, and the total population. 
2.	The map to the right of the dropdown box. The map zooms in to the selected state. You can then use the mouse to zoom in further or zoom out. You can also mouse over the state and that will pop up a box showing the total number of deaths for that state. The state will have a color ranging from light gray (lesser total deaths) to dark blue (higher total deaths) depending on the number of total deaths for that state. To the right of the map is a vertical bar which shows how the color scale changes from light gray to dark blue depending on the total number of deaths for the selected state.
3.	The "gauge-chart" to the upper right of the map. This chart is created using a special javascript library called "gauge-chart". Details of this library can be found at this link: https://github.com/recogizer/gauge-chart/. 
This gauge chart shows a ranking for the state based on the total number of deaths per million of population. It is a scale with a ranking of 1 to 50 where a rank of 1 means that the selected state had the lowest (best) ratio of total number of deaths per million of population, and a ranking of 50 means that the selected state had the highest (worst) ration of total number of deaths per million of population. 
4.	The pie chart to the lower right of the map. This chart shows the percentages of the total population broken down into 3 categories, total number of cases, total number of deaths, and the total number of people unaffected - the percentages for these 3 categories will always sum to 100% of the population of the selected state. It is a way to visually depict the magnitude of the total number of cases and deaths compared to the magnitude of the portion of the population unaffected.
5.	The box to the left of the screen below the  panel summary which is below the dropdown box. This box shows the total number of cases for the selected state, and then presents that number as a percentage of the total population. 
6.	The box in the middle of the screen below the map. This box shows the total number of deaths for the selected state, and then presents that number as a percentage of the total population.
7.	The box to the right of the screen below the pie chart. This box shows the total number of unaffected people for the selected state, and then presents that number as a percentage of the total population. The number of unaffected people is calculated as the total population for the state less the sum of the total number of cases and deaths, for the selected state.
8.	Bar chart # 1 which is below the 3 boxes mentioned in points 5 to 7 above. This bar chart shows the total number of deaths )Actual vs Predicted) for the selected state by date. This chart also has a "slider" feature at the bottom of the chart, which allows you to conveniently "slide" to a date window of your choice, and thereby zoom into that date window on the graph. At the top left hand corner of the chart, you also have 3 "time-horizon" buttons - 1W (for the last week from the selected date window), 3W (for the last 3 weeks from the selected date window, and All (for all the dates in the dataset). 
9.	Bar chart # 2 which is below Bar Chart # 1. This bar chart shows the daily cases (Actual vs Predicted) for the selected state by date. This bar chart also has the "slider" feature and the 3 "time-horizon" buttons mentioned in number 8. above.
10.	Bar chart # 3 which is below Bar Chart # 2. This bar chart shows the daily deaths (Actual vs Predicted) for the selected state by date. This bar chart also has the "slider" feature and the 3 "time-horizon" buttons mentioned in number 8. above.


# Conclusions:
1.	The 5 states with the highest total number of deaths are as follows:
* *New York: 30,374 (0.16% of the total population)*
* *New Jersey: 12,176 (0.14% of the total population)*
* *Massachusetts: 7,323 (0.10% of the total population)*
* *Pennsylvania: 5,943 (0.05% of the total population)*
* *Illinois: 5,903 (0.05% of the total population)*
2.	The 5 states with the highest total number of deaths per million of population are as follows:
* *New York: 1,562 (0.16% of the total population)*
* *New Jersey: 1,362 (0.14% of the total population)*
* *Connecticut: 1,143 (0.11% of the total population)*
* *Massachusetts: 1,050 (0.10% of the total population)*
* *South Dakota: 927 (0.10% of the total population)*

## Key Takeaways:
We were surprised by the relatively low percentage of the total population that was affected (total cases and deaths). Even for the hardest hit state (New York) the total percentage affected was just over 2% of the total population. This could be due to "stay-at-home" orders and social distancing measures taken in early March. 
<br>
Even with Predicted data, there are many factors contributing to the spread of this virus. The novelty of this virus makes it difficult to make predictions. However, the multiple visualizations provided on our webpage allows the user to explore the data in a way that tells a more comprehensive story. 






