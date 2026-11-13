# Preliminary Results

Note: Model owners please use the shared setup provided in main

| Model | Settings | Val ROC AUC | ± std | Train ROC AUC | Gap | Recall (default threshold) | Fit time (ms) | Predict time (ms / 1000 rows) | Status |
|---|---|---|---|---|---|---|---|---|---|
| Majority baseline | DummyClassifier (prior) | 0.5 | 0 | 0.5 | 0 | 0 | 11.6 | 14.2 | Measured in Main (evaluate_model), final setup |
| Logistic regression (reference) | bmi missing flag, class_weight balanced, C = 0.01 | 0.8592 | 0.0169 | 0.8675 | 0.0083 | 0.819 | 18.7 | 15.5 | Measured in Main (evaluate_model), final setup.|
| SVM | SVC poly, tuned (degree 2, coef0 1, C = 0.1, gamma 0.01, balanced) | 0.847 | 0.029 | 0.855 | 0.008 | 0.869 | 212 | 102 | Old cleaning, different split. Timed on a different machine |
| Random forest | 200 trees, max_features 10, min_samples_leaf 50, balanced | 0.862 | – | – | – | – | – | – | Old cleaning, different split. Sweeps print only the mean. No training score, recall or predict time. Only fit time is for leaf 20 on all cores. Test set already used |
| Gradient boosting | balanced sample weights, 50 trees, learning rate 0.1, max_depth 1 | 0.8569 | 0.0119 | 0.8704 | 0.0135 | 0.859 | 243 | 34.6 | Measured in Main (evaluate_model), final setup. Grid-searched on ROC AUC; in this setup 100 trees ties (0.8585). |
