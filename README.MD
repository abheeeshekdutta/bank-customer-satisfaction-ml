# Bank customer satisfaction prediction 

## Project Objective 

This project involves working with a dataset of bank customer satisfaction survey responses. The general objective here is to predict whether customers are satisfied with the bank based on their survey responses. The dataset consists of two different representations for the same set of customers:

1. Tabular data (bank-tabular.csv) which contains demographic information about each customer and ratings scores (1-5) relating to different aspects of their bank. A manually-labelled ‘satisfied’ variable indicates whether a customer is ‘satisfied’ or ‘dissatisfied’ with the bank.

2. Text data (bank-comments.csv) which contains short textual comments indicating customers' opinions regarding the bank. 

## Methodology Overview

The project is broadly divided into multiple tasks as mentioned below. For more details, refer to the Jupyter notebook file. 

### 1. Data preparation/pre-processing

1. Converting date columns to their correct format and datatype
2. Analysis and handling of missing values
3. Standardizing columns such as gender

### 2. Data Characterization

1. Exploring the distribution of numerical and categorical features
2. Building correlation plots
3. Performing temporal analysis based on customer satisfaction rates

### 3. Tabular Data Classification

1. Applying feature transformations:
    - Scaling numerical features
    - Encoding categorical features

2. Developing a model training & evaluation strategy: 
    - Classification models used: K-Nearest Neighbours(KNN), Decision Trees, Gaussian Naive Bayes
    - For each of the above models, different hyperparameters were used and the tuning was performed using Grid Search
    - Evaluation metrics used: accuracy, precision, f1 score and training time

### 4. Textual Data Classification

1. Applying feature transformations:
    - Converting text to lowercaes
    - Stripping off whitespaces, hyphens and tabs
    - Removing all special characters, single character/numbers
    - Removing words which do not exist in the English vocabulary
    - Removing records where the survey text seemed meaningless - e.g 'nothing to say', 'no comments' etc.

2. Developing a model training & evaluation strategy: 
    - Classification models used: K-Nearest Neighbours(KNN), Decision Trees, Gaussian Naive Bayes
    - For each of the above models, different hyperparameters were used and the tuning was performed using Grid Search
    - Evaluation metrics used: accuracy, precision, f1 score and training time

## File Formats 

The file bank-tabular.csv is a tab-separated text file containing the following fields:

 - customer_id: A unique identifier for each customer.
 - date: The date on which the survey was conducted.
 - customer_gender: The gender of the customer.
 - customer_age: The age of the customer.
 - customer_location: The location of the customer in Ireland.
 - customer_type: The type of the customer.
 - has_cc: Indicates whether or not the customer has a credit card with the bank.
 - has_mortgage: Indicates whether or not the customer has a mortgage with the bank.
 - convenience: The customer's rating score (1-5) for the availability and accessibility of the bank. Customers want their bank to be easily accessible through multiple channels such as branches and ATMs.
 - customer_service: A rating score (1-5) for customer service, including response time, friendliness, and competence of bank staff.
 - online_banking: A score (1-5) for the ease of use, functionality, and availability of online banking services
 - interest_rates: A score (1-5), where customers may be more satisfied with their bank if they offer competitive interest rates on savings and mortgages.
 - fees_charges: A score (1-5), where customers may be more dissatisfied when they are charged fees for services they did not expect, or when the fees/charges are high.
 - community_involvement: A score (1-5), where customers may have a more favorable view of their bank if they are involved in the local community and support charitable causes.
 - products_services: A score (1-5) which relates to the quality and variety of products and services offered by the bank.
 - privacy_security: The customer's score (1-5) reflecting whether customers believe their bank provides high levels of security and privacy, and manage their personal data carefully.
 - reputation: A score (1-5) indicating whether customers believe their bank has a good reputation for reliability and ethical practices.
 - satisfied: A manually-assigned boolean value indicating whether a customer is satisfied overall with their bank.


The file bank-comments.csv is a tab-separated text file containing the following fields:

- customer_id: A unique identifier for each customer.
- date: The date on which the survey was conducted.
- comments: The short text comments provided by customers about their bank.

## Results and conclusions
1. For the classification of tabular data, gaussian naive baye's was our best choice with an accuracy of about 84%, F1 score of 82% and minimal training time.

2. For the classification of text data, k-nearest neighbors was our best choice with an accuracy of about 95%, F1 score of 95% and minimal training time.

3. Based on the above results, we can say that the text representation is clearly more suitable for determining the customer satisfaction based on survey results. None of the models that were run on the tabular data could provide an accuracy or F1 score of more than 90%

4. Data pre-processing for the text data was much more complicated than tabular data, because of a variety of possibilities in the comments provided.

5. Since the dataset wasn't very large in both types of representations, the training times were in the order of milliseconds and less, but KNN took the least training time in both scenarios because of its simplicity.

6. Decision Trees are known to overfit, especially when there are too many features in the model. Therefore it has not performed well at all in the text classification.

## Insights from analysis

1. There were many missing values in the tabular dataset especially across the survey metrics such as convenience, reputation etc.

2. Females responded to the survey more than males. In terms of location, Leinster had the most number of customers.

3. Percentage of satisfied customers has dropped slightly from 2021 to 2022.

4. Survey result for online banking, convenience, fees charges and interest rates showed the highest amount of positive correlation with customer satisfaction

## Challenges faced

1. The pre-processing of text data was a big challenge due to the variety of missing/irrelevant values in the comments provided. I had to manually look for variations and account for them while preparing my regular expression.

2. Dealing with missing values for the survey metrics was a bit tricky as well since they were discrete values ranging from 1 to 5. The missing values were imputed based on average value and it was rounded off to fit the existing format.

## Ideas for further analysis/classification

1. The machine learning steps for both kinds of data could be converted to pipelines

2. Feature engineering should be implemented to reduce the dimensionality of data especially for text classification and to improve model performance

3. More amount of data should be collected and ingested into analysis and classification models so that we may have a better representation of customer viewpoints.