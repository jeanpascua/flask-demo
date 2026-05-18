# flask-demo

Simple Flask app containerized with Docker. The main point of this repo is the CI pipeline, not the app itself.

Every push to main triggers a GitHub Actions workflow that runs tests, security scans, and builds the Docker image. No manual steps.

---

## What's in here

- `app.py` - a basic Flask web server that returns a string on the root route
- `Dockerfile` - builds the container with Python 3.12 and installs dependencies
- `requirements.txt` - just Flask
- `conftest.py` / `tests/` - pytest test suite
- `.github/workflows/deploy.yml` - the GitHub Actions pipeline

---

## How it works

1. Push code to main
2. GitHub Actions spins up a fresh Ubuntu runner
3. Checks out the code
4. Runs `pytest tests/`
5. Runs Snyk dependency scan (fails on HIGH+ severity)
6. Builds Docker image
7. Runs Trivy container scan (fails on HIGH/CRITICAL)

---

## Stack

Python | Flask | Docker | GitHub Actions | Snyk | Trivy
