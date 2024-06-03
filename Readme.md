# Customer Purchase Prediction Model

This project aims to predict whether an online shopper will make a purchase based on their browsing behavior and other related parameters. The model is built using historical data of customer behavior from an e-commerce platform.

## Dataset

The dataset used for this project is the [Online Shoppers Intention](https://www.kaggle.com/datasets/henrysue/online-shoppers-intention) dataset, which contains various features about the user's browsing session, such as duration spent on different types of pages, bounce rates, and whether the visit occurred on a weekend.

## Features

The following features were used to build the prediction model:

- `Administrative_Duration`
- `Informational_Duration`
- `ProductRelated_Duration`
- `BounceRates`
- `ExitRates`
- `PageValues`
- `SpecialDay`
- `Month`
- `OperatingSystems`
- `Browser`
- `Region`
- `TrafficType`
- `VisitorType`
- `Weekend`
- `Revenue` (Target variable: whether a user will buy an item or not)

## Models Used

Two machine learning models were employed to predict the purchasing intention:

1. **Random Forest Classifier**
    - **Parameters**: `n_estimators=1000`, `random_state=1`
    - **Performance**:
        - **Accuracy**: 0.9259
        - **Precision, Recall, F1-Score**:
            ```
                        precision    recall  f1-score   support

                    0       0.95      0.90      0.92      2050
                    1       0.90      0.95      0.93      2050

            accuracy                           0.93      4100
            macro avg       0.93      0.93      0.93      4100
            weighted avg    0.93      0.93      0.93      4100
            ```

2. **Extra Trees Classifier**
    - **Parameters**: `n_estimators=100`, `random_state=42`
    - **Performance**:
        - **Accuracy**: 0.9395
        - **Precision, Recall, F1-Score**:
            ```
                        precision    recall  f1-score   support

                    0       0.96      0.91      0.94      2050
                    1       0.92      0.96      0.94      2050

            accuracy                            0.94      4100
            macro avg       0.94      0.94      0.94      4100
            weighted avg    0.94      0.94      0.94      4100
            ```

## Predictions

The models were tested on manual input data to predict whether a user will buy an item or not:

1. **Example 1:**
    ```python
    user_input = {
        'Administrative_Duration': 50,
        'Informational_Duration': 100,
        'ProductRelated_Duration': 200,
        'BounceRates': 0.05,
        'ExitRates': 0.1,
        'PageValues': 20,
        'SpecialDay': 0,
        'Month': 7,
        'OperatingSystems': 0,
        'Browser': 0,
        'Region': 0,
        'TrafficType': 1,
        'VisitorType': 'New_Visitor',
        'Weekend': 1
    }
    ```

    - **Prediction**:
        - **Extra Trees Classifier**: will buy
        - **Random Forest Classifier**: will NOT buy

2. **Example 2:**
    ```python
    user_input = {
        'Administrative_Duration': 1000000,
        'Informational_Duration': 1000000,
        'ProductRelated_Duration': 1000000,
        'BounceRates': 5.05,
        'ExitRates': 10.1,
        'PageValues': 2,
        'SpecialDay': 0,
        'Month': 1,
        'OperatingSystems': 0,
        'Browser': 1,
        'Region': 45,
        'TrafficType': 1,
        'VisitorType': 'Returning_Visitor',
        'Weekend': 1
    }
    ```

    - **Prediction**:
        - **Extra Trees Classifier**: will NOT buy
        - **Random Forest Classifier**: will NOT buy

## Conclusion

Both models, the Random Forest Classifier and the Extra Trees Classifier, demonstrated high accuracy in predicting whether a customer will make a purchase. The Extra Trees Classifier showed slightly better performance. These models can be used to help e-commerce platforms better understand and predict customer behavior, thereby enhancing targeted marketing strategies and improving overall sales.

## How to Use

1. **Download dataset**:
    Download the [Dataset](https://www.kaggle.com/datasets/henrysue/online-shoppers-intention) and extract its contents into the `working directory`

1. **Setup virtual environment**:
    ```bash
    python -m venv venv
    source venv/bin/activate
    ```

2. **Install the dependancies**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Run the notebook**:
    run the `Shopper purchase prediction analysis.ipynb` notebook cells.


