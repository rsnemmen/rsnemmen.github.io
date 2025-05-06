---
layout: page
title: Deployment with FastAPI, Docker
description: Serve and containerize ML models, ready for the cloud (GCP, AWS)
img: assets/img/forecasting-cover.jpg
importance: 1
category: work
---


<div class="alert alert-info"><h4>Executive Summary</h4><p>
The ability to operationalize a machine-learning model is just as important as the
model itself. In this mini-project I demonstrate how a trained XGBoost classifier
(taken from my <a href="https://rsnemmen.github.io/projects/1_churn/">Customer Churn</a> case study) can be
(1) wrapped behind a FastAPI service and (2) containerized with Docker, ready to be shipped to Google Cloud.
</p></div>


> “A model that never leaves the notebook never creates value.”

---


## Architecture Overview

- *FastAPI* provides the `/predict` endpoint and auto-generated docs
- *Docker* ensures identical runtime environments  
- *Cloud Run* offers zero-ops serverless hosting on Google Cloud


## Repositories

#### 1. Building the FastAPI micro-service

[This repository](https://github.com/rsnemmen/fastapi-model) contains all code and instructions on how to serve the API locally. It serves a pre-trained customer churn XGBoost model and provides a `/predict` endpoint for making predictions. It uses Pydantic for request data validation.


#### 2. Containerization with Docker

[This repository](https://github.com/rsnemmen/docker-local-deploy) packages the previous application (the customer churn API) into a Docker image, ready to be shipped to the cloud (e.g. Google Cloud, AWS). 

#### 3. Google Cloud deployment

This model is currently being served on Google Cloud Cloud Run, and [can be accessed here](https://churn-model-j5c2fjobrq-wl.a.run.app). 

## Key Takeaways

1. **Reproducibility**  
   A single source of truth (`Dockerfile`) recreates the environment byte-for-byte.

2. **Cloud portability**  
   Although demonstrated on Google Cloud Run, the same container
   can be deployed to AWS, Azure, or on-prem K8s.

4. **Framework agnostic**  
   These methods can be applied to other ML frameworks (PyTorch, TensorFlow).


## Next steps

- [ ] Deploy the same model using a managed platform like SageMaker, Vertex AI, or Azure ML endpoints.
- [ ] Add basic monitoring (logging predictions)
- [ ] Set up CI/CD pipeline using GitHub Actions to rebuild/redeploy the container on code changes.