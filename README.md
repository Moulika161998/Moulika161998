name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: 3.x

    - name: Install dependencies
      run: |
        pip install -r requirements.txt

    - name: Run Tests
      run: |
        python -m unittest discover tests

    - name: Deploy (Optional)
      if: github.event_name == 'push'
      run: |
        # Add deployment steps here (e.g., deploying to Heroku or AWS)

