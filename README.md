# Final_Project

## Notes

### Communication

1. Using Slack for most communications
2. Meeting Mondays at 7 to prepare ourselves for the weekly meetings and segment deliverables

### Important Links

1. location of dataset: <https://www.consumerfinance.gov/data-research/hmda/historic-data/?geo=nationwide&records=all-records&field_descriptions=codes>
2. Google Slides presentation: [Mortgage Loan Approval Calculator](<https://docs.google.com/presentation/d/10wGSHtKTgT1KMNkHMMkzDM7hiJk7xlth1AUYh64E-4w/edit?usp=sharing>)
3. Tableau Dashboad: <https://public.tableau.com/app/profile/victor.pesantez>






### 7/14/2022 Session

1. Cleaning the dataset
a) Dropping columns applicant_race_2 through applicant_race_5 and coapplicant_race_2 through coapplicant_race_5
b) respondent_id is index
c) add zeros to denied_reason_1 to indicate no denial (working)
d) drop denied_reason_2 and denied_reason_3 (working)

2. For segment 2 deliverables: Anu updating database (SQL); Alex, Victor, Olivia running machine learning models to determine most accurate model with small loss; Yaritza setting up presentation in Google Slides

NOTE: plz wait until we have a cleaned version of dataset before SQL and tableau use.

NOTE: hdma has an api

### 7/19/2022 Session

1. Additional Cleaning: All steps above were taken and...
a) removing outliers from the data under assumption that our dataset it normally distributed

2. Binning the data
a) Using the Action Taken column, add new column that condenses codes 1 and 6 to "Accepted", 4 and 5 to "Other", and 2, 3, 7, and 8 to "Denied." Drop "Other," and then This will be used as our output variable 

3. Once cleaned, (no null values), we will split the dataset into a smaller proportional sample (bc 14mil rows is not working on our computers)
a) decide on a number of sample csv's with proportions of output column similar to population (large csv)
b) current potential options: race/ethnicity (combine columns??), income bracket (bin), population size (bin), or agency type

4. In reference to the rubric, Anu is cleaning the model via SQL and will export new table for us to use. The data will be split into proportional groups based on choices (Alex?), run machine learning models (everyone?), reconvene and determine which models are working the best for the groups that we choose. What do we want to include in the presentation (Yartiza), create visualizations of our data in Tableau or something similar (Victor)

### 7/21/2022 Session

1. Running into issues with github storage, so to combat, we will only create important csv files, which will include...
a) machine learning model - proportional sample (based on action taken summary column)
b) visualization portion - income and loan amount binned (for analysis of columns)
c) hypothesis tests? - proportional sample (other variables yet to be determined like race, agency type, etc)
NOTE: original file is too large to get it on here

2. Create a cleaning file so that all that has to be done is run input file and it will automatically spit out a useful output file.

### 7/26/2022 Session

1. Preprocessed file is complete. We took a 1% sample of the file and are using that to run models on (the sample has >100,000 rows, so its big). 
a) had to run the preprocessed file through two jupyter notebooks because I kept running into error issues: prop_sample.ipynb abd prop_sample_v2.ipynb

2. Running models today, will submit deliverable 2 today.

3.

### 7/28/2022 Session

1. Instructor confirms that database deliverables are met, and helps make integration more efficient by recommending the use of Pickle to compress results and take less space/time.
2. Anu imports pickle in database_integration.ipynb, re-runs the codes, and creates a .pkl output. Anu sends .pkl output and updated code to team in Slack channel. This completes the database integration portion of the project in segment 2.
3. Yaritza plans to share presentation work with Anu to ramp up presentation portion of the project. She shared google_slides_presentation_in_progress with team, and showed samples of a deck template for use in the final presentation.
4. Victor creates charts to display metrics like denial_reason & applicant_income, then begins work in Tableau to plot data and display results. 
5. Team will submit complete deliverable 2 today

# Rubric Double Check

## Segment One

### Presentation

1. Selected Topic: Mortgage Loan Approval Calculator
2. Reason why topic is selected: Housing market is nuts, thus making it a topic of interest
3. Description of data source: hdma 2017 loan data
4. Questions we want data to answer: what variables most affect the approval of a mortgage

### Github

1. Include README: Done
2. README has description of the communication protocols: see above
3. Individual branches for each member: Done
4. Four commits from each member: probably impossible for segment 1

### Machine Learning Model

1. Take in data from provisional database: done
2. outputs labels for input data: loan approval is output and "several factors" for input

### Database:

1. sample data that mimics expected final database structure or schema: hmda 2017 nationwide; lending club?
2. Draft machine learning module is connected to the provisional database: working

## Segment 2

### Presentation

1. Description of the data exploration phase of the project: ok
2. Description of the analysis phase of the project: ok
3. Begin drafting slides in google slides: ok

### Github

1. All code necessary to perfomr exploratory analysis in github: working
2. Some code necessary to complete machine learning portion: ok

### Machine Learning Model

1. Description of preliminary data preprocessing: been taking notes above, however, to summarize, changed values in the columns where there are categorical variables, eliminated useless columns, reworked the state column to regions (US), created a categorizing variable with the action taken column (approved v denied).

