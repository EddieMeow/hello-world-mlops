# hello-world-mlops

A minimal MLOps example: trains a `LogisticRegression` model on the Iris dataset with scikit-learn, saves it to `artifacts/`, and serves predictions from the command line or a Flask backend server.

## Setup

This project uses [uv](https://docs.astral.sh/uv/) to manage the Python version and dependencies.

```bash
uv sync
```

## Usage

Train the model (saves `artifacts/model.pkl` and `artifacts/metrics.json`):

```bash
uv run train.py
```

Run a prediction:

```bash
uv run run_model.py --input "[5.1, 3.5, 1.4, 0.2]"
```

Start the backend server (serves predictions over HTTP on port 5001; trains the model automatically if `artifacts/model.pkl` doesn't exist yet):

```bash
uv run app.py
```

Then query it:

```bash
curl http://localhost:5001/health

curl -X POST http://localhost:5001/predict \
  -H "Content-Type: application/json" \
  -d '{"features": [5.1, 3.5, 1.4, 0.2]}'
```
