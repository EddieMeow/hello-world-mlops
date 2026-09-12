# hello-world-mlops

A minimal MLOps example: trains a `LogisticRegression` model on the Iris dataset with scikit-learn, saves it to `artifacts/`, and serves predictions from the command line.

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