2. Description of preliminary feature engineering and preliminary feature selection, including their decision-making process: 

a) columns eliminated: respondent_id, applicant_race_2, applicant_race_3, applicant_race_4, applicant_race_5, co_applicant_race_2, co_applicant_race_3, co_applicant_race_4, co_applicant_race_5, denial_reason_1, denial_reason_2, denial_reason_3, rate_spread, edit_status, sequence_number, application_date_indicator, msamd, as_of_year, county_code, census_tract_number

b) reason behind column elimination: identifiers do not apply to machine learning models, applicant race 1 and coapplicant race 1 should be sufficient as there are too many null values in the other applicant and coapplicant race columns, denial reasons act as a predictor of the model so removed to provide better learning model, unnecessary columns, or columns with too many categorical variables that are not easily binned or can be explained by another column

c) transformations: States to regions - converts state numbers to regions in order to better bin the data, all other categorical variables have values changed to reflect their actual meaning vs the number it is assigned. This also converts dtype to object, which makes it easier to separate out using OneHotEncoder. Action taken - converts the 8 variables into two variables which is more usable for categorical model. 

d) removed null values from remaining rows bc it is immaterial (10mil values remaining)

e) purchaser type removed in the machine learning model runs because it also acts like the denial reason - if it isn't there, than it is approved and falsely predicts model

f) see prop_sample.ipynb and prop_sample_v2.ipynb for data preprocessing and feature selection and engineering

3. Description of how data was split into training and testing sets: Olivia running neural network and Alex running random forest classifier

## Segment Three

### Machine Learning Model

1. Finally got the dataset together, running models of pickled data. 

a) Initial Cleaning Phase 1: Removed as_of_year, applicant_race_2, applicant_race_3, applicant_race_4, applicant_race_5, co_applicant_race_2. co_applicant_race_3, co_applicant-race_4, co_applicant_race_5, denial_reason_2, denial_reason_3, rate_spread, edit_status, sequence_number, and applicantion_date_indicator bc of duplicity and obsolescense. 

b) Intial Cleaning Phase 2: For columns agency_code, loan_type, property_type, loan_purpose, owner_occupancy, preapproval, action_taken, state_code, applicant_ethnicity, co_applicant_ethnicity, applicant_race_1, co_applicant_race_1, applicant_sex, co_applicant_sex, purchaser_type, hoepa_loan, and lien_status, change values to reflect categories and change dtype to object

c) Intial Cleaning Phase 3: Transform state_code to Region for a more concise explanation. Also transform action_taken to action_taken_summary to create a column for approvals and denials

d) Initial Cleaning Phase 4: Fill N/A values with 0 in columns msamd, applicant_income_000s, and denial_reason_1

e) Initial Cleaning Phase 5: Drop any remaining rows with null values from the dataset. Retention: 97.98% of data points (13,997,124 rows retained out of 14,285,496 rows from the raw data)

f) Transformation Phase 1: Export to pickle file and share with group via Google Drive

g) Machine Model Cleaned Version Phase 1: Drop denial_reason_1, lien_status, hoepa_status, state_code, purchaser_type, respondent_id, and action_taken columns because of circular references or obsolescence. This was determined from prior models using sample data

h) Machine Model Cleaned Version Phase 2: Drop rows that do not provide enough information to base the model off of. Only use "Home Purchase" from loan_purpose column, remove "Not Applicable" values from owner_occupancy, remove "Information not Provided" and "Not Applicable" values from applicant_sex, co_applicant_sex, applicant_ethnicity, and co_applicant_ethnicity columns, remove "Not Applicable" values from preapproval column, remove outliers from loan_amount_000s column, remove "2" values from action_taken_summary (anything other than approved or denied status).

i) Machine Model Cleaned Version Summary: Retained about 1,700,356 datapoints/rows

j) Transformation Phase 2: Export to new pickle file for use on machine learning models

k) Preprocess Phase 1: Rows with dtype "object" transformed into categorical variables. These columns include agency_code, loan_type, property_type, owner_occupancy, preapproval, applicant_ethnicity, co_applicant_ethnicity, applicant_race_1, co_applicant_race_1, applicant_sex, co_applicant_sex, Region

l) Preprocess Phase 2: Drop any exported categorical variable columns that are redundant

2. Neural Networks

a) Using action_taken_summary as the target output, run the neural network...

b) First run through: 3 hidden layers, first two are relu, third is leaky relu, output is sigmoid. Loss metric is binary_crossentropy, optimizer is adam, with metrics as accuracy. Using 50 epochs, the final output is loss: 0.3837 ccuracy: 0.8715

c) Second run through: same as above, just removed the redundant columns (preprocess phase 2)

d) Third run through: added a hidden layer, change all input/hidden layer activation functions to relu, same loss and accuracy as first run through

e) Fourth run through: 

3. Random Forest Classifier


### Dashboard

1. Using Tableau, visuals created using the sample file (other file too large, but this has representative data)
2. Link above in readme.
