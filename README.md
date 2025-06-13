# Flask Jenkins Docker CI/CD Pipeline

---

## 🚀 Project Overview

This project demonstrates how to automate the deployment of a simple **Flask** web application using:

- **Jenkins** for Continuous Integration / Continuous Deployment (CI/CD)
- **Docker** for containerizing the application
- **Docker Hub** for storing and sharing the Docker images
- **GitHub** as the source code repository

The goal is to show how modern software projects are built, packaged, and deployed automatically using industry-standard DevOps tools.

---

## 🧱 What Does This Project Do?

1. You write a small Flask app (a Python web app) that displays a welcome message.
2. You create a **Dockerfile** that packages this app into a Docker container.
3. Jenkins automatically pulls the latest code from GitHub.
4. Jenkins builds a Docker image from the app.
5. Jenkins logs into Docker Hub and pushes the image.
6. Anyone can pull the image from Docker Hub and run the app anywhere.

---

## 📋 Why This Matters for Beginners

- Learn **CI/CD concepts** — automating software building and deployment.
- Understand **Docker containers** — how apps are packaged with their dependencies.
- Get hands-on with **Jenkins pipelines** — the industry-standard automation server.
- Practice working with **GitHub and Docker Hub** — key tools for source control and container registry.

---
---

## 🏗️ Architecture Diagram

![image](https://github.com/user-attachments/assets/1c779419-cfc6-4c16-8b73-cfadc9eeaab1)


1. Push code changes to GitHub repository.

2. Jenkins triggers build on code push.

3. Jenkins builds Docker image and pushes it to Docker Hub.

4. Docker image is ready to deploy anywhere (cloud, local, servers).

---

## 📋 Key Steps Followed

1. **Code Development**  
   Create a simple Flask app (`app.py`) and Dockerfile.

2. **Source Control**  
   Push code to GitHub repository.

3. **Jenkins Pipeline**  
   Jenkinsfile defines steps to:
   - Checkout the repo
   - Build the Docker image
   - Login to Docker Hub
   - Push the image to Docker Hub

4. **Docker Hub**  
   Stores the built Docker image securely.

5. **Deployment**  
   Pull the Docker image from Docker Hub and run it anywhere.

---

## 🖼️ Screenshots

### Jenkins Pipeline Success

![image](https://github.com/user-attachments/assets/5f7477ab-17e9-41be-bbd8-e726a405f08c)


---

### Docker Hub Image Repository

![image](https://github.com/user-attachments/assets/a7860e45-4019-4d28-bec1-dc7d8b789ca3)


---

### Running Flask App in Browser

![image](https://github.com/user-attachments/assets/4f9bc65a-72b7-4819-9a0a-0eab7aaf35f9)


---
