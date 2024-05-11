# README for Writing Quality Prediction: A Stacked Ensemble Approach

This project aims to predict writing quality based on various features extracted from the writing process logs and essay content. It leverages a stacked ensemble model that combines multiple regression algorithms to achieve higher accuracy and robustness.

## Key Components

1. **Data Preparation**

    **Data Sources:**
    - `train_logs.csv`: Detailed logs of writing activities (e.g., input, deletion, cursor movement) for training essays.
    - `train_scores.csv`: Writing quality scores for the corresponding training essays.
    - `test_logs.csv`: Writing process logs for test essays (for prediction).
    - `train_essays_fast.csv`: Preprocessed essay texts for training.

    **Feature Engineering:**
    - **Time-based Features:** Time gaps between actions, total writing time, initial pauses, etc.
    - **Text-based Features:** Word count, sentence length, paragraph structure, punctuation usage.
    - **Activity and Event Features:** Frequencies of different actions (e.g., typing, deleting) and events (e.g., keystrokes).
    - **Statistical Summaries:** Aggregations like mean, standard deviation, quantiles, skewness, and kurtosis of various features.

2. **Model Development**

    **Stacked Ensemble:** A two-layer ensemble model is used:
    - **Base Models:** Lasso, ElasticNet, Ridge regression, Gradient Boosting, Random Forest, CatBoost, XGBoost, and Support Vector Regression.
    - **Meta-Model:** Linear Regression is used to combine the predictions of the base models.
    
    **Hyperparameter Optimization:** Grid search and stratified cross-validation are employed to find the best hyperparameters for each base model and the blending weights for the ensemble.

3. **Training and Evaluation**

    **Training Process:**
    - The dataset is split into folds using stratified K-fold cross-validation.
    - Base models are trained on each fold, and their predictions are used to train the meta-model.

    **Evaluation Metric:** Root Mean Squared Error (RMSE) is used to evaluate the model's performance.

4. **Prediction and Submission**

    **Blending:** The final predictions are obtained by blending the predictions of the individual models using optimized weights.
    
    **Post-processing:** Predictions are clipped to ensure they fall within the valid score range (0 to 6).
    
    **Submission:** The predictions for the test essays are formatted and saved in a CSV file for submission.

## Results

The stacked ensemble model achieved a competitive RMSE score on the validation set, demonstrating its effectiveness in predicting writing quality.

Feel free to explore and modify the code to experiment with different feature engineering techniques and model combinations.
