# Football_xG_Model_Prediction-
My FYMSc(CS) mini-project for second sem. A football xG_prediction web app made using Flask as backend,python to train models based on random forest,logistic regression and xgBoost algorithms.Basic frontend in HTML ,CSS and javascript.




<img width="344" height="1307" alt="image" src="https://github.com/user-attachments/assets/e16cb2c8-2e3e-4cc3-bf23-fcdaae9e23ce" />

Dataset Discussion
1. Data Collection
Data Source : 
The dataset is sourced from StatsBomb, an open-access football analytics provider that offers detailed event data for various competitions. StatsBomb uses a 120x80 meter coordinate system for pitch events, with the origin (0, 0) at the bottom-left corner and the goal at (120, 40). The data includes granular details about shots, such as location, type, outcome, and contextual factors like pressure and key passes.
The specific competitions used are:
2018 FIFA World Cup (Competition ID: 43, Season ID: 3): A high-profile international tournament with 64 matches, featuring top national teams. Shot data reflects a variety of playing styles and high-stakes scenarios.

La Liga 2021/2022 (Competition ID: 11, Season ID: 90): A top-tier domestic league with 380 matches, known for technical play and possession-based strategies, providing a robust sample of club-level shots.

2. Data Preprocessing
●	Dataset Size and Composition
Total Shots: Without subsampling, the three competitions yield approximately 13,000–14,000 shots (based on typical shot counts: ~1,000 from the World Cup, ~7,000–8,000 from La Liga, ~4,000–5,000 from Champions League).
Subsampled Size: ~6,000 shots, balancing computational efficiency with sufficient data for model training.
Breakdown:
World Cup: ~7–8% of shots (high-intensity, fewer matches).

La Liga: ~50–60% (high volume due to 380 matches).

●	Removing outliers (shots from unrealistic distances).
●	Standardizing unit measurements (e.g., converting shot distances to meters)
3. Feature Engineering
The dataset includes both raw and derived features:
Raw Features:
x (float, 0–120): Horizontal position.
y (float, 0–80): Vertical position.
shot_type (categorical): Type of shot attempt.

defensive_pressure (categorical): Simplified pressure indicator.

assist_type (categorical): Basic assist context.

goal (binary): Target variable.

Derived Features:
shot_distance (float, meters): Distance to goal, critical for xG as closer shots are more likely to score.

angle (float, degrees): Angle to goal, where wider angles correlate with higher scoring probability.

4. Machine Learning Model
1.	Model Selection:
●	Baseline Model: Logistic Regression (interpretable but limited).
●	Advanced Models:
○	XGBoost (Gradient Boosting for structured data).
○	LightGBM (Efficient for large datasets).
○	Neural Networks (Deep Learning for advanced spatial analysis).
2.	Training & Evaluation:
●	Loss Functions: Log Loss (for probability calibration), Brier Score (for reliability).
●	Performance Metrics:
○	ROC-AUC Curve: Measures model accuracy in distinguishing goal/no goal.
○	Calibration Curve: Ensures predicted probabilities match actual conversion rates.
●	Cross-Validation: Splitting data into train/test sets to avoid overfitting.
3.	Model Optimization:
●	Grid Search / Bayesian Optimization to tune hyperparameters.
●	Feature Importance Analysis to refine predictions

5. Prediction Layer
●	xG Score Calculation: Probability of shot success
●	The model assigns a probability score (0-1) to every shot based on input features.
●	Example: A shot from 10 meters with no defensive pressure might have xG = 0.75 (75% chance of scoring).
●	Comparing xG vs Actual Goals


6. Visualization
●	hot Maps: Visual representation of where shots are taken and their xG values.
●	Heatmaps: Highlights areas where teams generate the most high-xG chances.
●	Player Performance Dashboards: Displays xG trends across matches and seasons.
7. Deployment & Integration
●	Real-time xG Predictions:
○	Apache Kafka for streaming match data.( If applicable )
○	Live dashboards updating xG predictions in real-time.
●	Dashboard Integration:  custom web applications.
