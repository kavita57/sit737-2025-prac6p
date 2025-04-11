
# The Cyber Tech 

Welcome to **The Cyber Tech**, a modern web application built for an electronics store that showcases gadgets, devices, and tech accessories. This sleek app allows users to browse through products and experience a simple cart interface — all powered by Node.js and Express.js.


##  Project Overview

This project serves as a basic full-stack application with containerization and Kubernetes deployment, ideal for showcasing web development and DevOps skills.

###  Features

-  Modern front-end UI using HTML & CSS
-  Backend server using Express.js
-  Dockerized for easy deployment
-  Kubernetes-compatible with deployment and service YAML
-  Lightweight and simple to extend

---

###  Prerequisites

Ensure the following tools are installed on your machine:

- [Node.js](https://nodejs.org/) (v14+ recommended)
- [npm](https://www.npmjs.com/)
- [Docker](https://www.docker.com/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

---

###  Local Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/kavita57/SIT737-2025-PRAC2P.git
   cd sit737-2025-prac2p
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Start the Server**
   ```bash
   npm start
   ```

4. **Visit the App**
   Open your browser and go to `http://localhost:3000`

---

##  Docker Support

To build and run the application in a Docker container:

```bash
docker build -t the-cyber-tech1:latest .
docker run -p 3000:3000 the-cyber-tech1:latest
```

---

##  Kubernetes Deployment

###  Deployment Steps

1. **Apply the Kubernetes Configurations**
   ```bash
   kubectl apply -f deployment.yaml
   ```

2. **Check Status**
   ```bash
   kubectl get pods
   kubectl get services
   ```

3. **Access the App**
   Once the LoadBalancer external IP is provisioned, open it in your browser on port `80`.

###  deployment.yaml 

- Deployment with 2 replicas
- LoadBalancer service exposing port 80 → container port 3000

