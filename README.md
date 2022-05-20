# Amazon_Vine_Analysis

Dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Sports_v1_00.tsv.gz

## Purpose/Objective: 

The objective was to perform ETL on an AWS dataset using Apache Spark. PySpark was used to extract and transform the dataset. postgreSQL and AWS RDS were connected and the transformed data was exported to pgAdmin. A table (vine_table) was then exported from postgreSQL as a csv file for further analysis. This analysis (Vine_Review_Analysis.ipynb) was then used to determine whether paid reviews (Vine members) had a significant impact on the percentage of five star product reviews. 

## Results: 

The dataset was filtered to only have rows with greater or equals to 20 votes. This was done to get reviews that were more likely to be helpful. The DataFrame was then filtered to retrieve rows where the percentage of helpful votes (helpful_votes/total_votes * 100) was greater or equals to 50%. This DataFrame was then filtered into two categories, vine_df (vine == "Y") and not_vine_df (vine == "N").  

Vine members

<img width="373" alt="Screen Shot 2022-05-20 at 6 31 19 PM" src="https://user-images.githubusercontent.com/92544151/169620615-58f8e446-0397-4ac1-a848-acd634e5451e.png">

Non-Vine reviews

<img width="413" alt="Screen Shot 2022-05-20 at 5 53 38 PM" src="https://user-images.githubusercontent.com/92544151/169618956-ab85d45f-41af-4008-8cb3-b7d98fb04dfa.png">

Only 334 reviews were by Vine members while 61614 were non-Vine reviews. Out of the Vine reviews, 41.62% were five star reviews. On the other hand, 53.02% of non-Vine reviews were five star. 

## Summary: 

Given the results, it can be said that the Vine members were not biased in favour of the product. In fact, the percentage of Non-Vine five star reviews was about 12% higher. To conclude this with a greater degree of confidence though, all of the reviews should be considered for analysis and not just the ones with >=20 votes. Also, given that the dataset consisted of only the sporting products, other categories might exhibit bias.
