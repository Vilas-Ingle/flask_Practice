# Jenkins CI Pipeline for Flask Application

## Project Overview

This project demonstrates a **Continuous Integration (CI) Pipeline** for a Flask-based Student Registration System using **Jenkins**.

The pipeline automatically builds, tests, and deploys the application whenever code is pushed to the **main** branch of the GitHub repository.

The project also includes:

* Jenkins Pipeline as Code (`Jenkinsfile`)
* GitHub Webhook Integration
* Automated Unit Testing using Pytest
* Automated Email Notifications on Build Success/Failure
* Basic Deployment to a Jenkins staging environment

---

# Project Architecture

```text
Developer
    │
    │ Git Push
    ▼
GitHub Repository
    │
    │ Webhook
    ▼
Jenkins Pipeline
    │
    ├── Build
    ├── Test
    └── Deploy
    │
    ▼
Email Notification
```

---

# Technology Stack

| Component            | Technology       |
| -------------------- | ---------------- |
| Programming Language | Python 3         |
| Framework            | Flask            |
| Database             | MongoDB Atlas    |
| CI Tool              | Jenkins          |
| Version Control      | Git & GitHub     |
| Testing Framework    | Pytest           |
| Operating System     | Ubuntu 24.04 LTS |
| Cloud Platform       | AWS EC2          |

---

# Project Structure

```text
flask_Practice/
│
├── templates/
├── app.py
├── test_app.py
├── requirements.txt
├── Jenkinsfile
├── start_flask.sh
├── README.md
├── .env
└── docs/
    └── screenshots/
```

---

# Jenkins Pipeline

The Jenkins pipeline is defined inside the **Jenkinsfile**.

It contains three stages.

## Build Stage

The Build stage performs the following tasks:

* Creates Python Virtual Environment
* Upgrades pip
* Installs project dependencies
* Creates the required `.env` file

---

## Test Stage

The Test stage executes:

```bash
pytest -v
```

If any test fails, the pipeline stops immediately.

---

## Deploy Stage

The Deploy stage performs a simple deployment by:

* Stopping the previous Flask process (if running)
* Starting the Flask application

Deployment is intended for a staging environment for learning purposes.

---

# GitHub Webhook

A GitHub Webhook has been configured between GitHub and Jenkins.

Whenever code is pushed to the **main** branch:

* GitHub automatically notifies Jenkins.
* Jenkins starts the pipeline automatically.
* No manual build is required.

---

# Email Notifications

Jenkins has been configured with Gmail SMTP.

Notifications are automatically sent for:

* Successful Builds
* Failed Builds

This allows developers to know the pipeline status without logging into Jenkins.

---

# Local Setup

## Clone Repository

```bash
git clone https://github.com/Vilas-Ingle/flask_Practice.git
cd flask_Practice
```

---

## Create Virtual Environment

```bash
python3 -m venv venv
```

Activate it:

Linux/Mac

```bash
source venv/bin/activate
```

Windows

```cmd
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
MONGO_URI=<MongoDB Connection String>
SECRET_KEY=<Secret Key>
```

---

## Run Application

```bash
python app.py
```

Application will be available at:

```text
http://localhost:5000
```

---

# Running Tests

Execute:

```bash
pytest -v
```

---

# Screenshots

The project includes screenshots for:

* Project Structure
* Python Virtual Environment
* Jenkins Installation
* Jenkins Dashboard
* Jenkins Pipeline
* Successful Pipeline Execution
* GitHub Webhook
* Webhook Trigger
* Success Email Notification
* Failure Email Notification
* Flask Application
* Pytest Execution

Screenshots are available inside:

```text
docs/screenshots/flask-assignment/
```

---

# Future Improvements

This project currently demonstrates a basic Jenkins CI pipeline.

Future enhancements include:

* Dockerizing the Flask application
* Deploying using Docker Compose
* Deploying with Gunicorn + Nginx
* CI/CD using GitHub Actions
* Kubernetes deployment
* Production deployment using Systemd services

---

# Deliverables

✔ Jenkins Installation

✔ Jenkinsfile

✔ GitHub Webhook

✔ Automated Build

✔ Automated Testing

✔ Automated Deployment

✔ Email Notifications

✔ Documentation

✔ Screenshots

---

# License

This project is licensed under the MIT License.

