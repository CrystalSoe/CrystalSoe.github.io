---
Layout: post
Author: Soe Lai Nwe
Title: "Applied Data Science Project Documentation"
Categories: ITD214
---

## Contents
- Background & Business Goal
- About the Dataset
- Business Objective, Success Criteria & Data Mining Goals
- Project Plan
- Data Preparation & Transformation
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

# Data Preparation & Transformation

1. Select
2. Clean
3. Construct
4. Integrate
5. Format

1.Select
- Explore statistics on numeric columns

Variable           | Range                |
-------------------| -------------        | 
rating             | 1 to 5               | 
is_recommended     | 0 (False) , 1 (True) |
submission time    | 2017 to 2023         |

![correlation matrix](https://github.com/user-attachments/assets/c8430fbb-0e66-48d2-ba40-e770e8529c3b)

-rating & is_recommended are strongly correlated. 

- Focus variables

 -ratings, is_recommended,  total_neg_feedback_count, total_pos_feedback_count, 
submission_time, reviews

2.Clean
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

3.Construct
- merged_reviews

-Combine review_text and review_title columns and create 'merged_review' new column

- submission time

-Split to three columns as year, month, date

4.Integrate N/A

5.Format

-construct a datetime value to be ready for further analysis

-define 100 words as long review and calculate each review length and creat review length and review type columns

# Modelling
1. Select Modeling Techniques
2. Generate Test Design
3. Build Model
4. Assess model

1.Select Modeling Techniques

- **Random Forest Regressor**: Can handle complex and non-linear relation ship, less sensitive to noisy data, reduce overfitting.

- **Decision Trees**: Can handle both numerical and categorical data. Each decision node represents a rule or condition, making the model’s decision-making process transparent.

- **Linear Regression**: Linear Regression is straightforward to implement and easy to interpret. 

**Feature selection**:

Features      | Variable                                                   |
--------------| ---------------------------------------------------------- |
Target        | rating                                                     | 
Numerical     | 'is_recommended', 'Year', 'Month', 'Date', 'review_length' |
Categorical   | 'author_id', 'review_type', 'merged_review'                |

2.Generate Test Design
- Sample a smaller subset of the data- to ensure a manageable and efficient testing process
  - Testing set size as 10% of overall data
  - Shape: 96242 ,12
 
- Check Data Types: Identify which columns have mixed types
  - ensure that all categorical features are properly encoded into numeric values before training the model.

- Feature and Target Definition: 
  - define feature(x)  and target variable (y)

- Data splitting: 
  - split the data into training and test sets. 20% of the data for testing, 80% for training

3.Build model

- Challenges
  - Encountering a Memory Error due to the large size of the data.

- Adjustment
  - Optimize One-Hot Encoding: to remove less informative features and reduce the feature space.
  - Use Sparse Matrix: Use OneHotEncoder with sparse=True to avoid storing the entire matrix in memory. When using sparse=True, the result is a sparse matrix which is more memory-efficient.
  - Apply SMOTE (Synthetic Minority Over-sampling Technique) SMOTE is applied to the training data ensuring that model trains on a balanced dataset.

4.Assessment 

1. Random Forest Model

![image](https://github.com/user-attachments/assets/4955302e-2a11-45f4-a430-25820eea4b63)

  - Class 5 is having a much higher precision, recall, and F1-score compared to the other class. This suggests that the model is heavily biased towards predicting rating 5.

  - To improve performance across all classes. Try SMOTE to develop data balance.

After optimizing,result as below

![image](https://github.com/user-attachments/assets/ec75d107-d680-4198-9629-2e50f1d39edd)

- Model result review 
  - Improvement: After SMOTE the recall of class 2 and 4  significantly improved.

  - The accuracy of 0.66 is relatively stable compared to the previous model accuracy 0.69.

  - Recommendation 

     Class 3 still suffers from low recall and precision, suggests that the model may need further adjustments or different techniques to improve performance for 
     this class.

2. Decision Tree Model

![image](https://github.com/user-attachments/assets/4b8fa9da-3b27-46a8-a381-5d3bb7650fb2)

- Class 2 has relatively low precision and recall, meaning the model struggles to correctly identify instances of this class.

- To improve model, fine-tune the hyper parameters of the Decision Tree to optimize performance by adjusting tree depth, minimum samples per leaf, and splitting criteria.

![image](https://github.com/user-attachments/assets/21ba89cc-4476-43a2-a2db-01327c9075e8)

- Model result review
  - Accuracy is imrproved to 0.69 after adjust tree depth and sample of leaf.

3. Linear Regression Model

![image](https://github.com/user-attachments/assets/13b3ab80-98f2-4f55-a9f9-f7628f6f8b0a)

Mean Squared Error: 0.383 

R^2 Score: 0.711

# Evaluation

1. Random Forest Model

- Overall Accuracy: 0.66

    - Interpretation: The model's accuracy of 66% indicates that approximately 66 out of 100 predictions are correct.

    - Class 1 and 2 has moderate performance .Class 3 has high precision but zero recall and class 4 struggling with prediction and class 5 is the best in overall model performance.
 
2. Decision Tree Model

- Overall Accuracy: 0.68

  - The model’s accuracy of 68% suggests that approximately 68 out of 100 predictions are correct. This is an improvement over the previous accuracy of 66% in random forest model.

  - Class 1 is moderate performance with recall 42% . class 2 and 3 with low precision around 20% and class 4 is better precision with 31% than 2,3 . Class 5 is the best precision with 76%.

3. Linear Regression Model

 - Mean Squared Error: 0.383 
 - R^2 Score: 0.713
   
![image](https://github.com/user-attachments/assets/a672cb85-94b6-4c70-bf24-108e144c63d2)

    - In class 1, most points are clustered near to 1 but some are near to class 2.
  
    - In class 2. predictions are close to class 2 but some are clustered above and below class2.

    - Class 3 and 4 are poorly predicted and class 5 is the best prediction among all classes.

# Model comparison

- In overall model comparison, will choose Decision Tree model. It gives reasonable precision, recall, and F1-scores across the majority of classes, making it a more robust choice compared to the Random Forest and Linear Regression models.

## Recommendation and Analysis

- Visualize common words in Product_name with rating 3

![image](https://github.com/user-attachments/assets/d39b0374-5809-41ad-9638-3cc2b6410cae)

- Top 5 rating 3 products with short reviews

![image](https://github.com/user-attachments/assets/9646373f-bdf4-4746-a724-aceace4166b7)
 
    1. Lip Sleeping Mask Intense Hydration with Vitamin C
    
    2. Cleansing & Exfloliating wipes
  
    3. Saliccylic Acid Acne Healing Dots
    
    4. Priotini Polypeptide Firming Refillable Moisturize
    
    5. Alpha Beta Extra Strength Daily Peel pads

- "Anti-aging, eye cream, cleansing wipes, and moisturizing products”.
  - These products consistently earned a rating of 3, indicating areas where customer satisfaction could be improved. Sephora needs to prioritize improvements to these products to better meet customer expectations.





## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here.
https://github.com/CrystalSoe/itd214
