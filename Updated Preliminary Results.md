# Preliminary Results

Note: Model owners please use the shared setup provided in main

| Model | Settings | Val ROC AUC | ± std | Train ROC AUC | Gap | Recall (default threshold) | Fit time (ms) | Score time (ms, predict + metrics, per fold) | Status |
|---|---|---|---|---|---|---|---|---|---|
| Majority baseline | DummyClassifier (prior) | 0.5 | 0 | 0.5 | 0 | 0 | 35.4 | 43.7 | Measured in Main (evaluate_model), same Colab run |
| Logistic regression (reference) | bmi missing flag, class_weight balanced, C = 0.01 | 0.8592 | 0.0169 | 0.8675 | 0.0083 | 0.819 | 84.0 | 41.3 | Measured in Main (evaluate_model), same Colab run |
| Linear SVM | LinearSVC (hinge, C = 0.01, class weight 1:10), sigmoid-calibrated, threshold 0.05 | 0.8562 | 0.0159 | 0.8657 | 0.0094 | 0.804 (at threshold 0.05) | 150.3 | 72.1 | Measured in Main (evaluate_model), same Colab run |
| Random forest | 200 trees, max_features 10, min_samples_leaf 20, class_weight balanced | 0.8508 | 0.0095 | 0.9480 | 0.0972 | 0.6635 | 1387.6 | 187.4 | Measured in Main (evaluate_model), same Colab run |
| Gradient boosting | balanced sample weights, 50 trees, learning rate 0.1, max_depth 1 | 0.8569 | 0.0119 | 0.8704 | 0.0135 | 0.859 | 243.3 | 34.6 | Measured in Main (evaluate_model), same Colab run. Grid-searched on ROC AUC; 100 trees ties (0.8585). |

Timed on: Google Colab | AMD EPYC 7B12 (2 cores, 12.7 GB) | CPU only | Python 3.13.18
