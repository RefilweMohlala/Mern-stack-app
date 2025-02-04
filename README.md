# MERN Stack Containerization with Docker & Docker Compose

## Overview
This project demonstrates how to containerize a **MERN (MongoDB, Express.js, React, Node.js)** stack application using **Docker** and **Docker Compose**. The main objective is to simplify and streamline the development, deployment, and scalability of MERN applications by utilizing containerization. This approach ensures that all services run in isolated environments, reducing conflicts between dependencies and improving development consistency.

---

## Problem Solved
Building and deploying a MERN stack application can often lead to issues with environment setup, dependency conflicts, and manual service configuration. By containerizing each component (frontend, backend, and database) with Docker, this project solves the following problems:

- **Environment Consistency**: Containers ensure the application runs consistently across different environments, whether it's a developer's machine, testing, or production.
- **Dependency Conflicts**: By isolating services in containers, each part of the stack can have its own specific environment, reducing dependency issues.
- **Simplified Deployment**: Docker Compose automates service orchestration, making it easier to deploy the entire stack with a single command.
- **Scalability**: With Docker, it's easier to scale individual services of the MERN stack, improving the application's ability to handle increasing traffic.

---

## Technologies Used
- **Docker**: Containerizes the individual services.
- **Docker Compose**: Orchestrates the services.
- **MongoDB**: Database service.
- **Express.js**: Backend framework.
- **React.js**: Frontend framework.
- **Node.js**: Backend runtime environment.

---

## Setup & Implementation

### 1. **Create a Docker Network**
Create a custom bridge network to allow inter-container communication:
```bash
docker network create mern
```
2. Frontend Containerization
A Dockerfile is created for the React frontend. Here’s how to build and run it:
```bash
docker build -t mern-frontend .
docker run --network=mern --name=frontend -d -p 5173:5173 mern-frontend
```
3. Database Setup (MongoDB)
To set up MongoDB with persistent storage:
```bash
docker run --network=mern --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest
```
4. Backend Containerization
The backend is containerized with the following Dockerfile:
```bash
docker build -t mern-backend .
docker run --network=mern --name=backend -d -p 5050:5050 mern-backend
```
5. Docker Compose
The docker-compose.yml file manages all the services (frontend, backend, and database). To run everything with one command:
```bash
docker-compose up -d
```
Features
Fully containerized MERN application.
Persistent MongoDB storage using Docker volumes.
Efficient orchestration with Docker Compose for easy service management.
Scalable and easily deployable setup.


## Screenshots
running containers
![Screenshot 2025-02-04 175139](https://github.com/user-attachments/assets/688b3e7a-90df-4bd9-8708-5ccca6861ed3)

removal of containers
![Screenshot 2025-02-04 175652](https://github.com/user-attachments/assets/ccb76efd-0287-4cfd-a2dc-6cc1592c8b38)

running containers + docker compose 
![Screenshot 2025-02-04 194023](https://github.com/user-attachments/assets/8ee97ab6-1c51-40f2-9164-464bf6ce344d)

