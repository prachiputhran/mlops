# ⚙️ Experiment 01: Setting Up a Reproducible ML Project with Git, Conda & Azure ML

[svg](https://github.com/prachiputhran/mlops#%EF%B8%8F-experiment-01-setting-up-a-reproducible-ml-project-with-git-conda--azure-ml)

> **Experiment 01 · MLOps / Environment & Reproducibility**

An experiment focused on setting up a **reproducible machine learning project environment** using **Git, Conda, Jupyter Notebook, Google Colab, and Azure Machine Learning**.

The goal was to understand how proper project structure and environment management can make machine learning experiments **reproducible, portable, version-controlled, and easier to integrate with cloud-based ML platforms**.

---

## 🔍 What I Explored

[svg](https://github.com/prachiputhran/mlops#-what-i-explored)

This experiment focused on establishing the foundation required for a structured MLOps workflow:

* 📁 **ML Project Structure** — organizing source code, notebooks, data, models, and outputs
* 🔀 **Git Version Control** — tracking project changes and maintaining reproducible versions
* 🐍 **Conda Environment** — creating an isolated Python environment for ML development
* 📦 **Dependency Management** — maintaining project dependencies using `requirements.txt`
* 💻 **Jupyter Notebook** — local experimentation and development
* ☁️ **Google Colab** — cloud-based notebook experimentation
* ☁️ **Azure Machine Learning** — creating reusable cloud ML environments
* 🔄 **Reproducibility** — ensuring the same dependencies and project configuration can be recreated across environments

---

## 🏗️ Project Setup Architecture

[svg](https://github.com/prachiputhran/mlops#%EF%B8%8F-project-setup-architecture)

The overall setup can be represented as:

```text
                    ML Project
                        │
          ┌─────────────┴─────────────┐
          │                           │
      Git / GitHub              Environment
          │                           │
          │                    ┌──────┴──────┐
          │                    │             │
          │                  Conda       requirements.txt
          │                    │
          │             ┌──────┴──────┐
          │             │             │
          │          Jupyter       Colab
          │
          ▼
    Version Control
          │
          ▼
    Azure ML Integration
          │
          ▼
   Azure ML Environment
```

**svg**

The setup creates a consistent development workflow from **local experimentation → version control → cloud ML execution**.

---

## 💻 Offline Setup

[svg](https://github.com/prachiputhran/mlops#-offline-setup)

The first stage was performed locally to establish the basic ML project environment.

### 1. Initialize Git Repository

Git was initialized to track changes to the machine learning project:

```bash
git init
git add .
git commit -m "Initial ML project setup"
```

Git provides version control for source code, notebooks, configuration files, and other project components.

---

### 2. Create a Conda Environment

A dedicated Conda environment was created to isolate the project's Python dependencies:

```bash
conda create -n mlops-env python=3.10
conda activate mlops-env
```

Using an isolated environment prevents dependencies from different projects from interfering with each other.

---

### 3. Install Dependencies

Required Python packages were installed inside the environment.

The dependencies were recorded using:

```bash
pip freeze > requirements.txt
```

The `requirements.txt` file can then be used to recreate the environment:

```bash
pip install -r requirements.txt
```

This improves reproducibility by documenting the packages required by the project.

---

## 📓 Coding Environment

[svg](https://github.com/prachiputhran/mlops#-coding-environment)

The experiment explored two notebook-based development environments:

### Jupyter Notebook

Jupyter Notebook was used for local experimentation, data analysis, visualization, and model development.

```bash
jupyter notebook
```

### Google Colab

Google Colab was used as an alternative cloud-based notebook environment.

This provides a convenient environment for running Python and ML experiments without requiring the complete local setup on every machine.

The same project dependencies can be installed in Colab using:

```python
!pip install -r requirements.txt
```

---

## ☁️ Online Setup — Azure Machine Learning

[svg](https://github.com/prachiputhran/mlops#%EF%B8%8F-online-setup--azure-machine-learning)

The second stage focused on integrating the project with **Azure Machine Learning**.

Azure ML environments provide a reusable definition of the software dependencies required to run machine learning jobs.

The environment can specify components such as:

* Python version
* Python packages
* Conda dependencies
* Docker configuration
* Runtime dependencies

The workflow can therefore be represented as:

```text
Local Project
     │
     ├── Git
     ├── Conda
     └── requirements.txt
     │
     ▼
Azure Machine Learning
     │
     ▼
Azure ML Environment
     │
     ├── Python
     ├── Dependencies
     └── Runtime Configuration
     │
     ▼
Reproducible ML Job
```

**svg**

This allows the same ML project to move from local development to Azure ML while maintaining a controlled software environment.

---

## 🔄 Reproducibility Workflow

[svg](https://github.com/prachiputhran/mlops#-reproducibility-workflow)

The experiment demonstrates the importance of keeping both **code and environment configuration** under control.

```text
Create Project
     ↓
Initialize Git
     ↓
Create Conda Environment
     ↓
Install Dependencies
     ↓
Generate requirements.txt
     ↓
Develop using Jupyter / Colab
     ↓
Commit Changes to Git
     ↓
Create Azure ML Environment
     ↓
Run ML Workflow
```

**svg**

Instead of relying on a developer's individual machine configuration, the required environment can be explicitly defined and recreated.

---

## 📁 Repository Structure

[svg](https://github.com/prachiputhran/mlops#-repository-structure)

The experiment follows a structured ML project layout:

```text
mlops/
│
├── .git/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│
├── src/
│
├── models/
│
├── outputs/
│
├── azureml/
│
├── requirements.txt
├── environment.yml
├── exp1.ipynb
└── README.md
```

**svg**

### Why this structure?

[svg](https://github.com/prachiputhran/mlops#why-this-structure)

Separating project components makes the ML workflow easier to maintain and reproduce.

* `data/` → stores datasets and processed data
* `notebooks/` → experimentation and analysis
* `src/` → reusable Python source code
* `models/` → trained model artifacts
* `outputs/` → generated results and experiment outputs
* `azureml/` → Azure ML configuration
* `requirements.txt` → Python package dependencies
* `environment.yml` → Conda environment definition
* `exp1.ipynb` → experiment notebook

---

## 🧪 Environment Configuration

[svg](https://github.com/prachiputhran/mlops#-environment-configuration)

Two dependency-management approaches were explored.

### `requirements.txt`

A Python package dependency list:

```text
numpy
pandas
scikit-learn
matplotlib
jupyter
```

It can be installed using:

```bash
pip install -r requirements.txt
```

### `environment.yml`

A Conda environment can also be described using:

```yaml
name: mlops-env

channels:
  - conda-forge
  - defaults

dependencies:
  - python=3.10
  - pip
  - numpy
  - pandas
  - scikit-learn
  - matplotlib
  - jupyter
```

The environment can then be recreated using:

```bash
conda env create -f environment.yml
conda activate mlops-env
```

This provides another mechanism for reproducing the project environment.

---

## 🔗 Git Version Control Workflow

[svg](https://github.com/prachiputhran/mlops#-git-version-control-workflow)

The basic Git workflow used in the experiment was:

```text
Modify Project
     ↓
git status
     ↓
git add .
     ↓
git commit
     ↓
git push
     ↓
GitHub Repository
```

Example:

```bash
git status
git add .
git commit -m "Add experiment 01 environment setup"
git push origin main
```

This ensures that changes to the project structure and environment configuration can be tracked over time.

---

## ☁️ Azure ML Environment Integration

[svg](https://github.com/prachiputhran/mlops#-azure-ml-environment-integration)

The project was prepared for integration with Azure Machine Learning by defining the required software environment.

The main concept is:

```text
requirements / Conda configuration
              ↓
       Azure ML Environment
              ↓
        ML Compute
              ↓
        Training Job
```

**svg**

Azure ML environments help provide a consistent runtime for machine learning jobs and reduce dependency-related inconsistencies between development and execution environments.

---

## 🧠 What I Learned

[svg](https://github.com/prachiputhran/mlops#-what-i-learned)

This experiment established the foundation for reproducible MLOps workflows.

The key concepts learned were:

### 1. Version Control

Git allows ML projects to maintain a history of code and configuration changes.

### 2. Environment Isolation

Conda allows different projects to maintain independent Python environments and dependencies.

### 3. Dependency Management

Files such as `requirements.txt` and `environment.yml` make it possible to document and recreate project environments.

### 4. Reproducible Experiments

A combination of **version-controlled code + controlled dependencies + structured project organization** makes ML experiments easier to reproduce.

### 5. Cloud Integration

Azure Machine Learning extends the local development workflow into a managed cloud ML environment.

The experiment therefore establishes the foundation:

> **Code + Environment + Version Control → Reproducible ML Workflow**

---

## 🛠️ Technologies

[svg](https://github.com/prachiputhran/mlops#%EF%B8%8F-technologies)

* **Git**
* **GitHub**
* **GitHub Desktop**
* **Python**
* **Conda**
* **Jupyter Notebook**
* **Google Colab**
* **Azure Machine Learning**
* **YAML**
* **requirements.txt**

---

## 📚 Reference

[svg](https://github.com/prachiputhran/mlops#-reference)

* [Azure Machine Learning — Environments](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-use-environments?utm_source=chatgpt.com)

