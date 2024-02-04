### Disaster Response Pipeline Project

## Table of Contents
- [Table of Contents](#table-of-contents)
  - [Project Overview](#project-overview)
  - [File Descriptions](#file-descriptions)
    - [app](#app)
    - [data](#data)
    - [models](#models)
  - [Project Components](#project-components)
    - [1. ETL Pipeline](#1-etl-pipeline)
    - [2. ML Pipeline](#2-ml-pipeline)
    - [3. Flask Web App](#3-flask-web-app)
  - [How to Use the Project](#how-to-use-the-project)
  - [Acknowledgments](#acknowledgments)

### Project Overview
In this project, I applied my data engineering and machine learning skills to analyze disaster data provided by [Figure Eight](https://appen.com/). The goal was to build a model and deploy it as an API that classifies disaster-related messages. This classification helps route messages to appropriate disaster relief agencies. Additionally, a web app was developed to allow emergency workers to input messages and receive real-time classification results, along with data visualizations.

### File Descriptions
The project consists of the following files and directories:

#### app
- `template`: Contains HTML templates for the web app.
  - `master.html`: The main page of the web app.
  - `go.html`: The page displaying classification results.
- `run.py`: A Flask file that runs the web app.

#### data
- `disaster_categories.csv`: Data containing message categories.
- `disaster_messages.csv`: Data containing disaster-related messages.
- `process_data.py`: A Python script for data cleaning and ETL pipeline.

#### models
- `train_classifier.py`: A Python script for building and training the classification model.

### Project Components
The project consists of three main components:

#### 1. ETL Pipeline
The `process_data.py` script performs the following tasks:
- Loads the messages and categories datasets.
- Merges the two datasets based on a common identifier.
- Cleans and preprocesses the data.
- Stores the cleaned data in an SQLite database.

#### 2. ML Pipeline
The `train_classifier.py` script builds and trains a machine learning model:
- Loads data from the SQLite database.
- Splits the dataset into training and test sets.
- Creates a text processing and machine learning pipeline.
- Trains and optimizes the model using GridSearchCV.
- Evaluates the model's performance on the test set.
- Exports the final model as a pickle file.

#### 3. Flask Web App
The project includes a web app that allows emergency workers to:
- Input a new message.
- Receive classification results in multiple categories.
- Visualize data through interactive plots.

### How to Use the Project
To set up and run the project, follow these steps:

1. Run the ETL pipeline to clean and store data in the SQLite database:
    ```bash
    python data/process_data.py data/disaster_messages.csv data/disaster_categories.csv data/DisasterResponse.db
    ```

2. Train the classifier and save the model:
    ```bash
    python models/train_classifier.py data/DisasterResponse.db models/classifier.pkl
    ```

3. Run the web app:
    ```bash
    python app/run.py
    ```

4. Access the web app by visiting http://0.0.0.0:3000/ in your web browser.

### Acknowledgments
I would like to express my gratitude to Udacity for providing the initial project structure and guidance throughout this project.
