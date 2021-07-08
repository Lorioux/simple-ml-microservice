[![CircleCI](https://circleci.com/gh/Lorioux/simple-ml-microservice/tree/main.svg?style=svg)](https://circleci.com/gh/Lorioux/simple-ml-microservice/tree/main)

## Project Overview

In this project, we operationalize a Machine Learning Microservice API.

There is given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

The goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:

* Test project code using linting
* Complete a Dockerfile to containerize this application
* Deploy containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that code has been tested

**The final implementation of the project will showcase how to operationalize production microservices.**

---

## Setup the Environment

* Create a virtualenv and activate it
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl

### Kubernetes Test Steps

When kubernetes is ready and running, and localhost ports are forwarded to kubernetes POD´s ports.

1. Run `bash make_prediction.sh` to test prediction in the POD's Containers.
2. Run `$ kubectl logs pods` to get POD's log

**Results should be like this:**

Found 3 pods, using pod/micro-ml-dps-78df5cb9c7-shz2m

* Serving Flask app "app" (lazy loading)
* Environment: development
* Debug mode: on
* Running on http://0.0.0.0:80/ (Press CTRL+C to quit)
* Restarting with stat
* Debugger is active!
* Debugger PIN: 278-013-256
  [2021-07-08 16:32:35,356] INFO in app: JSON payload:
  {'CHAS': {'0': 0}, 'RM': {'0': 6.575}, 'TAX': {'0': 296.0}, 'PTRATIO': {'0': 15.3}, 'B': {'0': 396.9}, 'LSTAT': {'0': 4.98}}
  [2021-07-08 16:32:35,363] INFO in app: Inference payload DataFrame:
  CHAS     RM    TAX  PTRATIO      B  LSTAT
  0     0  6.575  296.0     15.3  396.9   4.98
  [2021-07-08 16:32:35,368] INFO in app: Scaling Payload:
  CHAS     RM    TAX  PTRATIO      B  LSTAT
  0     0  6.575  296.0     15.3  396.9   4.98
  [2021-07-08 16:32:35,370] INFO in app: Predicted value: \[20.35373177134412]
  127.0.0.1 - - [08/Jul/2021 16:32:35] "POST /predict HTTP/1.1" 200 -
