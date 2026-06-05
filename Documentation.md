# Django Notes App - CI/CD Deployment using Jenkins, Docker and Nginx

## Project Overview

The Django Notes App is a full-stack web application developed using Django and React. The application allows users to create, manage, and organize notes through a user-friendly interface.

The project follows a multi-tier architecture where:

* React provides the frontend user interface
* Django provides backend APIs and business logic
* SQLite stores application data
* Nginx acts as a reverse proxy
* Docker containerizes the application
* Jenkins automates the build and deployment process

---

# Application Architecture

```text
                    +----------------+
                    |     Browser    |
                    +--------+-------+
                             |
                             v
                    +----------------+
                    |     Nginx      |
                    | Reverse Proxy  |
                    +--------+-------+
                             |
            +----------------+----------------+
            |                                 |
            v                                 v
    +---------------+                +---------------+
    | React Frontend|                | Django Backend|
    +---------------+                +-------+-------+
                                             |
                                             v
                                    +---------------+
                                    | SQLite DB     |
                                    +---------------+
```

---

# Repository Structure

```text
django-notes-app/
│
├── api/                    # Django API Application
├── mynotes/                # Django Project Configuration
├── nginx/                  # Nginx Configuration
├── notesapp/               # React Frontend
├── staticfiles/            # Static Assets
│
├── Dockerfile              # Docker Image Definition
├── docker-compose.yml      # Multi-Container Deployment
├── Jenkinsfile             # CI/CD Pipeline
├── manage.py               # Django Management Script
├── requirements.txt        # Python Dependencies
├── Procfile                # Process Definition
├── db.sqlite3              # SQLite Database
└── .env                    # Environment Variables
```

The repository contains separate frontend and backend components managed through Docker Compose.

---

# Technology Stack

| Layer            | Technology            |
| ---------------- | --------------------- |
| Frontend         | React                 |
| Backend          | Django                |
| API              | Django REST Framework |
| Database         | SQLite                |
| Reverse Proxy    | Nginx                 |
| Containerization | Docker                |
| Orchestration    | Docker Compose        |
| CI/CD            | Jenkins               |
| Version Control  | GitHub                |

---

# Infrastructure Configuration

| Resource         | Configuration |
| ---------------- | ------------- |
| OS               | Ubuntu 24.04  |
| CPU              | 2 vCPU        |
| Memory           | 4 GB RAM      |
| Storage          | 20 GB         |
| Jenkins Port     | 8080          |
| Application Port | 8000          |

---

# Objective

The primary goal of this project was:

* Deploy a full-stack Django and React application
* Automate deployment using Jenkins
* Containerize services using Docker
* Manage services using Docker Compose
* Implement Continuous Integration and Continuous Deployment (CI/CD)

---

# Deployment Process

## Step 1: Create Jenkins Server

Provisioned an Ubuntu Server with:

* Ubuntu 24.04 LTS
* 2 vCPU
* 4 GB RAM
* 20 GB Storage

---

## Step 2: Install Required Tools

Installed:

* Git
* Docker
* Docker Compose
* OpenJDK 17
* Jenkins

Verified services and dependencies.

---

## Step 3: Configure Network Access

Opened required ports:

| Port | Purpose     |
| ---- | ----------- |
| 22   | SSH         |
| 8080 | Jenkins     |
| 8000 | Application |

---

## Step 4: Configure Jenkins

Accessed Jenkins Dashboard:

```bash
http://<SERVER-IP>:8080
```

Installed required plugins:

* Git Plugin
* Pipeline Plugin
* Docker Pipeline Plugin

---

## Step 5: Create Pipeline Job

Configured Jenkins Pipeline using SCM.

Repository Source:

```text
GitHub Repository
```

Pipeline reads the Jenkinsfile directly from source control.

---

## Step 6: CI/CD Execution

Pipeline performs:

1. Source Code Checkout
2. Docker Image Build
3. Container Deployment
4. Service Verification

Deployment command:

```bash
docker compose up -d --build
```

Docker Compose handles:

* React Frontend
* Django Backend
* Nginx Service
* Application Networking

---

# Challenges Faced

## Docker Permission Issue

### Problem

Jenkins failed to build Docker images.

Error:

```bash
permission denied while trying to connect to docker daemon
```

### Resolution

Added Jenkins user to Docker group.

```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
sudo systemctl restart docker
```

---

## Application Accessibility Issue

### Problem

Application deployed successfully but was inaccessible externally.

### Root Cause

Application port was not opened in the server security group.

### Resolution

Opened port 8000 in the firewall/security group configuration.

After updating network rules, the application became accessible.

---

# CI/CD Workflow

```text
Developer
    |
git push
    |
    v
GitHub Repository
    |
    v
Jenkins Pipeline
    |
    v
Docker Build
    |
    v
Docker Compose Deployment
    |
    v
Nginx
    |
    v
React + Django Application
```

---

# Result

Successfully deployed a full-stack Django Notes Application using Jenkins and Docker.

### Achievements

* Automated CI/CD Pipeline
* Dockerized Application
* Implemented Docker Compose Deployment
* Integrated Jenkins with GitHub
* Configured Nginx Reverse Proxy
* Resolved Docker Permission Issues
* Successfully exposed application to external users

The application is capable of creating and managing notes through a React-based user interface backed by Django APIs and SQLite database storage.

---

# Skills Demonstrated

* Jenkins CI/CD
* Docker
* Docker Compose
* Django
* React
* Nginx
* Git & GitHub
* Linux Administration
* Application Deployment
* DevOps Practices
* Troubleshooting & Debugging

---

# Conclusion

This project demonstrates the deployment of a modern full-stack application using industry-standard DevOps tools. The implementation showcases CI/CD automation, containerization, service orchestration, and production-style deployment practices using Jenkins, Docker, Docker Compose, and Nginx.
