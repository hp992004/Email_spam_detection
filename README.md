# Spam Detection Model Report

## 1. Data Preparation:
- **Dataset Used:** SMS Spam Collection Dataset from Kaggle.
- **Loading Data:** The dataset was loaded using `pd.read_csv` from the provided CSV file.
- **Feature and Label Separation:** Features (`X`) include email text, and labels (`y`) represent spam or not spam.

## 2. Text Tokenization:
- **Tokenizer Object Creation:** A `Tokenizer` object was created from `tensorflow.keras.preprocessing.text` to convert text into sequences of integers.
- **Text to Sequences Conversion:** The `fit_on_texts` method was used to fit the tokenizer on training data, and `texts_to_sequences` converted text to integer sequences.
- **Padding Sequences:** Sequences were padded to have equal lengths using `pad_sequences`.

## 3. Model Creation:
- **Model Function:** A function `create_model` was defined to create a sequential model with embedding, global average pooling, and dense layers.
- **Compilation:** The model was compiled with binary crossentropy loss and specified optimizer.

## 4. Hyperparameter Tuning:
- **GridSearchCV:** `GridSearchCV` from `sklearn.model_selection` was used to perform hyperparameter tuning.
- **Parameters Tested:**
  - `units`: [32, 64, 128]
- **Batch Sizes Tested:**
  - [16, 32, 64]
- **Loop Iteration:** For each batch size, a new `KerasClassifier` instance was created, and grid search was performed.

## 5. Model Training:
- **Model Fitting:** The model was fit to the training data using `fit` with early stopping callback to monitor loss.
- **Evaluation:** Model performance was evaluated on the test data, and loss and accuracy were printed.

## 6. Model Evaluation:
- **Confusion Matrix:** Confusion matrix was calculated using `sklearn.metrics.confusion_matrix`.
- **Classification Report:** A detailed classification report was generated using `sklearn.metrics.classification_report`.
- **Performance Metrics:** Loss, accuracy, confusion matrix, true positives (TP), true negatives (TN), false positives (FP), false negatives (FN) were analyzed.

## 7. Recommendations and Conclusion:
- **Tokenizer Placement:** The `Tokenizer` object should be created before defining the model.
- **Hyperparameter Tuning Issue:** The model instance should be created inside the hyperparameter tuning loop to ensure separate models for different hyperparameters.
- **Model Coefficients Analysis:** It would be beneficial to analyze the model coefficients to understand the importance of different features.

## 8. Further Steps:
- **Visualization:** Consider visualizing training/validation loss and accuracy over epochs to understand model training dynamics.
- **Feature Importance:** Analyze feature importance or coefficients to identify key factors in spam detection.
