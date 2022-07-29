# Final_Project

Notes

Communication

Using Slack for most communications
Meeting Mondays at 7 to prepare ourselves for the weekly meetings and segment deliverables.

7/14/2022 Session

1. Cleaning the dataset a) Dropping columns applicant_race_2 through applicant_race_5 and coapplicant_race_2 through coapplicant_race_5 b) respondent_id is index c) add zeros to denied_reason_1 to indicate no denial (working) d) drop denied_reason_2 and denied_reason_3 (working)
2. For segment 2 deliverables: Anu updating database (SQL); Alex, Victor, Olivia running machine learning models to determine most accurate model with small loss; Yaritza setting up presentation in Google Slides


7/19/2022 Session

1. Additional Cleaning: All steps above were taken and... a) removing outliers from the data under assumption that our dataset it normally distributed
2. Binning the data a) Using the Action Taken column, add new column that condenses codes 1 and 6 to "Accepted", 4 and 5 to "Other", and 2, 3, 7, and 8 to "Denied." Drop "Other," and then This will be used as our output variable
3. Once cleaned, (no null values), we will split the dataset into a smaller proportional sample (bc 14mil rows is not working on our computers) a) decide on a number of sample csv's with proportions of output column similar to population (large csv) b) current potential options: race/ethnicity (combine columns??), income bracket (bin), population size (bin), or agency type
4. In reference to the rubric, Anu is cleaning the model via SQL and will export new table for us to use. The data will be split into proportional groups based on choices (Alex?), run machine learning models (everyone?), reconvene and determine which models are working the best for the groups that we choose. What do we want to include in the presentation (Yartiza), create visualizations of our data in Tableau or something similar (Victor)


7/21/2022 Session

1. Running into issues with github storage, so to combat, we will only create important csv files, which will include... a) machine learning model - proportional sample (based on action taken summary column) b) visualization portion - income and loan amount binned (for analysis of columns) c) hypothesis tests? - proportional sample (other variables yet to be determined like race, agency type, etc) NOTE: original file is too large to get it on here
2. Create a cleaning file so that all that has to be done is run input file and it will automatically spit out a useful output file.


7/26/2022 Session

1. Preprocessed file is complete. We took a 1% sample of the file and are using that to run models on (the sample has >100,000 rows, so its big). a) had to run the preprocessed file through two jupyter notebooks because I kept running into error issues: prop_sample.ipynb abd prop_sample_v2.ipynb


7/28/2022 Session

1. Instructor confirms that database deliverables are met, and helps make integration more efficient by recommending the use of Pickle to compress results and take less space/time.
2. Anu imports pickle in database_integration.ipynb, re-runs the codes, and creates a .pkl output. Anu sends .pkl output and updated code to team in Slack channel. This completes the database integration portion of the project in segment 2.
3. Yaritza plans to share presentation work with Anu to ramp up presentation portion of the project. She shared google_slides_presentation_in_progress with team, and showed samples of a deck template for use in the final presentation.
4. Victor creates charts to display metrics like denial_reason & applicant_income, then begins work in Tableau to plot data and display results.
5. Team will submit complete deliverable 2 today

