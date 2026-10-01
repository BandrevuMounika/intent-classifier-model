# Intent Classifier Model

A small machine-learning project that demonstrates how to build and serve a text intent classification model using Python and Flask.

## Project Overview

This project covers the basic ML model lifecycle:

1. Train a text classification model.
2. Save the trained model as an artifact.
3. Load the model from the Flask application.
4. Expose predictions through a REST API.
5. Send text input and receive the predicted intent with probabilities.

## Project Structure

```text
intent-classifier/
│
├── model/
│   ├── train.py
│   └── artifacts/
│       └── intent_model.pkl
│
├── app.py
├── requirements.txt
└── README.md
```

## 1. Create a Virtual Environment

Create and activate a Python virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

On Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

## 2. Install Dependencies

Install the required Python packages:

```bash
pip install -r requirements.txt
```

## 3. Train the Model

Run the training script:

```bash
python model/train.py
```

After successful training, the model artifact will be generated:

```text
model/artifacts/intent_model.pkl
```

This file contains the trained intent classification model.

## 4. Start the Flask API

Run the Flask application:

```bash
python app.py
```

The API will be available at:

```text
http://127.0.0.1:6000
```

## 5. Test the Prediction API

Send a POST request to the `/predict` endpoint:

```bash
curl -X POST http://127.0.0.1:6000/predict \
  -H "Content-Type: application/json" \
  -d '{"text":"I want to cancel my subscription"}'
```

## Example Response

```json
{
  "intent": "complaint",
  "probabilities": {
    "complaint": 0.85,
    "question": 0.05
  }
}
```

The API receives the user's text, passes it through the trained model, and returns the predicted intent along with the probability for each supported intent.

