# Company Review Analysis - Sourced from Indeed
#### MSDS692 Data Science Practicum 1

## PROJECT OVERVIEW
The results of a 2018 Monster recruiting survey say filling jobs with qualified candidates is more difficult than it was five years ago (Thibodeaux). The survey points to a good economy and an increase in open jobs as the major reasons contributing to difficulties in attracting top talent (Thibodeaux, 2018). The goal of this project is to utilize company reviews web-scraped from Indeed to gain insight on what impacts employee satisfaction and organizational culture.  These key insights could then be adopted to build a better organizational culture and a more effective recruiting process that attracts more quality candidates.

The analysis for this project focuses on Google and Tesla. Google, known for its impressive organizational culture, receives two million applications a year (Schneider, 2017). While Tesla's mission to help the planet by electrifying cars is attractive to candidates, the company culture has a reputation of being intense, as it drives to fulfill this mission (George, 2018). It will be interesting to if the analysis of each companies reviews reflect their perceived organizational cultures.  

## EDA (EXPLORATORY DATA ANALYSIS)

### Data Mining

For this project, I [web-scraped](https://github.com/chris10davies/MSDS692-Data-Science-Practicum/blob/master/web_scrape.ipynb) Indeed using urlib.request to gather the review data and beautiful soup to parse it.

** Company Review Dataset (web-scraped from Indeed) **

2 separate datasets (Google & Tesla)

| Variable       | Description          |  Source |Type |
|:------------- |:-------------|:-----:|:-----:|
| Title     | Review title | scraped |string |
| Reviewer | Job title of the reviewer and current/former employee. | scraped |string |
| Location | Company city,  state  | scraped |string |
| Date       | Review date | scraped |date|
| Rating | Company rating (1-5) |scraped |integer |
| Review | Text of the review | scraped |string |
| State | Variable created by pulling it from location  | created |string |
| Job Title | Variable created by pulling it from reviewer      | created |string |
| Employee Status | Variable created by pulling it from reviewer      | created |string |

The featured review was repeated on every company review page I scraped, so I removed duplicates.
``` python
# Remove featured review that is reapeated on every page
google_reviews = google_reviews.drop_duplicates(keep='first')
tesla_reviews = tesla_reviews.drop_duplicates(keep='first')
```
The scraped reviews were saved off to excel to capture the reviews at a point in time.  I chose excel as the format to avoid issues with punctuation in the review text interfering with importing the data for analysis.  The number of rows were low so excel could definitely handle the volume.  

| File       |# of rows |
|:------------- |:-------------|
| Google   | 1329 |
| Tesla  | 1235 |

If you're interested in the steps I took to engineer the state, job title, and job status variables from the web-scraped review data, take a look at 

##  ANALYSIS
ML Models
ANOVA/t-tests

## CONCLUSIONS

## REFERENCES
George, P. (2018, December 13). Working at Tesla Means Being in an 'Abusive Relationship' With Elon Musk: Report. Retrieved from https://jalopnik.com/working-at-tesla-means-being-in-an-abusive-relationship-1831072258

Schneider, M. (2017, July 26). Google Gets 2 Million Applications a Year. To Have a Shot, Your Resume Must Pass the '6-Second Test'. Retrieved from https://www.inc.com/michael-schneider/its-harder-to-get-into-google-than-harvard.html

Thibodeaux, W. (2018, September 19). 67 Percent of Recruiters Say It's Harder Than Ever to Find Talent. Here's How to Beat the Odds. Retrieved from https://www.inc.com/wanda-thibodeaux/67-percent-of-recruiters-say-its-harder-than-ever-to-find-talent-heres-how-to-beat-odds.html
