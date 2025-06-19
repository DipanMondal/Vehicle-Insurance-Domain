# Vehicle-Insurance-Domain

## Intro
This project, "Vehicle-Insurance-Domain," is an MLOps (Machine Learning Operations) project focused on predicting vehicle insurance responses. It sets up an end-to-end machine learning pipeline, from data ingestion to model deployment, using a modular and robust architecture.

### Project Overview

The project aims to build and deploy a machine learning model that predicts whether a customer is interested in vehicle insurance. It incorporates:

* **Data Ingestion:** Fetching data from a MongoDB database.
* **Data Validation:** Ensuring data quality and consistency using a schema.
* **Data Transformation:** Preprocessing data, handling categorical features, and scaling numerical features. It also addresses class imbalance using SMOTEENN.
* **Model Training:** Training a RandomForestClassifier model and optimizing its hyperparameters.
* **Model Evaluation:** Comparing the trained model's performance with a production model (if available) to determine if it should be pushed to production.
* **Model Pusher:** Deploying the accepted model to Google Drive for cloud storage.
* **Prediction Pipeline & Web Interface:** Providing a FastAPI-based web application for real-time predictions.

### Setup and Installation

1.  **Clone the Repository:**
    ```bash
    git clone <repository_url>
    cd Vehicle-Insurance-Domain
    ```
2.  **Create a Virtual Environment:**
    ```bash
    python -m venv venv
    ```
3.  **Activate the Virtual Environment:**
    * Windows: `venv\Scripts\activate`
    * macOS/Linux: `source venv/bin/activate`
