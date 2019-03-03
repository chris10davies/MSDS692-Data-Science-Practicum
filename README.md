# Company Review Analysis - Sourced from Indeed
#### MSDS692 Data Science Practicum 1

## PROJECT OVERVIEW
The results of a 2018 Monster recruiting survey say filling jobs with qualified candidates is more difficult than it was five years ago (Thibodeaux). The survey points to a good economy and an increase in open jobs as the major reasons contributing to difficulties in attracting top talent (Thibodeaux, 2018). The goal of this project is to utilize company reviews web-scraped from Indeed to gain insight on what impacts employee satisfaction and organizational culture.  These key insights could then be adopted to build a better organizational culture and a more effective recruiting process that attracts more quality candidates.

The analysis for this project focuses on Google and Tesla. Google, known for its impressive organizational culture, receives two million applications a year (Schneider, 2017). While Tesla's mission to help the planet by electrifying cars is attractive to candidates, the company culture has a reputation of being intense, as it drives to fulfill this mission (George, 2018). It will be interesting to if the analysis of each companies reviews reflect their perceived organizational cultures.  

## DATA MINING

For this project, the data was [web-scraped](https://github.com/chris10davies/MSDS692-Data-Science-Practicum/blob/master/web_scrape.ipynb) from Indeed using urlib.request to gather the review data and beautiful soup to parse it.

**Company Review Dataset (web-scraped from Indeed)**

2 separate datasets (Google & Tesla)

| Variable       | Description          |  Source |Type |
|:------------- |:-------------|:-----:|:-----:|
| Title     | Review title | scraped |string |
| Reviewer | Job title of the reviewer and current/former employee. | scraped |string |
| Location | Company city,  state  | scraped |string |
| Date       | Review date | scraped |date|
| Rating | Company rating (1-5) |scraped |integer |
| Review | Text of the review | scraped |string |
| State | Variable created by pulling it from location  | created |category |
| Job Title | Variable created by pulling it from reviewer      | created |string |
| Employee Status | Variable created by pulling it from reviewer      | created |category |

The featured review was repeated on every company review page that was scraped, so duplicates had to be removed.
``` python
# Remove featured review that is reapeated on every page
google_reviews = google_reviews.drop_duplicates(keep='first')
tesla_reviews = tesla_reviews.drop_duplicates(keep='first')
```
The scraped reviews were saved off to excel to capture the reviews at a point in time. Excel was chosen as the exported format to avoid issues with punctuation interfering with re-importing the data for analysis.  The number of rows were low so excel could definitely handle the volume.  

| File       |# of rows |
|:------------- |:-------------|
| Google   | 1329 |
| Tesla  | 1235 |

If you're interested in the steps taken to engineer the state, job title, and job status variables from the web-scraped review data, take a look at the [created_variables.md](https://github.com/chris10davies/MSDS692-Data-Science-Practicum/blob/master/created_variables.md).

## EDA (EXPLORATORY DATA ANALYSIS)

##### Employee Status
First, I made a bar plot to see the proportion of reviews from current vs. former employees.  Tesla had slightly more reviews from current employees while Google had more from former employees.

![alt text](images/bar_emp_status.png "emp_status")

##### Ratings
The majority of Google's reviews are rated 5 or 4 and there very few 2's and 1's. Tesla also had many 5's and 4's along with a decent amount of lower ratings. This lines up with Google's mean rating of 4.2 compared to Tesla's mean rating of 3.6.

Google             |  Tesla
:-------------------------:|:-------------------------:
![alt text](images/rating_google.png "rating_google")  |  ![alt text](images/rating_tesla.png "rating_tesla")


##  ANALYSIS
ML Models
ANOVA/t-tests

## CONCLUSIONS

## REFERENCES
George, P. (2018, December 13). Working at Tesla Means Being in an 'Abusive Relationship' With Elon Musk: Report. Retrieved from https://jalopnik.com/working-at-tesla-means-being-in-an-abusive-relationship-1831072258

Schneider, M. (2017, July 26). Google Gets 2 Million Applications a Year. To Have a Shot, Your Resume Must Pass the '6-Second Test'. Retrieved from https://www.inc.com/michael-schneider/its-harder-to-get-into-google-than-harvard.html

Thibodeaux, W. (2018, September 19). 67 Percent of Recruiters Say It's Harder Than Ever to Find Talent. Here's How to Beat the Odds. Retrieved from https://www.inc.com/wanda-thibodeaux/67-percent-of-recruiters-say-its-harder-than-ever-to-find-talent-heres-how-to-beat-odds.html
