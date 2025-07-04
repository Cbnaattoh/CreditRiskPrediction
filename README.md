# Credit Risk Prediction

This Streamlit application predicts credit scores based on user financial details and provides information on the factors affecting credit scores.

## Features

- **Home Page**:  
  Enter your financial details (income, debt, loan info, etc.) to get a predicted credit score and its category (Poor, Fair, Good, Very Good, Exceptional).

- **Info Page**:  
  Learn how each input factor (like income, debt-to-income ratio, employment length, etc.) impacts your credit score, with clear explanations.

- **Navigation**:  
  Use the sidebar to switch between the Home and Info pages.

## How to Run

1. **Install dependencies**  
   ```
   pip install -r requirements.txt
   ```

2. **Train the model**  
   Ensure you have run the training script (`train.py`) to generate the model and preprocessor files in `ml_model/models/`.

3. **Start the app**  
   ```
   streamlit run ml_model/scripts/app.py
   ```

4. **Open in browser**  
   Go to the URL shown in your terminal (usually http://localhost:8501).

## File Structure

- `ml_model/scripts/app.py` – Main Streamlit app
- `ml_model/scripts/utils.py` – Utility functions for preprocessing
- `ml_model/models/` – Folder for trained model, preprocessor, and metrics files

## Notes

- All monetary values are in Ghanaian Cedi (GHC).
- Make sure the model and preprocessor files exist before running the app.
- For any issues, check the error messages in the Streamlit interface.

---
```# Credit Risk Prediction

This Streamlit application predicts credit scores based on user financial details and provides information on the factors affecting credit scores.

## Features

- **Home Page**:  
  Enter your financial details (income, debt, loan info, etc.) to get a predicted credit score and its category (Poor, Fair, Good, Very Good, Exceptional).

- **Info Page**:  
  Learn how each input factor (like income, debt-to-income ratio, employment length, etc.) impacts your credit score, with clear explanations.

- **Navigation**:  
  Use the sidebar to switch between the Home and Info pages.

## How to Run

1. **Install dependencies**  
   ```
   pip install -r requirements.txt
   ```

2. **Train the model**  
   Ensure you have run the training script (`train.py`) to generate the model and preprocessor files in `ml_model/models/`.

3. **Start the app**  
   ```
   streamlit run ml_model/scripts/app.py
   ```

4. **Open in browser**  
   Go to the URL shown in your terminal (usually http://localhost:8501).

## File Structure

- `ml_model/scripts/app.py` – Main Streamlit app
- `ml_model/scripts/utils.py` – Utility functions for preprocessing
- `ml_model/models/` – Folder for trained model, preprocessor, and metrics files

## Notes

- All monetary values are in Ghanaian Cedi (GHC).
- Make sure the model and preprocessor files exist before running the app.
- For any issues, check the error messages in the Streamlit interface.