4.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
5.  **MongoDB Setup:**
    * Sign up for [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
    * Create a new project and a free cluster (M0 service).
    * Set up a database user with a username and password.
    * Configure "Network Access" to allow connections from `0.0.0.0/0` (for development purposes; restrict in production).
    * Obtain your MongoDB connection string (replace `<username>` and `<db_password>` with your credentials).
    * Create a `.env` file in the root directory of the project and set the following environment variables:
        ```
        MONGO_USER=<your_mongodb_username>
        MONGO_PASSWORD=<your_mongodb_password>
        MONGO_URI=<your_mongodb_connection_string>
        ```
    * You can push the initial dataset to MongoDB using the `MongoDB_testing.ipynb` notebook located in the `notebook` folder.

6.  **Google Drive Setup (for Model Pusher):**
    * Create a Google Cloud Platform project.
    * Enable the Google Drive API.
    * Create a service account and generate a JSON key file.
    * Save this JSON key file as `cred/key.json` in your project's root directory.
    * Create a specific folder in your Google Drive for model storage.
    * Copy the ID of this Google Drive folder and update `GOOGLE_FOLDER_ID` in `src/constants/__init__.py`.

### How to Run

#### 1. Train the Model

To run the entire training pipeline (data ingestion, validation, transformation, model training, evaluation, and pushing to cloud):

```bash
python demo.py
```
This project, "Vehicle-Insurance-Domain," is an MLOps (Machine Learning Operations) project focused on predicting vehicle insurance responses. It sets up an end-to-end machine learning pipeline, from data ingestion to model deployment, using a modular and robust architecture.

Project Overview
The project aims to build and deploy a machine learning model that predicts whether a customer is interested in vehicle insurance. It incorporates:

Data Ingestion: Fetching data from a MongoDB database.
Data Validation: Ensuring data quality and consistency using a schema.
Data Transformation: Preprocessing data, handling categorical features, and scaling numerical features. It also addresses class imbalance using SMOTEENN.
Model Training: Training a RandomForestClassifier model and optimizing its hyperparameters.
Model Evaluation: Comparing the trained model's performance with a production model (if available) to determine if it should be pushed to production.
Model Pusher: Deploying the accepted model to Google Drive for cloud storage.
Prediction Pipeline & Web Interface: Providing a FastAPI-based web application for real-time predictions.
Setup and Installation
Clone the Repository:

Bash

git clone <repository_url>
cd Vehicle-Insurance-Domain
Create a Virtual Environment:

Bash

python -m venv venv
Activate the Virtual Environment:

Windows: venv\Scripts\activate
macOS/Linux: source venv/bin/activate
Install Dependencies:

Bash

pip install -r requirements.txt
MongoDB Setup:

Sign up for MongoDB Atlas.
Create a new project and a free cluster (M0 service).
Set up a database user with a username and password.
Configure "Network Access" to allow connections from 0.0.0.0/0 (for development purposes; restrict in production).
Obtain your MongoDB connection string (replace <username> and <db_password> with your credentials).
Create a .env file in the root directory of the project and set the following environment variables:
MONGO_USER=<your_mongodb_username>
MONGO_PASSWORD=<your_mongodb_password>
MONGO_URI=<your_mongodb_connection_string>
You can push the initial dataset to MongoDB using the MongoDB_testing.ipynb notebook located in the notebook folder.
Google Drive Setup (for Model Pusher):

Create a Google Cloud Platform project.
Enable the Google Drive API.
Create a service account and generate a JSON key file.
Save this JSON key file as cred/key.json in your project's root directory.
Create a specific folder in your Google Drive for model storage.
Copy the ID of this Google Drive folder and update GOOGLE_FOLDER_ID in src/constants/__init__.py.
How to Run
1. Train the Model
To run the entire training pipeline (data ingestion, validation, transformation, model training, evaluation, and pushing to cloud):

Bash

python demo.py
Alternatively, you can trigger the training via the web interface by navigating to /train after starting the FastAPI app.

2. Run the Web Application
To start the FastAPI application for predictions:

Bash

uvicorn app:app --host 0.0.0.0 --port 5000
Once the server is running, open your web browser and go to http://0.0.0.0:5000 (or the configured APP_HOST and APP_PORT). You will see a form to input vehicle data and get a prediction.

Project Structure (Brief)
The project follows a standard MLOps lifecycle, with components organized for clarity and modularity:

src/: Contains the core source code.
components/: Individual stages of the ML pipeline (data ingestion, transformation, model trainer, etc.).
configuration/: MongoDB connection setup.
cloud_storage/: Google Drive integration for model storage.
data_access/: Handlers for fetching data from MongoDB.
constants/: Centralized configuration variables.
entity/: Data class definitions for configurations and artifacts.
exception/: Custom exception handling.
logger/: Logging configuration.
pipeline/: Orchestrates the training and prediction workflows.
utils/: Utility functions (reading YAML, saving/loading objects).
notebook/: Jupyter notebooks for EDA, testing MongoDB, etc.
config/: YAML files for schema and model configurations.
templates/: HTML templates for the web interface.
static/: Static files (CSS).
app.py: FastAPI application entry point.
demo.py: Script to run the training pipeline.
requirements.txt: Project dependencies.
setup.py, pyproject.toml: Python package metadata.
.env: Environment variables (not committed to Git).
Raw README.md Code
Markdown

# Vehicle-Insurance-Domain

## Intro
This project, "Vehicle-Insurance-Domain," is an MLOps (Machine Learning Operations) project focused on predicting vehicle insurance responses. It sets up an end-to-end machine learning pipeline, from data ingestion to model deployment, using a modular and robust architecture.

### Project Overview

The project aims to build and deploy a machine learning model that predicts whether a customer is interested in vehicle insurance. It incorporates:

* **Data Ingestion:** Fetching data from a MongoDB database.
* **Data Validation:** Ensuring data quality and consistency using a schema.
* **Data Transformation:** Preprocessing data, handling categorical features, and scaling numerical features. It also addresses class imbalance using SMOTEENN.
* **Model Training:** Training a RandomForestClassifier model and optimizing its hyperparameters.
* **Model Evaluation:** Comparing the trained model's performance with a production model (if available) to determine if it should be pushed to production.
* **Model Pusher:** Deploying the accepted model to Google Drive for cloud storage.
* **Prediction Pipeline & Web Interface:** Providing a FastAPI-based web application for real-time predictions.

### Setup and Installation

1.  **Clone the Repository:**
    ```bash
    git clone <repository_url>
    cd Vehicle-Insurance-Domain
    ```
2.  **Create a Virtual Environment:**
    ```bash
    python -m venv venv
    ```
3.  **Activate the Virtual Environment:**
    * Windows: `venv\Scripts\activate`
    * macOS/Linux: `source venv/bin/activate`
4.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
5.  **MongoDB Setup:**
    * Sign up for [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
    * Create a new project and a free cluster (M0 service).
    * Set up a database user with a username and password.
    * Configure "Network Access" to allow connections from `0.0.0.0/0` (for development purposes; restrict in production).
    * Obtain your MongoDB connection string (replace `<username>` and `<db_password>` with your credentials).
    * Create a `.env` file in the root directory of the project and set the following environment variables:
        ```
        MONGO_USER=<your_mongodb_username>
        MONGO_PASSWORD=<your_mongodb_password>
        MONGO_URI=<your_mongodb_connection_string>
        ```
    * You can push the initial dataset to MongoDB using the `MongoDB_testing.ipynb` notebook located in the `notebook` folder.

6.  **Google Drive Setup (for Model Pusher):**
    * Create a Google Cloud Platform project.
    * Enable the Google Drive API.
    * Create a service account and generate a JSON key file.
    * Save this JSON key file as `cred/key.json` in your project's root directory.
    * Create a specific folder in your Google Drive for model storage.
    * Copy the ID of this Google Drive folder and update `GOOGLE_FOLDER_ID` in `src/constants/__init__.py`.

### How to Run

#### 1. Train the Model

To run the entire training pipeline (data ingestion, validation, transformation, model training, evaluation, and pushing to cloud):

```bash
python demo.py
```

Alternatively, you can trigger the training via the web interface by navigating to /train after starting the FastAPI app.

2. Run the Web Application
To start the FastAPI application for predictions:

```bash
uvicorn app:app --host 0.0.0.0 --port 5000
```
Once the server is running, open your web browser and go to `http://0.0.0.0:5000` (or the configured APP_HOST and APP_PORT). You will see a form to input vehicle data and get a prediction.
