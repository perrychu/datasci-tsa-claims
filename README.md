# datasci-tsa-claims
Prediction of TSA (Transportation Security Administration) passenger claim outcomes.

## Summary
This is my classification project for Metis (a data science bootcamp). It includes data cleaning and exploration of [200k TSA passenger claims from 2002-2015](https://www.dhs.gov/tsa-claims-data), and a pipeline for model & feature validation.

The goal is to predict whether a TSA claim will be approved, settled, or denied (i.e. full / partial / no payment). With
an accurate predictor, there would be a few uses:
* Passenger / insurance – Predict if a claim will be approved (is it worth submitting given filing costs?)
* TSA – Automate initial triage of claims, infer areas that can be targeted to avoid cost (or prevent passenger dissatisfaction)

Some concepts I explored were class imbalance, picking useful performance metrics, and methods for representing categorical variables.

## Files:
#### Code
* **TSA_Data_Cleaning.ipynb** - EDA of raw features, cleaning (e.g., merging inconsistent categories, removing nulls)
  * tsa_claims.csv.zip - Raw data archive from Kaggle (compiled from dhs.gov/tsa-claims-data)
  * tsa_claims_clean.csv - Cleaned data file
* **TSA_Feature_Model.ipynb** - Feature engineering, feature selection (using random forest baseline), model selection, model tuning

#### Docs
* **TSA_Claims_Slides.pdf** - Project presentation slides
* **TSA_Claims_Writeup.pdf** - Outline of project process

## Results
I used accuracy to test the model since the target was fairly balanced across classes (47/31/22%) and accuracy should be a good metric for a general predictive model case. However, it would be interesting to pick a metric for a specific use case (e.g. maximize precision for TSA traige or recall for helping customers decide whether to file a claim).

The best model was XGBoost, which had 57.6% accuracy after hyperparameter tuning.

The most important features (by information gain) were claim value, claim site (e.g. vehicle, checkpoint, security), and claim type (e.g. damage, loss, injury). See presentation slides for some exploration of those features.
