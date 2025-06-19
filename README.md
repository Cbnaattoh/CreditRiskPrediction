# Credit Risk Prediction App - Demo

## Overview
The Credit Risk Prediction App is a Streamlit-based web application designed to predict an individual's credit score based on financial inputs, tailored for users in Ghana. It leverages an XGBoost model trained on a dataset of financial features to provide accurate credit score predictions, categorized into Poor, Fair, Good, Very Good, or Exceptional. The app includes input validation, an information section explaining how inputs affect the credit score, and color-coded outputs (red for scores < 580, yellow for 580–739, green for ≥ 740). All monetary values are in Ghanaian Cedi (GHC).

## Features
- **Credit Score Prediction**: Enter financial details to receive a predicted credit score (300–850), category, and confidence level.
- **Input Validation**: Ensures valid inputs with specific ranges (e.g., Annual Income: 5,000–10,000,000 GHC).
- **Information Section**: Explains how each input (e.g., Annual Income, Debt-to-Income Ratio) positively or negatively impacts the credit score.
- **Color-Coded Outputs**:
  - Red background for scores < 580 (Poor).
  - Yellow background for scores 580–739 (Fair or Good).
  - Green background for scores ≥ 740 (Very Good or Exceptional).
- **Ghanaian Context**: Monetary inputs and outputs are in GHC, with ranges suited for Ghanaian financial profiles.
- **Confidence Level**: Displays the model's R-squared score as a percentage to indicate prediction reliability.

## Project Structure
```
CreditRiskPrediction/
├── ml_model/
│   ├── data/
│   │   ├── raw/
│   │   │   └── dataset.csv
│   ├── models/
│   │   ├── xgboost_credit_score_model.pkl
│   │   ├── preprocessor.pkl
│   │   └── model_metrics.pkl
│   ├── scripts/
│   │   ├── app.py
│   │   ├── preprocess.py
│   │   ├── train.py
│   │   ├── predict.py
│   │   └── utils.py
├── venv/
├── README.md
└── requirements.txt 
```

- **data/raw/dataset.csv**: The dataset used for training.
- **models/**: Contains the trained XGBoost model, preprocessor, and metrics.
- **scripts/**:
  - `app.py`: The Streamlit app.
  - `preprocess.py`: Preprocesses the dataset.
  - `train.py`: Trains the XGBoost model.
  - `predict.py`: Handles predictions (used by `app.py`).
  - `utils.py`: Utility functions for preprocessing and feature handling.

## Prerequisites
- Python 3.8 or higher
- Virtual environment (recommended)
- Git 

## Setup Instructions
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Cbnaattoh/CreditRiskPrediction
   cd CreditRiskPrediction
   ```

2. **Create and Activate a Virtual Environment**:
   ```bash
   python -m venv venv
   .\venv\Scripts\activate  # Windows
   # source venv/bin/activate  # macOS/Linux
   ```

3. **Install Dependencies**:
   Create a `requirements.txt` file with the following:
   ```
   joblib
   pandas
   scikit-learn
   xgboost
   numpy
   streamlit
   ```
   Then install:
   ```bash
   pip install -r requirements.txt
   ```

4. **Prepare the Model**:
   - Ensure `dataset.csv` is in `ml_model/data/raw/`.
   - Run preprocessing and training scripts:
     ```bash
     python ml_model/scripts/preprocess.py
     python ml_model/scripts/train.py
     ```
   - This generates `xgboost_credit_score_model.pkl`, `preprocessor.pkl`, and `model_metrics.pkl` in `ml_model/models/`.

5. **Run the App**:
   ```bash
   streamlit run ml_model/scripts/app.py
   ```
   - The app will open in your default browser (typically `http://localhost:8501`).

## Usage
1. **Open the App**:
   - After running the command above, access the app in your browser.

2. **View the Information Section**:
   - Expand the "How Inputs Affect Your Credit Score" section to understand the impact of each input (e.g., higher Annual Income improves your score).

3. **Enter Financial Details**:
   - Fill out the form with details such as:
     - Annual Income (GHC): 5,000–10,000,000
     - Debt-to-Income Ratio (%): 0–100
     - Employment Length: e.g., "5 years", "10+ years", "< 1 year"
     - Home Ownership: MORTGAGE, RENT, OWN, NONE, OTHER
   - Example inputs:
     ```
     Annual Income (GHC): 500000
     Debt-to-Income Ratio (%): 20
     Interest Rate (%): 10
     Revolving Utilization Rate (%): 30
     Number of Delinquencies in Past 2 Years: 0
     Number of Inquiries in Last 6 Months: 1
     Employment Length: 5 years
     Number of Open Accounts: 10
     Collections in Past 12 Months (excluding medical): 0
     Loan Amount (GHC): 100000
     Credit History Length (years): 10
     Maximum Balance on Bankcards (GHC): 50000
     Total Number of Accounts: 15
     Number of Revolving Accounts Opened in Last 12 Months: 2
     Number of Public Records: 0
     Home Ownership: RENT
     ```

4. **Submit and View Results**:
   - Click "Predict Credit Score".
   - If inputs are valid, see the predicted score, category, and confidence level with:
     - Red background for scores < 580 (Poor).
     - Yellow background for scores 580–739 (Fair or Good).
     - Green background for scores ≥ 740 (Very Good or Exceptional).
   - If inputs are invalid (e.g., Annual Income < 5,000 GHC), error messages will appear.

## Example Outputs
- **High Score (e.g., 750)**:
  ```
  Prediction Results
  [Green background]
  Predicted Credit Score: 750
  Credit Score Category: Very Good
  Confidence Level: <value>.00%
  ```
- **Moderate Score (e.g., 600)**:
  ```
  Prediction Results
  [Yellow background]
  Predicted Credit Score: 600
  Credit Score Category: Fair
  Confidence Level: <value>.00%
  ```
- **Low Score (e.g., 500)**:
  ```
  Prediction Results
  [Red background]
  Predicted Credit Score: 500
  Credit Score Category: Poor
  Confidence Level: <value>.00%
  ```


## Troubleshooting
- **Model Files Missing**:
  - Rerun `preprocess.py` and `train.py` to generate `xgboost_credit_score_model.pkl`, `preprocessor.pkl`, and `model_metrics.pkl`.
- **Invalid Inputs**:
  - Check error messages for guidance (e.g., "Annual Income must be between 5,000 and 10,000,000 GHC").
- **Score Shows "Invalid Score"**:
  - Ensure inputs produce scores within 300–850. If not, verify the model’s training data range.
  - If a score like 739 shows "Invalid Score", ensure `app.py` uses the latest version with rounded scores in `get_credit_score_category`.

- **Streamlit Issues**:
  - Update Streamlit: `pip install --upgrade streamlit`.
  - Check the console for errors and share them for support.

## Contributing
- To contribute, fork the repository, create a branch, and submit a pull request.
- Report issues or suggest features via GitHub Issues.

## License
This project is licensed under the MIT License (see `LICENSE` file, if included).

## Acknowledgments
- Built with [Streamlit](https://streamlit.io/), [XGBoost](https://xgboost.readthedocs.io/), and [scikit-learn](https://scikit-learn.org/).
- Designed for financial inclusion in Ghana, supporting credit access for diverse economic profiles.

