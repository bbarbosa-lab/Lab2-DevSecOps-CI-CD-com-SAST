#  CI/CD with SAST — SonarCloud + Trivy + GitHub Actions

**Lab  Final** — DevSecOps Impacta

A demonstration project that integrates **SonarCloud** (SAST + Code Quality) and **Trivy** (vulnerability scanning for dependencies, IaC, and Docker images) into a complete **CI/CD** pipeline using **GitHub Actions**.

---

##  Objective

To demonstrate in practice how to implement **Security as Code** in a modern pipeline:
- Static Application Security Testing (SAST) with SonarCloud
- Vulnerability scanning of dependencies, Dockerfiles, and IaC with Trivy
- Integration with GitHub Security
- Automated testing with coverage reporting

---

##  Technologies Used

- **Python 3.9** + **Flask**
- **SonarCloud** (SAST + Code Quality)
- **Trivy** (Container + IaC scanning)
- **GitHub Actions**
- **Docker**
- **pytest** + **coverage**

---

##  Project Structure

```bash
.
├── .github/
│   └── workflows/
│       └── sast-scan.yml          # Main CI/CD Pipeline
├── app/
│   ├── app.py                     # Flask app with intentional vulnerabilities
│   ├── test_app.py                # Unit tests
│   ├── requirements.txt           # Dependencies with known CVEs (for demo)
│   └── Dockerfile
├── sonar-project.properties       # SonarCloud configuration
├── .gitignore
└── README.md

 Intentional Vulnerabilities (Demo Purposes)
This project intentionally includes security flaws to demonstrate detection:

SQL Injection (/user)
Command Injection (/ping)
Hardcoded Secrets
Outdated dependencies with known vulnerabilities

A secure version of the endpoint (/user/safe) is also provided for comparison.

 Setup Instructions
1. Create the GitHub Repository

Go to github.com/new
Repository name: lab-final (or any name you prefer)
Description: CI/CD with SAST — SonarCloud + Trivy + GitHub Actions
Visibility: Public (required for free SonarCloud plan)
Click Create repository

2. Configure SonarCloud

Go to sonarcloud.io and log in with GitHub
Click + → Analyze new project
Select your repository
Choose With GitHub Actions
Save your Project Key and Organization Key

3. Add the Files
Copy all the files into your repository with the structure shown above.
4. Add GitHub Secrets
Go to Settings → Secrets and variables → Actions and add:

SONAR_TOKEN → Generate this in SonarCloud (Project → Administration → Security)


 GitHub Actions Pipeline
The workflow .github/workflows/sast-scan.yml runs the following jobs:
Job 1: SonarCloud SAST

Runs tests with coverage
Performs full SAST analysis
Publishes results to SonarCloud



