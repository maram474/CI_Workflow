# CI/CD Pipeline with Python

![CI](https://github.com/maram474/CI_Workflow/actions/workflows/ci.yml/badge.svg)
![Coverage](https://img.shields.io/badge/coverage-100%25-brightgreen)

This project demonstrates a complete **CI/CD pipeline** for Python applications using GitHub Actions.  
It includes **automated testing**, **code coverage**, **artifact collection**, **deployment to GitHub Pages**, and **email notifications**.

---

## 🚀 Features

- **Automated tests** using **Pytest**  
- **Code coverage reports** (XML & HTML)  
- **Artifact collection** for debugging failed tests  
- **Deployment to GitHub Pages** (coverage reports)  
- **Email notifications** with attached test reports  

---

## 🗂 Project Structure
CI_Workflow/
│
├── src/ # Source code
│ └── app.py
├── tests/ # Unit tests
│ └── test_app.py
├── .github/workflows/ci.yml # GitHub Actions workflow
├── requirements.txt # Python dependencies
├── README.md # Project documentation
└── .gitignore # Ignored files (cache, reports, secrets)


---

## ⚙️ How the Pipeline Works

1. **Triggering**:  
   - Push to `main` or `develop` branch  
   - Pull request creation or update  

2. **Tests Job**:
   - Checks out the repository  
   - Sets up Python environment  
   - Installs dependencies (`requirements.txt`)  
   - Runs **Pytest** tests with:
     - JUnit XML report (`report.xml`)  
     - Coverage report (`coverage.xml` and `htmlcov/`)  
   - Uploads artifacts for debugging  

3. **Deploy Job**:
   - Runs **only if tests succeed**  
   - Deploys **HTML coverage report** to **GitHub Pages**  

4. **Notify Job**:
   - Runs **always**, even if tests fail  
   - Downloads test report artifact  
   - Sends an **email notification** with:
     - Job status (success/failure)  
     - Commit SHA  
     - Attached `report.xml`  

---

