---
layout: post
author: Soe Lai Nwe
title: "Applied Data Science Project Documentation"
categories: ITD214
---

## Contents
- Background & Business Goal
- About the Dataset
- Business Objective, Success Criteria & Data Mining Goals
- Project Plan
- Data Understanding, Preparation & Transformation
- Modelling
- Evaluation

## Background & Business Goal
Since its inception in 1969 in Paris, Sephora has expanded globally and revolutionized beauty retailing with a focus on luxury and expertise. It offers a wide selection of skincare products and solutions, ranging from makeup, skincare, hair care and beauty tools.  

Its dedication to empowering customers through personalized service and expert advice is central to Sephora's success. Ongoing competition and market saturation challenges mean Sephora must constantly distinguish itself from other competitors through its unique brand identity and offering. Through innovations with digital tools and enhanced personalized recommendations based on customer preferences, it remains dedicated to its mission to elevate the beauty retail experience and lead in the industry.

This project aims to gather valuable insights into customer satisfaction and sentiment by analysing helpful reviews and features. These include identifying best-selling items, product effectiveness through reviews and ratings, and a recommendation system for cross-selling to increase sales and customer satisfaction.   

# About data set

- The data set was collected from Kaggle https://www.kaggle.com/datasets/nadyinky/sephora-products-and-skincare-reviews
- Contains information about over 8,000 beauty products from Sephora online store. Including product, brand names, prices, ingredients, ratings and all other features. 
- More than a million  user reviews on over 2,000 products on all products from the Skincare category, including user appearances, and review ratings by other users.


File Information                            | Data Explorer         |
--------------------------------------------| --------------------- | 
File Format: Excel CSV                      | Columns: 19           | 
No. of Files: 6 (5 Reviews + 1 Product Info | Rows: 1,094,411       |
File size: 154 MB                           | Data Type: String, Integers and floats|



# Business Objective
- Analyzing ratings, author recommendations, pos, neg feedback count and reviews to identify trends, patterns and address areas with lower ratings.

# Success Criteria
- Enhance customer satisfaction by analyzing ratings (3) and identifying areas for improvement

# Data Mining Goal
- Explore ratings, feedback count, author recommendation to identify the trends. 
- Analyzing long and short reviews association with ratings and filter the products to improve customer experience.

# Hypothesis
- Longer reviews with detailed feedback are more likely to correlate with higher ratings than shorter reviews.

# Project Plan 

![project plan](https://github.com/user-attachments/assets/02cc02cc-cf27-4b12-97e9-f7dc89226ce9)

## Data Preparation

- Remove unnecessary columns for analysis

-Various product parameters (skin tone,eye_color,skin_type,
hair_color)

- Remove duplicates

![duplicates](https://github.com/user-attachments/assets/bdb51279-7165-4bb0-a2e7-053dc51e3106)

- Remove NaV value columns

remove helpfulness col: as 51% of data is NaN value

remove is_recommended NaN value columns

![null value](https://github.com/user-attachments/assets/6099f46a-f07d-463f-a3be-172de5bdeeee)

# Summary of data

![summary of data](https://github.com/user-attachments/assets/8284c912-2a61-416c-a5e5-fb70a53114ee)


### Modelling
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

### Evaluation
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Recommendation and Analysis
Explain the analysis and recommendations

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here.
https://github.com/CrystalSoe/itd214
