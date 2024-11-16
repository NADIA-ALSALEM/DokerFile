# Random Forest Salary Prediction API with FastAPI

This repository contains a FastAPI-based API service for salary prediction using a machine learning model built with **Random Forest Regression**. The model is trained to predict the salary of individuals based on their position level.

## Features
- **Machine Learning Model**: A **RandomForestRegressor** from **scikit-learn** is used to predict the salary based on position levels.
- **Model Persistence**: The trained model is saved and loaded using **joblib** to avoid retraining the model each time the API starts.
- **Prediction Endpoint**: A POST endpoint (`/predict/`) accepts a JSON request with user ID and features, and returns the predicted salary.
- **API Documentation**: The API comes with an interactive Swagger UI for easy testing and exploration.
- **Background Tasks**: The API can run background tasks to monitor data drift or perform additional operations.


## Setup
1. Clone this repository to your local machine.
2. Install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```
3. Train and save the model (if not already available) by running the script once. The model will be saved as `random_forest_model.pkl`.
4. Run the FastAPI app:
   ```bash
   uvicorn random_forest_regression:app --host 0.0.0.0 --port 8000
   ```
5. The app will be running at `http://localhost:8000`. You can use the Swagger UI at `http://localhost:8000/docs` to test the prediction endpoint.

## API Endpoints
- **GET /**: A simple welcome message.
- **POST /predict/**: Accepts user input as a JSON object, predicts the salary, and returns the result.

### Example Request:
```json
{
  "user_id": "123",
  "features": {
    "level": 6.5
  }
}
```

### Example Response:
```json
{
  "predicted_salary": 150000.0
}
```

## Monitoring and Logging
The API is equipped with basic logging to track prediction requests and potential errors. The model's input features are logged for monitoring, and background tasks can be added for further operations like data drift detection (though it’s not implemented in this version).
