
# Electronics Store Containerized Application

This project demonstrates containerization of a simple Node.js web application using Docker and Docker Compose. It also illustrates how to implement container health checks to ensure that if the application becomes unresponsive, the container is automatically restarted.

## Project Overview

The application serves a static HTML page (`index.html`) that showcases an electronics store with featured products. The backend is a simple Node.js server (`server.js`) that delivers the HTML page.

## Project Structure

├── Dockerfile
├── docker-compose.yml
├── index.html
├── package.json
├── package-lock.json
├── bg image.png
└── server.js

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on your machine.
- [Docker Compose](https://docs.docker.com/compose/install/) (typically included with Docker Desktop).

## How to Run the Application

### 1. Clone the Repository
Clone the project to your local machine:
```bash
git clone <repository-url>
cd <project-directory>
```

### 2. Build the Docker Image
Build the Docker image using the provided `Dockerfile`:
```bash
docker build -t myapp .
```

### 3. Start the Application with Docker Compose
Use Docker Compose to start the container in detached mode:
```bash
docker-compose up -d
```
This command builds and starts the container based on the configuration in `docker-compose.yml`.

### 4. Verify the Application
Open your browser and navigate to [http://localhost:3000](http://localhost:3000) to view the application.

## Container Health Check

The application uses Docker Compose health checks to monitor container health. In the `docker-compose.yml` file, the health check is defined as follows:

```yaml
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost:3000"]
  interval: 30s
  timeout: 10s
  retries: 3
```

- **test:** Runs `curl` to check if the application is reachable at `http://localhost:3000`.
- **interval:** Health check is performed every 30 seconds.
- **timeout:** The check will fail if no response is received within 10 seconds.
- **retries:** If the check fails 3 times consecutively, the container is marked as unhealthy, prompting Docker to restart it automatically.

To view the container's health status, run:
```bash
docker ps
```
Look for the status column, which will indicate if the container is `(healthy)` or `(unhealthy)`.

## Pushing the Docker Image to Docker Hub

If you wish to push your image to Docker Hub, follow these steps:

1. **Log in to Docker Hub:**
   ```bash
   docker login
   ```

2. **Tag the Docker Image:**
   
   ```bash
   docker tag mywebsite kavita493/mywebsite
   ```

3. **Push the Image:**
   ```bash
   docker push kavita493/mywebsite
   ```

After pushing, your image will be available on Docker Hub at:
```
https://hub.docker.com/r/kavita493/mywebsite
```

## Troubleshooting

- **Missing Files:** Ensure that `Dockerfile` and `docker-compose.yml` are in the root directory of your project.
- **Container Issues:** If the container fails to start or appears unhealthy, check the logs:
  ```bash
  docker logs <container_id>
  ```
- **Dependencies:** Verify that Docker and Docker Compose are installed and running correctly on your system.

# SIT737-2025-Prac2P: Microservice Deployment on GCP

## Project Overview
This project demonstrates the deployment of a microservice on Google Cloud Platform (GCP) using Docker and Google Artifact Registry. The microservice is built with Node.js and deployed in a containerized environment.

## Prerequisites
Ensure you have the following installed and configured:
- [Google Cloud SDK](https://cloud.google.com/sdk/docs/install)
- [Docker](https://www.docker.com/get-started)
- A Google Cloud Platform (GCP) project with billing enabled
- Authentication set up for Docker to push images to Google Artifact Registry

## Setup and Configuration

### 1. Initialize Google Cloud CLI
```sh
 gcloud init
```
Select the appropriate account and project.

### 2. Configure Docker Authentication for Google Artifact Registry
```sh
gcloud auth configure-docker australia-southeast1-docker.pkg.dev
```

### 3. Clone the Repository
```sh
git clone <repository-url>
cd sit737-2025-prac2p
```

### 4. Build the Docker Image
```sh
docker build -t mywebsite .
```

### 5. Tag the Image for Google Artifact Registry
```sh
docker tag mywebsite australia-southeast1-docker.pkg.dev/sit737-25t1-kavita-1a24f01/sit737-2025-prac5d/my-microservice:latest
```

### 6. Push the Image to Google Artifact Registry
```sh
docker push australia-southeast1-docker.pkg.dev/sit737-25t1-kavita-1a24f01/sit737-2025-prac5d/my-microservice:latest
```
## Running the Docker Container

By using docker run command we can check that it can boot your microservice from the published image:

```bash
docker run -d -p 8081:3000 gcr.io/sit737-25t1-kavita-1a24f01/mywebsite:latest











