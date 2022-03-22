# Excel Kickstarter Analysis

## Objective: 
Modify and analyze the data of 4,000 past Kickstarter projects as you attempt to uncover market trends.

## Tools & databases used:
- Advanced Excel

## Dataset:
- Kickstarter csv file.

## Expanding The Data

*Note: I converted column letters into their column names for reame readability.*

1) The dataset comes with Goal and Pledge amounts, but no other data. For the first step I want expand the data I have and create a Percentage Funded column for later analysis.
`=ROUND(Pledged/Goal*100,0)
2) Next I want to find the average donation each kickstarter receives. This column contains errors since some cells are trying to divide by 0, so I'm accounting for those with "IFERROR()"
`=IFERROR(ROUND(Pledged/Backers,2),0)
3) This dataset contains a category column where the parant and sub are combined, so for better analysis I'm splitting this into two new columns: Parent category" and "Subcategory" using text to column with a backslash delimiter.
4) Launch Date and Deadline are both in unix timestamp format, so I'm creating a "Date Created" and "Date Ended" conversion column to display Month/Day/Year.
`=(((Deadline/60)/60)/24)+DATE(1970,1,1)`

## Conditional Formatting: 
I'm applying conditonal formatting to Outcomes & Percentage Funded in order to easily identify performance of the kickstarters.

## Category & Subcategory Statistics
My first Analysis is to see how well the categories perform using pivot tables and stacked bar graphs.
1) Parent Category Outcomes.  
![category_statistics](https://github.com/Ryndine/excel_kickstarter_analysis/blob/main/Images/category_statistics.jpg)  
 - This data seems to show that Journalism kickstarters seem to perform the worst. However, since we do not know why the kickstarters were canceled it's unclear to tell if Journalism is performing poorly. Looking at food which had 200 kickstarters, 140 Failed, 20 Canceled, and only 34 Successful, this clearly indicates that this category performs very poorly on kickstarter, and you're more likely to expect failure if attempting a kickstarter in this category.
 - On the other side is theater, This occupies the largest space on kickstarter. Theater has the most successful kickstarters out of all the categories, but it also has the most failures. Compared to Music, it doesn't seem to perform as well. A larger percentage of kickstarters are successful which indicates that attempting a Music based kickstarter is the safest option if attempting to recieve funding.
2) Subcategory Outcomes.  
![subcategory_analysis](https://github.com/Ryndine/excel_kickstarter_analysis/blob/main/Images/subcategory_statistics.jpg)  
 - The subcategories paint a clearer picture of where success lies within these categories. As expected plays receive the highest volume of kickstarters. Digging into the data more though you see that there see to be subcategories that never see any failure. Most notable are documentaries, rock music, and hardware. There are many other subcategories seeing strong success but these three are by far the safest of them all.

## Outcomes Based on Goals:  
![outcomes_goals](https://github.com/Ryndine/excel_kickstarter_analysis/blob/main/Images/outcomes_goals.jpg)  
Second analysis is to see how well kickstarters performed based on their goals.
 - At first glance the graph shows that the higher the goals the more likely a kickstarter is to fail, however there seems to be a spot between 30,000 and 40,000 where kickstarters start performing well.
 - Looking further into this it seems that the data is being influenced by lack of substantiel data. There are fewer kickstarters the higher the goals, so it's hard to gauage the validity of the results as of yet.

## Theater Outcomes by Launch Date:
![theater_outcomes](https://github.com/Ryndine/excel_kickstarter_analysis/blob/main/Images/theater_outcomes_date.jpg)
The next analysis I wanted to gain deeper insight into the theater category since it contains the most amount of kickstarter data.
- It seems that after April kickstarters seem to perform much better. Maybe this could be attributed to tax returns? Either way performance seems to normalize again around August.

## Edinburgh Research:
![vlookup](https://github.com/Ryndine/excel_kickstarter_analysis/blob/main/Images/vlookup.jpg)
Next I setup a vlookup so I can look at specific kickstarters within the data.

# Statistical Analysis:
![statistical_analysis](https://github.com/Ryndine/excel_kickstarter_analysis/blob/main/Images/statistical_analysis.jpg)
Then for my last step I decided to breakdown the dataset into a stastical analysis to gain one final insight into performance.
- Here it seems to confirm that kickstarters that are successful often have smaller goals than kickstarters that fail.
