
# MEAN Stack Deployment: Automated Cloud Infrastructure

A robust, full-stack MEAN (MongoDB, Express, Angular, Node.js) application deployed on **Google Cloud Platform (GCP)**. This project demonstrates a production-grade deployment strategy using **Docker Compose** for orchestration, **Nginx** as a reverse proxy, and **GitHub Actions** for a fully automated CI/CD pipeline.

---

### 🏗️ Technical Architecture

This application leverages a containerized microservices architecture to ensure scalability and ease of maintenance:

* **Frontend Gateway:** An Angular application served through an Nginx proxy.
* **API Layer:** A Node.js/Express backend that handles business logic and database transactions.
* **Database:** A dedicated MongoDB container with persistent volume storage.
* **Smart Routing:** Configured with **Relative Pathing** (`/api/...`) at the Nginx level. This allows the application to remain IP-agnostic, meaning the frontend automatically resolves the server's public IP without hardcoding.

---

### ✨ Key Features

* **Automated CI/CD:** Every push to the master branch triggers a GitHub Action that builds, pushes, and deploys the new code.
* **Reverse Proxy Integration:** Nginx handles all incoming Port 80 traffic, routing requests between the static frontend and the API.
* **Container Orchestration:** Uses Docker Compose to manage the lifecycle of all three tiers (Web, API, DB) as a single unit.
* **Cloud Native:** Specifically optimized for GCP Compute Engine environments.

---

### 📸 Deployment Showcases

#### 🚀 1. CI/CD Execution & Deployment

<img width="1468" height="749" alt="image" src="https://github.com/user-attachments/assets/8384b565-062e-4407-a56b-5e5d3e800437" />
<br>

🐳 2. Docker Image Build & Push

<img width="1745" height="500" alt="Screenshot 2026-02-24 031951" src="https://github.com/user-attachments/assets/83962c57-4f37-48ac-80ea-b0fdce0316c6" /><br>

<img width="1278" height="513" alt="image" src="https://github.com/user-attachments/assets/2614c363-fb3d-4766-80f3-03fa3f465fd7" /><br>

#### 🛡️ 3. Infrastructure (GCP)

<img width="1229" height="355" alt="image" src="https://github.com/user-attachments/assets/363f75dc-fe28-4f56-8c62-1aad50e5483e" /><br>

<img width="1172" height="721" alt="image" src="https://github.com/user-attachments/assets/36f68e29-b77c-403a-ad79-d23602b61217" /><br>

#### 🌐 4. Working Application UI

<img width="1264" height="619" alt="Screenshot 2026-02-24 183734" src="https://github.com/user-attachments/assets/af25469e-f5cf-434e-bd3f-a1dd0a6fd166" /><br>

<img width="1232" height="819" alt="Screenshot 2026-02-24 183806" src="https://github.com/user-attachments/assets/b25c5280-f978-4c02-af59-1bb62e4a1433" /><br>

<img width="1196" height="786" alt="Screenshot 2026-02-24 183720" src="https://github.com/user-attachments/assets/b1d3880a-4d0c-416f-97c7-abf954848f0e" /><br>


---

### 🛠️ Troubleshooting & Engineering Fixes

During the development and deployment of this stack, the following technical challenges were addressed:

1. **Nginx 502 Bad Gateway:** Identified a port mismatch where the proxy was looking for port 8081 while the backend was listening on 8080. Synchronized internal communication to 8080.
2. **Relative API Resolution:** Resolved `404 Not Found` errors by removing trailing slashes in the Nginx `proxy_pass` directive, ensuring the backend received the full `/api/tutorials` path.
3. **Cross-Origin (CORS) Pre-flight:** Implemented an `OPTIONS` handling block in Nginx to support browser pre-flight requests during the submission process.

---

### 🚀 Setup & Installation

#### Prerequisites

* Docker & Docker Compose installed on the VM.
* GitHub Secrets configured for `VM_HOST`, `VM_SSH_KEY`, and Docker Hub credentials.

#### Manual Deployment

1. **Clone the Repository:**
```bash
git clone https://github.com/amruthkumartj/mean-for-discoverdollar.git
cd mean-for-discoverdollar

```


2. **Spin Up Containers:**
```bash
sudo docker compose up -d --build

```



#### Maintenance Commands

* **Check Logs:** `sudo docker compose logs -f`
* **Service Status:** `sudo docker compose ps`

---
