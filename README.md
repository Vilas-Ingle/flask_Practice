# Flask Student Registration System – CI/CD using Jenkins & GitHub Actions

## Project Overview

This project demonstrates a complete **CI/CD implementation** for a Flask-based **Student Registration System** using two industry-standard automation tools:

* **Jenkins**
* **GitHub Actions**

The application performs CRUD operations on student records stored in **MongoDB Atlas**.

Both Jenkins and GitHub Actions automate the software delivery lifecycle by building, testing, and deploying the application whenever code changes are pushed to the repository.

---

# Features

* Add Student
* View Students
* Update Student
* Delete Student
* MongoDB Atlas Integration
* Automated Unit Testing using Pytest
* CI/CD using Jenkins
* CI/CD using GitHub Actions
* Branch-based Deployment
* Email Notifications using Jenkins

---

# Project Architecture

```text
                        Developer
                            │
                        Git Push
                            │
                    GitHub Repository
                    ┌─────────┴─────────┐
                    │                   │
            GitHub Actions         Jenkins
                    │                   │
            Build → Test → Deploy  Build → Test → Deploy
                    │                   │
      Staging / Production      Email Notification
```

---

# Technology Stack

| Component            | Technology              |
| -------------------- | ----------------------- |
| Programming Language | Python 3.12             |
| Framework            | Flask                   |
| Database             | MongoDB Atlas           |
| Frontend             | HTML, Bootstrap         |
| Testing              | Pytest                  |
| Version Control      | Git & GitHub            |
| CI/CD                | Jenkins, GitHub Actions |
| Operating System     | Ubuntu 24.04 LTS        |
| Cloud Platform       | AWS EC2                 |

---

# CI/CD Implementation

This project demonstrates two different CI/CD implementations for the same Flask application.

---

## Part 1 – Jenkins CI/CD

The Jenkins pipeline is implemented using **Pipeline as Code** through the `Jenkinsfile`.

### Pipeline Stages

### Build

* Creates Python Virtual Environment
* Upgrades pip
* Installs dependencies
* Creates `.env` file

### Test

* Executes unit tests using Pytest
* Stops the pipeline if any test fails

### Deploy

* Stops the previous Flask application
* Starts the latest application instance

### Additional Features

* GitHub Webhook Integration
* Automatic Pipeline Trigger
* Email Notifications on Build Success/Failure

---

## Part 2 – GitHub Actions CI/CD

GitHub Actions is implemented using:

```text
.github/workflows/ci-cd.yml
```

### Workflow Stages

### Build

* Checkout Repository
* Setup Python
* Upgrade pip
* Install Dependencies

### Test

* Create `.env` file using GitHub Secrets
* Execute Pytest

### Deployment

Branch-based deployment strategy:

| Branch  | Environment |
| ------- | ----------- |
| staging | Staging     |
| main    | Production  |

Deployment jobs execute automatically after successful testing.

---

# Project Structure

```text
flask_Practice/
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── docs/
│   └── screenshots/
│       ├── jenkins/
│       └── github-actions/
│
├── templates/
├── app.py
├── test_app.py
├── requirements.txt
├── Jenkinsfile
├── README.md
└── .env
```

---

# Local Setup

## Clone Repository

```bash
git clone https://github.com/Vilas-Ingle/flask_Practice.git

cd flask_Practice
```

---

## Create Virtual Environment

Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

Windows

```cmd
python -m venv venv

venv\Scripts\activate
```

---

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Configure Environment Variables

Create a `.env` file:

```text
MONGO_URI=<MongoDB Atlas Connection String>

SECRET_KEY=<Your Secret Key>
```

---

## Run Application

```bash
python app.py
```

Application URL

```text
http://localhost:5000
```

---

# Running Unit Tests

```bash
pytest -v
```

---

# GitHub Webhook

A GitHub Webhook is configured with Jenkins.

Whenever code is pushed to the repository:

* GitHub notifies Jenkins
* Jenkins automatically starts the CI pipeline
* No manual intervention is required

---

# GitHub Secrets

GitHub Actions securely stores sensitive information using Repository Secrets.

Secrets configured:

* `MONGO_URI`
* `SECRET_KEY`

These secrets are injected during workflow execution without exposing their values in logs.

---

# Screenshots

Documentation screenshots are organized as follows:

```text
docs/
└── screenshots/
    ├── jenkins/
    └── github-actions/
```

### Jenkins

* Jenkins Installation
* Jenkins Dashboard
* Jenkins Pipeline
* Webhook Configuration
* Successful Build
* Email Notifications
* Flask Deployment

### GitHub Actions

* GitHub Actions Workflow
* Repository Secrets
* Build Success
* Test Success
* Staging Deployment
* Production Deployment
* Workflow Graph
* Workflow Logs

---

# Future Improvements

* Dockerize the Flask Application
* Deploy using Docker Compose
* Gunicorn + Nginx Deployment
* Deploy to AWS EC2 using GitHub Actions
* Kubernetes Deployment
* Terraform Infrastructure Provisioning
* Monitoring using Prometheus & Grafana

---

# Deliverables

* Jenkins CI Pipeline
* GitHub Actions Workflow
* Jenkinsfile
* GitHub Secrets
* GitHub Webhook
* Automated Build
* Automated Testing
* Branch-based Deployment
* Email Notifications
* Documentation
* Screenshots

---

# Learning Outcomes

Through this project, the following DevOps concepts were implemented:

* Continuous Integration (CI)
* Continuous Deployment (CD)
* Pipeline as Code
* GitHub Webhooks
* GitHub Actions
* Jenkins Pipelines
* GitHub Secrets
* Branch-based Deployment Strategy
* Automated Testing
* Build Automation

---

# License

This project is licensed under the MIT License.

