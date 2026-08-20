# ⚙️ Experiment 02: Automating ML Training & Testing with GitHub Actions

> **Experiment 02 · MLOps / CI Automation**

An experiment exploring how **GitHub Actions can automate machine learning workflows**, from code changes and testing to integration with **Azure Machine Learning**.

The goal was to understand how CI/CD principles can be applied to ML projects so that training and testing become **repeatable, automated, and less dependent on manual execution**.

---

## 🔍 What I Explored

This experiment focused on integrating a machine learning project with **GitHub Actions** and exploring two execution environments:

* 💻 **Offline Setup** — local development with GitHub Desktop and YAML-based CI workflows
* ☁️ **Online Setup** — GitHub Actions connected to an Azure Machine Learning pipeline
* 🧪 **Automated Testing** — running tests as part of the workflow
* 🔄 **Pipeline Automation** — triggering ML workflow steps through CI

The experiment also introduced a structured repository layout separating source code, tests, workflows, models, data, and outputs.

---

## 🏗️ Workflow Architecture

The overall workflow can be viewed as:

```text
Developer
    │
    │ Push / Commit
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├── Install Dependencies
    │
    ├── Run Tests
    │
    ├── Execute ML Workflow
    │
    └── Trigger Azure ML
    │
    ▼
Azure Machine Learning
    │
    ├── Training
    ├── Evaluation
    └── Outputs / Models
```

This creates a bridge between **software engineering workflows** and **machine learning workflows**.

---

## 💻 Offline Setup

The initial workflow was explored locally using:

* GitHub Desktop
* YAML workflow configuration
* Local source code and test directories

The purpose of this setup was to understand the structure of a GitHub Actions workflow before connecting it to cloud-based ML infrastructure.

A workflow can define steps such as:

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5

      - name: Install dependencies
        run: pip install -r requirements.txt

      - name: Run tests
        run: pytest
```

---

## ☁️ Online Setup — Azure Machine Learning

The second stage explored connecting the GitHub Actions workflow with **Azure Machine Learning**.

The idea is to allow a repository event, such as a push or pull request, to initiate an automated ML workflow rather than requiring every step to be executed manually.

```text
Git Push
   ↓
GitHub Actions
   ↓
CI Checks
   ↓
Azure ML Pipeline
   ↓
Training / Testing
   ↓
Model & Outputs
```

This demonstrates one of the foundations of **MLOps automation**: connecting source-code changes with reproducible ML workflows.

---

## 📁 Repository Structure

The experiment uses a structure that separates different components of the ML workflow:

```text
mlops/
│
├── .github/
│   └── workflows/
│
├── azureml/
├── models/
├── notebooks/
├── outputs/
├── raw/
├── src/
├── tests/
├── workflows/
│
├── exp2.ipynb
└── README.md
```

### Why this structure?

Separating the repository into logical components makes it easier to:

* maintain the project
* automate testing
* manage ML workflows
* separate source code from generated outputs
* integrate cloud-based ML pipelines
* scale the project beyond notebook-based experimentation

---

## 🧪 CI Pipeline

The core idea behind the experiment is to move from manually executing ML tasks:

```text
Edit Code
   ↓
Run Tests Manually
   ↓
Run Training Manually
   ↓
Check Results
```

toward an automated workflow:

```text
Push Code
   ↓
GitHub Actions
   ↓
Automated Tests
   ↓
ML Pipeline
   ↓
Results
```

This reduces repetitive manual steps and creates a more consistent development process.

---

## 🧠 What I Learned

This experiment helped me understand that **MLOps is not simply about deploying a model**.

A reliable ML system also needs automation around the model lifecycle:

> **Code → Test → Train → Evaluate → Deploy**

GitHub Actions provides the CI/CD layer, while Azure Machine Learning provides infrastructure for executing and managing ML workflows.

The experiment therefore connected two areas that are often treated separately:

**Software Engineering + Machine Learning**

---

## 🛠️ Technologies

* **GitHub Actions**
* **GitHub**
* **GitHub Desktop**
* **YAML**
* **Python**
* **Pytest**
* **Azure Machine Learning**
* **Jupyter Notebook**

---

## 📚 Reference

* [Azure GitHub Actions](https://github.com/Azure/actions?utm_source=chatgpt.com)

This experiment established the CI automation layer that makes that larger workflow possible.
