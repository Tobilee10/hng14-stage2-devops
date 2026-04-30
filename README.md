# hng14-stage2-devops


git clone <your-repo-url> && cd hng14-stage2-devops
    ```
2.  **Environment Setup**:
    ```bash
    cp .env.example .env
    ```
3.  **Deploy**:
    ```bash
    docker-compose up -d --build
    ```
4.  **Verify**: 
    Access the dashboard at `http://localhost:3000`.

## 🛠️ DevOps Features
*   **Networking**: Services communicate via Docker DNS (e.g., `REDIS_HOST=redis`) to prevent connection errors.
*   **Security**: All images use multi-stage builds and run as non-root users.
*   **Automation**: GitHub Actions pipeline for linting, testing, and integrationIf you are referring to the **README.md** as the single most important file for your submission, here is the final, standardized version. It incorporates the fixes for the `ConnectionError` and outlines the containerized architecture you've built.

# Job Processor Microservices

A containerized job processing system using **FastAPI**, **Node.js**, and **Redis**, designed for the HNG Internship Stage 2 DevOps track.

## 🏗️ Architecture
The system consists of four decoupled services:
*   **Frontend**: Node.js/Express dashboard.
*   **API**: FastAPI backend for job creation.
*   **Worker**: Python service for background processing.
*   **Broker**: Redis instance for message queuing.



## 🚀 Quick Start
1.  **Clone & Enter**:
    ```bash
    git clone <your-repo-url> && cd hng14-stage2-devops
    ```
2.  **Environment Setup**:
    ```bash
    cp .env.example .env
    ```
3.  **Deploy**:
    ```bash
    docker-compose up -d --build
    ```
4.  **Verify**: 
    Access the dashboard at `http://localhost:3000`.

## 🛠️ DevOps Features
*   **Networking**: Services communicate via Docker DNS (e.g., `REDIS_HOST=redis`) to prevent connection errors.
*   **Security**: All images use multi-stage builds and run as non-root users.
*   **Automation**: GitHub Actions pipeline for linting, testing, and integration.

## 📄 Documentation
*   **[FIXES.md](./FIXES.md)**: Detailed ledger of resolved architecturalIf you are referring to the **README.md** as the single most important file for your submission, here is the final, standardized version. It incorporates the fixes for the `ConnectionError` and outlines the containerized architecture you've built.



  