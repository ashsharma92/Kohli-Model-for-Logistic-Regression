# Kohli Model for Logistic Regression
This model will help to estimate the likelihood of Virat Kohli's IPL team (Royal Challengers Bangalore) winning a game if he has scored a half century. A logistic regression model was used for this purpose.
A logistic regression model was developed to assess the likelihood of Royal Challengers Bangalore winning an IPL match based solely on whether Virat Kohli scored a half-century in that game. The model was trained and evaluated on a subset of IPL match data.

The model achieved an overall accuracy of approximately 54.5% on the test set, indicating a slightly better than random predictive capability. Further examination of the classification report reveals nuanced performance across the two outcome classes (Win and Loss).

For matches resulting in a loss for Royal Challengers Bangalore (Class 0), the model demonstrated a precision of 0.51 and a recall of 0.83. This suggests that while only about half of the predicted losses were actually losses, the model successfully identified a high proportion of the true loss outcomes.

Conversely, for matches where Royal Challengers Bangalore won (Class 1), the model exhibited a precision of 0.67 but a considerably lower recall of 0.29. This implies that while two-thirds of the predicted wins were accurate, the model missed a significant number of actual victories. The F1-scores for both classes (0.63 for Loss, 0.41 for Win) further highlight the imbalance in predictive performance.

The confusion matrix illustrates these findings, showing a higher number of true negatives (correctly predicted losses) compared to true positives (correctly predicted wins), along with a substantial number of false negatives (missed wins).

The coefficient associated with the 'Kohli_Half_Century' feature was found to be approximately 0.28. This positive coefficient suggests that scoring a half-century by Virat Kohli is associated with an increase in the log-odds of Royal Challengers Bangalore winning. However, the relatively small magnitude of the coefficient, coupled with the overall model performance, indicates that this single factor has a limited predictive power for match outcomes. The intercept of the model was approximately -0.26.

In conclusion, while the logistic regression model indicates a positive correlation between Virat Kohli scoring a half-century and the team's likelihood of winning, this single variable is not a strong predictor of match outcome. The model's accuracy is modest, and its ability to identify wins is particularly limited. Future iterations of this analysis should consider incorporating additional features known to influence IPL match results to potentially develop a more robust and accurate predictive model. These features could include the performance of other key players, opponent team strength, venue characteristics, and overall team form.


STEPS to do this project:
