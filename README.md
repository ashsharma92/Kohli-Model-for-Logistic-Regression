# Kohli Model for Logistic Regression
This model will help to estimate the likelihood of Virat Kohli's IPL team (Royal Challengers Bangalore) winning a game if he has scored a half century. A logistic regression model was used for this purpose.
A logistic regression model was developed to assess the likelihood of Royal Challengers Bangalore winning an IPL match based solely on whether Virat Kohli scored a half-century in that game. The model was trained and evaluated on a subset of IPL match data.

The model achieved an overall accuracy of approximately 54.5% on the test set, indicating a slightly better than random predictive capability. Further examination of the classification report reveals nuanced performance across the two outcome classes (Win and Loss).

For matches resulting in a loss for Royal Challengers Bangalore (Class 0), the model demonstrated a precision of 0.51 and a recall of 0.83. This suggests that while only about half of the predicted losses were actually losses, the model successfully identified a high proportion of the true loss outcomes.

Conversely, for matches where Royal Challengers Bangalore won (Class 1), the model exhibited a precision of 0.67 but a considerably lower recall of 0.29. This implies that while two-thirds of the predicted wins were accurate, the model missed a significant number of actual victories. The F1-scores for both classes (0.63 for Loss, 0.41 for Win) further highlight the imbalance in predictive performance.

The confusion matrix illustrates these findings, showing a higher number of true negatives (correctly predicted losses) compared to true positives (correctly predicted wins), along with a substantial number of false negatives (missed wins).

The coefficient associated with the 'Kohli_Half_Century' feature was found to be approximately 0.28. This positive coefficient suggests that scoring a half-century by Virat Kohli is associated with an increase in the log-odds of Royal Challengers Bangalore winning. However, the relatively small magnitude of the coefficient, coupled with the overall model performance, indicates that this single factor has a limited predictive power for match outcomes. The intercept of the model was approximately -0.26.

In conclusion, while the logistic regression model indicates a positive correlation between Virat Kohli scoring a half-century and the team's likelihood of winning, this single variable is not a strong predictor of match outcome. The model's accuracy is modest, and its ability to identify wins is particularly limited. Future iterations of this analysis should consider incorporating additional features known to influence IPL match results to potentially develop a more robust and accurate predictive model. These features could include the performance of other key players, opponent team strength, venue characteristics, and overall team form.

Data Dictionary:


STEPS to do this project:

1. First in terms of sourcing the information I used this website to generate a CSV of all of Virat Kohli's innings from his debut match till now. The issue with this dataset was that it did not contain match result (win or loss).
2. I then had to use the same website to source all the match results from each season from 2008 till 2025. Once downloaded I then ensured that each dataset had a match_id column that matches with the Kohli dataset to ensure a join could be executed in python.
3. I imported all the datasets into Jupyter notebooks as dataframes and then noticed that the Team1 and Team2 column (which showed who played against who) for each row also contained scorecard information. I then had to use a bespoke function to ensure I can extract only the team name from these columns as this was needed for down the line. I executed this function by using the .apply method on all dataframes for all seasons. In hindsight I could have done this in one go down the line!
4. I then used pd.concat to utilise a union for all these dataframes as they contained the same data type and headings this was possible.I also saw that some columns existed that were null and some rows also came up null. I used standard techniques to drop them and called this df_union_cleaned.
5. I then uploaded the Kohli scores dataset.
6. I also then reduced the size of the df_union_cleaned dataframe to only focus on rows which contain either Royal Challengers Bangalore or Royal Challengers Bengaluru as the team had a name change.
7. I then joined this joined dataframe with Kohli's dataset using a left join (Kohli data as left table).
8. I then reduced size of this dataframe further to focus on Strike Rate, 50, Result. This was now called final_data.
9. After this I then changed the Result cell entries to a binary output by making a new column and making use of np.where to change entries from RCB to 1 (for a win) and other teams to 0.
10. In the last block of code I used various python libraries and functions to make a logistic regression model, train on 80% data, make predictions on test set and then evaluate the model and interpret the coefficient.
