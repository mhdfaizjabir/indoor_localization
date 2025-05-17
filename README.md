#  Indoor Localization using Wi-Fi Fingerprinting

Dataset - https://archive.ics.uci.edu/dataset/422/wireless+indoor+localization

This project solves the problem of **indoor localization** by predicting both:
- **Coordinates** (longitude & latitude) using regression
- **Building and floor** using classification

It uses **Wi-Fi signal strengths** from over 500 Access Points and applies various machine learning models, including **KNN**, **Neural Networks**, **Decision Trees**, and **CNNs**, along with **PCA** for dimensionality reduction.

---

##  Objectives

- Predict indoor **coordinates** via regression
- Predict **building** and **floor level** via classification
- Apply **PCA** for dimensionality reduction (520 ➝ 267 features)
- Evaluate and tune KNN, Decision Tree, and CNN models

---


## Regression Results: KNN for Coordinate Prediction

| Target     | RMSE (Initial) | RMSE (PCA) | RMSE (Tuned) | MAE (Initial) | MAE (PCA) | MAE (Tuned) |
|------------|----------------|------------|--------------|----------------|-----------|-------------|
| Longitude  | 17.41          | 15.85      | **15.13**    | 8.03           | 7.49      | 7.70        |
| Latitude   | 15.13          | 14.72      | **14.72**    | 7.69           | 7.59      | 7.59        |

-  PCA reduced features by ~48.7% (520 ➝ 267)
-  Longitude prediction improved by **13.1%** after preprocessing and tuning
-  Optimal `k`: 13 for longitude, 5 for latitude
-  Cross-validated average RMSE: ~13.74 ± 8.01

---

## 🤖 Model Comparison: Regression

| Model         | Longitude RMSE | Longitude MAE | Latitude RMSE | Latitude MAE |
|---------------|----------------|---------------|----------------|--------------|
| KNN Initial   | 17.41          | 8.03          | 15.13          | 7.69         |
| KNN + PCA     | 15.85          | 7.49          | 14.72          | 7.59         |
| KNN Tuned     | **15.13**      | **7.70**      | **14.72**      | **7.59**     |
| Neural Net    | 22.80          | 12.06         | 17.82          | 8.70         |

-  KNN consistently outperformed Neural Networks
-  PCA preprocessing improved both accuracy and training speed
-  Average Euclidean prediction error: ~21 units = **room-level accuracy**

---

##  Classification: Building & Floor Prediction

###  Decision Tree Results

| Target   | Accuracy (Initial) | Accuracy (Tuned) | Validation Accuracy |
|----------|--------------------|------------------|----------------------|
| Building | ~92%               | ~94.3%           | ~93.6%               |
| Floor    | ~85%               | ~87.1%           | ~85.5%               |

-  PCA improved generalization and reduced overfitting
-  Good baseline, but limited in modeling spatial complexity

---

### CNN Results (Convolutional Neural Network)

| Target   | Accuracy (Initial) | Accuracy (Tuned) | Validation Accuracy |
|----------|--------------------|------------------|----------------------|
| Building | ~99.82%            | ~99.85%          | ~99.85%              |
| Floor    | ~98.4%             | ~99.15%          | ~98.9%               |

-  High accuracy for both targets
-  CNN outperformed Decision Tree on **floor prediction**
-  Especially effective in capturing complex spatial patterns

---

##  Tools & Technologies

- Python, NumPy, Pandas, Matplotlib, Seaborn
- Scikit-learn, TensorFlow / Keras
- PCA, KNN, Decision Trees, CNN
- GridSearchCV for hyperparameter tuning

---

##  Key Takeaways

- PCA improved model efficiency and accuracy
- KNN was best for regression (coordinates); CNN was best for classification
- Achieved **room-level localization accuracy** using Wi-Fi signal fingerprints

---


