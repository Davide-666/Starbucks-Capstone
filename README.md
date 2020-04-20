# Starbucks Customer Classification - Capstone for the Data Scientist D§NnaoDegree by Udacity

##Contest
This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks. But not all users receive the same offer. 

The attached json data set is a simplified version of the real Starbucks app (just a single product, whereas Starbucks actually sells dozens of products):
* portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
* profile.json - demographic data for each customer
* transcript.json - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

portfolio.json
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

profile.json
* age (int) - age of the customer
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income
* transcript.json

event (str) - record description (ie transaction, offer received, offer viewed, etc.)
person (str) - customer id
time (int) - time in hours since start of test. The data begins at time t=0
value - (dict of strings) - either an offer id or transaction amount depending on the record
Final Advice
Because this is a capstone project, you are free to analyze the data any way you see fit. For example, you could build a machine learning model that predicts how much someone will spend based on demographics and offer type. Or you could build a model that predicts whether or not someone will respond to an offer. Or, you don't need to build a machine learning model at all. You could develop a set of heuristics that determine what offer you should send to each customer (i.e., 75 percent of women customers who were 35 years old responded to offer A vs 40 percent from the same demographic to offer B, so send offer A).

### Results from the analysis
From the first raw data analysis that can be found below, we can make some key general statement:
* the informal offers have an high view rate but are never closed
* BOGO offer have an higher view rate than discount one but a lower conversion rate
* Female have an higher view and conversion rate than men
* Subscription was flat in 2014 and 2016 and have an increse in Summer time for 2015 and (steeper) 2017
* During the first semester of 2018 this KPI is going bad

### Next steps:
* Missing data on income were filled with overall mean value. Other methods to be tested (drop NA, filling with overall moda, filling with mean/moda by "nearest category, ...)
* Age 118. It is clearly a mistype or the default value. In these records gender and income are not specified. Records could be dropped or forced to age 18.
* Futher analysis on macro data (distribution of order price, income, ...)
* ML analysis using different ML engine and different percentage of data for train/test/validate, using also random sampling
