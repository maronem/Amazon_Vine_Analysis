# Amazon Vine Analysis

### Overview 

The purpose of this analysis was to analyze Amazon reviews written by unpaid Amazon users or Amazon Vine Program members and determine if there is any bias toward positive reviews from Vine members. We performed our analysis on a dataset of Amazon video game reviews from the US which we accessed through Amazon Web Service (AWS) S3. We used the Apache Spark engine along with the PySpark interface to extract and transform the dataset and then load our data into pgAdmin through an AWS RDS instance. 

## Analysis

Below is a preview of our initial dataset. All available datasets are constructed with the same data categories and layout. As seen we chose to analyze video game reviews as the product_category is "Video Games". From this data we were able to assess potential review bias between Vine and non-Vine members.

Starting Dataset
:---------------:
![image](https://user-images.githubusercontent.com/108199140/196826289-79af5410-4c42-47d1-ac83-779d0e61c034.png)

Following cutting down our dataset to keep relevant categories, we filtered the data for reviews that had a minimum of 20 votes to eliminate any non-important reviews and following this only used reviews that were considered "helpful". A review was considered "helpful" if it had greater than 50% of its total votes being helpful votes.

Reviews with >20 votes      |     Helpful Reviews
:--------------------------:|:-----------------------------:
![image](https://user-images.githubusercontent.com/108199140/196827167-5f346a72-dc2f-4511-9b49-30f898688989.png) | ![image](https://user-images.githubusercontent.com/108199140/196827323-426edcbb-0c09-4865-aeef-c4e752776ca9.png)

We then split our dataset into two seperate datasets, one strictly cotnainging reviews from Vine members and the other with reviews from non-Vine members. These cleaned datasets were used to investigate the questions below.

Reviews with >20 votes      |     Helpful Reviews
:--------------------------:|:-----------------------------:
![image](https://user-images.githubusercontent.com/108199140/196827478-6770a0e6-fcdf-484a-b2b8-492ebaf9e27c.png) | ![image](https://user-images.githubusercontent.com/108199140/196827499-3610fed8-532d-4d60-b9ae-1e6a4ce3331d.png)

### Analysis Questions

1. How many Vine reviews and non-Vine reviews were there

* Within our video game review dataset, there were 94 reviews from Vine members and 40,471 non-Vine members.

2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

* There were only 48 Vine member 5-star reviews, while there were 15,663 5-star non-Vine reviews in our dataset. 

3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

* Of stricly the Vine reviews, 51.06% were 5-star reviews, while of all the non-Vine reviews, 38.70% were 5-stars. 

## Summary

From our analysis we determined that there is a positivity bias for Video Games in the Vine program as over 50% of Vine reviews were 5 star reviews, while only 38.7% of non-Vine reviews were 5 stars, a 12.36% difference. Although we only investigated this bias in one dataset and this could be different for other product categories, for video games, we determined there is a positivity bias. Another analysis that could be performed on this dataset could be to filter data by verified_purchase and look at the percentage of 5 star reviews for Vine and non-Vine members. From our data previews, Vine reviews are showing many non-verified purchases, these non-verified purchases could be skewing the data and contributing to the positivity bias. For example, to perform this we could run the following code for Vine reviews:
```
verified_paid_reviews = paid_reviews.filter(paid_reviews["verified_purchase"] == "Y")
```
Recalculating our results sctrictly looking at verified purchases could eliminate the positivity bias.
