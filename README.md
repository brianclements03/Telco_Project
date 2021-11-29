## DESCRIPTION

### This project is an exploration of our customers' churn through a database of information related to their accounts. Certain demographic information will be looked at, as well as what types of services and contracts they have, charges, and use behavior (e.g. tenure and churn).




## GOALS

### The goal of this project is to explore factors related to customer churn at Telco, and to develop a machine learning model in an attempt to predict future churn. 

## PROJECT PLANNING (i.e. the data science pipeline)

### Wrangle the data: acquire from the Codeup database. Then clean, prep and split it into train, validate and test sets.  From here, I explored the data (from univariate to bivariate and multivariate, respectively), asking questions that I wanted to answer as I went.  Once the data had been explored to my satisfaction, I built different machine learning models in an attempt to predict which customers were most likely to churn.

## REPRODUCABILITY

### The main tools needed to reproduce the project are the database itself, and numerous python imports (e.g. pandas, sklearn, numpy, etc--an exhaustive list can be referred to at the top of my code).  For graphing purposes, seaborns is handy, as is a knowledge of statistical testing that is available in the sklearn and other libraries available for python.

## ANSWERS TO YOUR HYPOTHESES, KEY FINDINGS, RECOMMENDATIONS, TAKEAWAYS

## Research Question 1
Are those with dependents paying less? What about their churn? We can see in the next cell that they churn less.
### Answer to Research Question 1:
Our chi^2 test shows that we can proceed with the understanding that customers with dependents churn less; additionally, it is clear from the charts that they are charged less but still provide a higher lifetime value.

## Research Question 2
We know that people with paperless billing they churn at a higher rate; could this be related to their contract type, or perhaps higher monthly charges?
### Answer to Research Question 2:
Our chi^2 test shows that we can proceed with the understanding that paperless billing is related to churn; these customers also pay more every month.

## Research Question 3
Are people with longer tenure creating more long-term value? 
### Answer to Research Question 3:
Our mann-whitney test shows that we can proceed with the understanding that tenure is related to churn, obvious as it may seem; customer churn goes down as their lifetime value (measured in total charges) goes up. Interestingly, there is a point at which total charges point to a higher level of churn--perhaps an area for further exploration. 

## Research Question 4
How does the electronic check payment method relates to higher churn?
### Answer to Research Question 4:

The seaborns charts and chi^2 test above demonstrate that paying by electronic check relates to higher churn--in spite of the fact that these customers are not paying very much more per month! One conclusion is that this form of payment relates to a lower commitment to the the company, and therefore higher churn.


# DATA DICTIONARY

 #   Column                                 Non-Null Count  Dtype  
---  ------                                 --------------  -----  
 0   customer_id                            7043 non-null   object 
 1   gender                                 7043 non-null   object 
 2   senior_citizen                         7043 non-null   int64  
 3   partner                                7043 non-null   object 
 4   dependents                             7043 non-null   object 
 5   tenure                                 7043 non-null   int64  
 6   phone_service                          7043 non-null   object 
 7   multiple_lines                         7043 non-null   object 
 8   online_security                        7043 non-null   object 
 9   online_backup                          7043 non-null   object 
 10  device_protection                      7043 non-null   object 
 11  tech_support                           7043 non-null   object 
 12  streaming_tv                           7043 non-null   object 
 13  streaming_movies                       7043 non-null   object 
 14  paperless_billing                      7043 non-null   object 
 15  monthly_charges                        7043 non-null   float64
 16  total_charges                          7043 non-null   float64
 17  churn                                  7043 non-null   object 
 18  contract_type                          7043 non-null   object 
 19  internet_service_type                  7043 non-null   object 
 20  payment_type                           7043 non-null   object 
 21  gender_Male                            7043 non-null   uint8  
 22  partner_Yes                            7043 non-null   uint8  
 23  dependents_Yes                         7043 non-null   uint8  
 24  phone_service_Yes                      7043 non-null   uint8  
 25  multiple_lines_No phone service        7043 non-null   uint8  
 26  multiple_lines_Yes                     7043 non-null   uint8  
 27  online_security_No internet service    7043 non-null   uint8  
 28  online_security_Yes                    7043 non-null   uint8  
 29  online_backup_No internet service      7043 non-null   uint8  
 30  online_backup_Yes                      7043 non-null   uint8  
 31  device_protection_No internet service  7043 non-null   uint8  
 32  device_protection_Yes                  7043 non-null   uint8  
 33  tech_support_No internet service       7043 non-null   uint8  
 34  tech_support_Yes                       7043 non-null   uint8  
 35  streaming_tv_No internet service       7043 non-null   uint8  
 36  streaming_tv_Yes                       7043 non-null   uint8  
 37  streaming_movies_No internet service   7043 non-null   uint8  
 38  streaming_movies_Yes                   7043 non-null   uint8  
 39  paperless_billing_Yes                  7043 non-null   uint8  
 40  churn_Yes                              7043 non-null   uint8  
 41  contract_type_One year                 7043 non-null   uint8  
 42  contract_type_Two year                 7043 non-null   uint8  
 43  internet_service_type_Fiber optic      7043 non-null   uint8  
 44  internet_service_type_None             7043 non-null   uint8  
 45  payment_type_Credit card (automatic)   7043 non-null   uint8  
 46  payment_type_Electronic check          7043 non-null   uint8  
 47  payment_type_Mailed check              7043 non-null   uint8  

Please note the following, user-defined functions used:
    -get_telco_data: accesses an existing csv file or creates one in its absence (using new_telco_data)
    -new_telco_data: runs a SQL query to create a new Telco csv from the Codeup database
    -get_connection(db, user=user, host=host, password=password): uses my info from my env file to create a connection url to access the Codeup db. It takes in a string name of a database as an argument. The env file includes the username, password and host address as seen in the curly brackets
    -prep_telco: cleans up the telco dataframe to make analysis easier
    -split_telco_data: splits the telco dataframe into train, validate, test subsets
    -cols_to_dummy: converts the train data set into an encoded version, dropping all string type columns


