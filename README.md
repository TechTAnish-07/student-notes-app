# 📓 StudyVault — Student Notes App

A two-tier web application built for **CS515 Unix Programming** (Assignment 03) at IIIT Tiruchirappalli.  
It demonstrates full-stack development with **Node.js + PostgreSQL**, containerized using **Docker**, and orchestrated with **Kubernetes (Minikube)**.

---

## 🚀 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| Backend | Node.js + Express.js |
| Database | PostgreSQL 15 |
| Containerization | Docker + Docker Compose |
| Orchestration | Kubernetes (Minikube) |
| Version Control | Git + GitHub |

---

## ✨ Features

- 📝 Add notes with subject, title, and content
- 🗂️ Filter notes by subject (Mathematics, Physics, CS, etc.)
- 🗑️ Delete notes
- 💾 Persistent storage via PostgreSQL
- 🐳 Fully containerized with Docker
- ☸️ Deployed on local Kubernetes cluster via Minikube

---

## 📁 Project Structure
```
student-notes-app/
├── app.js                  # Express backend + REST API
├── package.json
├── package-lock.json
├── Dockerfile              # Multi-stage optimized Docker build
├── docker-compose.yml      # Local development setup
├── .gitignore
├── public/
│   └── index.html          # Frontend UI
└── k8s/
    ├── app-deployment.yaml      # App deployment (2 replicas)
    ├── app-service.yaml         # NodePort service
    ├── db-deployment.yaml       # PostgreSQL + PVC
    └── db-service-secret.yaml   # DB service + credentials
```

---

## ⚙️ Phase 2 — Run with Docker Compose

### Prerequisites
- Docker Desktop installed and running

### Steps
```bash
# Clone the repository
git clone https://github.com/TechTAnish-07/student-notes-app.git
cd student-notes-app

# Build and start all containers
docker compose up --build
```

Visit **http://127.0.0.1:56618/** in your browser.

To stop:
```bash
docker compose down
```

---

## ☸️ Phase 3 — Run with Kubernetes (Minikube)

### Prerequisites
- Minikube installed
- kubectl installed
- Docker Desktop running

### Steps
```bash
# Start Minikube
minikube start

# Point Docker to Minikube's daemon
eval $(minikube docker-env)

# Build the image inside Minikube
docker build -t student-notes-app:latest .

# Apply Kubernetes manifests
kubectl apply -f k8s/db-service-secret.yaml
kubectl apply -f k8s/db-deployment.yaml
kubectl apply -f k8s/app-deployment.yaml
kubectl apply -f k8s/app-service.yaml

# Check pods are running
kubectl get pods

# Open the app in browser
minikube service notes-app-service
```

---

## 🔌 REST API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/notes` | Get all notes |
| POST | `/api/notes` | Create a new note |
| DELETE | `/api/notes/:id` | Delete a note by ID |
| GET | `/health` | Health check |

---

## 👨‍💻 Author

**Tanish Patidar**  
3rd Year — Computer Science and Engineering
IIIT Tiruchirappalli  
CS515 — Unix Programming
