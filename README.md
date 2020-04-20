# Starbucks Capstone Challenge
## Contest<br>
This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount, BOGO (buy one get one free) or informal offer. Some users might not receive any offer during certain weeks. But not all users receive the same offer. 

The attached json data set is a simplified version of the real Starbucks app (just a single product, whereas Starbucks actually sells dozens of products):
* portfolio.json - offer ids and meta data about each offer (duration, type, etc.)
* profile.json - demographic data for each customer
* transcript.json - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

##### portfolio.json
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

##### profile.json
* age (int) - age of the customer
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

##### transcript.json
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record

## Main results
Performance of the offers
* the informal offers have an high view rate but are never closed
* BOGO offers' view rate is higher than discount offers but the conversion rate is lower
* the count of transaction is less than twice the count of offers received
![offer type vs event](https://raw.githubusercontent.com/Davide-666/Starbucks-Capstone/master/offer%20type%20vs%20event.png)<br>
Possible improvement: focus on discount

Gender
* the count of female subscription is lower than men's
* female have an higher view and conversion rate than men
* the count of transaction is much higher for man but the count of offer closed by genre is almost the same
![subscription by gender](https://raw.githubusercontent.com/Davide-666/Starbucks-Capstone/master/subscription%20by%20gender.png)<br>
![event vs gender](https://raw.githubusercontent.com/Davide-666/Starbucks-Capstone/master/event%20vs%20gender.png)<br>
Possible improvement: switch more offers to female 

Subscription
* Subscription was flat in 2014 and 2016 and have an increse in Summer time for 2015 and (steeper) 2017
* During the first semester of 2018 this KPI worsened
![subscription by months](https://raw.githubusercontent.com/Davide-666/Starbucks-Capstone/master/subscription%20by%20months.png)<br>
Possible improvement: further investigation are needed 

## Next steps:
* In the actual project income missing data were filled with the overall mean value. Other methods can be tested (drop NA, filling with overall moda, filling with mean/moda by "nearest category", ...)
* Age 118. It is clearly a mistype or the default value. In the same records both gender and income are not specified. Records could be dropped or age forced to 18
* Futher analysis on macro data (distribution of order price, income, ...)
* ML analysis using different ML engine and different percentage of data for train/test/validate, using also random sampling
