# Amazon Vine Analysis

### Overview 

The purpose of this analysis was to analyze Amazon reviews written by unpaid Amazon users or Amazon Vine Program members and determine if there is any bias toward positive reviews from Vine members. We performed our analysis on a dataset of Amazon video game reviews from the US which we accessed through Amazon Web Service (AWS) S3. We used the Apache Spark engine along with the PySpark interface to extract and transform the dataset and then load our data into pgAdmin through an AWS RDS instance. 

### Analysis

1. How many Vine reviews and non-Vine reviews were there

* 

2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

* There were only 48 Vine member 5-star reviews, while there were 15,663 5-star non-Vine reviews in our dataset. 

3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

### Summary

Is there any positive bias?
