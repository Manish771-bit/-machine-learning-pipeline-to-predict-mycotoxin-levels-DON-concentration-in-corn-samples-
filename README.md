# -machine-learning-pipeline-to-predict-mycotoxin-levels-DON-concentration-in-corn-samples-
FastAPI-based Machine Learning API

This repository contains a FastAPI-based web service that serves a machine learning model for predictions. The API loads a pre-trained model and a scaler, accepts input features via a POST request, and returns predictions.

📂 Repository Structure
📦 project_root
├── 📄 api_server.py         # FastAPI server script
├── 📄 model_training_eval.py # Model training and evaluation script
├── 📦 models                # Directory for storing trained models
│   ├── rf_model.pkl         # Saved Random Forest model
│   ├── scaler.pkl           # Saved data scaler
├── 📄 requirements.txt      # Required dependencies
├── 📄 README.md             # Project documentation
🚀 Setup Instructions

1️⃣ Install Dependencies

First, install the required dependencies using:
pip install -r requirements.txt
For Google Colab users, also install  ngrok for public API exposure:
pip install pyngrok
2️⃣ Train the Model (Optional)

If the trained model is not available, run:
python model_training_eval.py
3️⃣ Start the API Server

Run the FastAPI server:
python api_server.py
This will start the API at http://0.0.0.0:8000.

4️⃣ Expose API to Public (Colab Users)

If using Google Colab, run:
from pyngrok import ngrok
public_url = ngrok.connect(8000)
print(f"Public URL: {public_url.public_url}")

5️⃣ Test API

Use the following Python script to send a test request:
import requests

url = "https://your-public-url.ngrok-free.app/predict"  # Replace with actual ngrok URL
data = {"features": [0.5, -1.2, 3.4, 2.1]}

response = requests.post(url, json=data)
print("Status Code:", response.status_code)
print("Response:", response.json())
🛠️ Dependencies

fastapi
uvicorn
joblib
numpy
scikit-learn
pyngrok

📌 Notes

Ensure rf_model.pkl and scaler.pkl exist before running the server.

Restart Colab runtime if API fails to respond.

Keep the server running before sending request.

Happy Coding! 🚀
