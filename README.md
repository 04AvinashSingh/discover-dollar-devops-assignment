# 🚀 MEAN Stack CRUD Application — DevOps Deployment  
### MongoDB | Express | Angular 15 | Node.js | Docker | Nginx | AWS EC2

This project is a full-stack MEAN CRUD application deployed in a production environment using **Docker**, **Docker Compose**, **Nginx reverse proxy**, and **AWS EC2**.

The app allows users to create, edit, search, and delete **tutorials**.  
Each tutorial contains:
- Title  
- Description  
- Published status  

---

# 📁 Project Structure

```
discover-dollar-devops-assignment/
│
├── backend/             # Node.js + Express REST API
│   ├── app/
│   ├── server.js
│   ├── Dockerfile
│
├── frontend/            # Angular 15 frontend
│   ├── src/
│   ├── angular.json
│   ├── Dockerfile
│
├── docker-compose.yml   # Defines MongoDB, backend, and frontend containers
└── README.md
```

---

# 🧰 Tech Stack

| Layer | Technology |
|------|------------|
| Frontend | Angular 15 |
| Backend | Node.js + Express |
| Database | MongoDB |
| Reverse Proxy | Nginx |
| Containerization | Docker + Docker Compose |
| Cloud Hosting | AWS EC2 (Ubuntu) |

---

# 🏗️ Architecture

### EC2 Instance  
Runs:
- Docker containers  
- Nginx reverse proxy  

### Docker Compose Containers  
```
- frontend (Angular build served via Nginx)
- backend (Node.js + Express API)
- mongo (MongoDB database)
```

Nginx routes requests:
- `/` → Angular frontend  
- `/api/` → Node backend  

---

# ▶️ Run Locally (Without Docker)

### Backend
```
cd backend
npm install
node server.js
```

### Frontend
```
cd frontend
npm install
ng serve --port 8081
```

---

# 🐳 Run With Docker (Required for Assignment)

```
cd discover-dollar-devops-assignment
docker compose up --build -d
```

Check running containers:

```
docker ps
```

---

# 🔗 API Endpoints

| Method | Endpoint | Description |
|--------|-----------|-------------|
| POST | `/api/tutorials` | Create tutorial |
| GET | `/api/tutorials` | Get all |
| GET | `/api/tutorials/:id` | Get by ID |
| PUT | `/api/tutorials/:id` | Update |
| DELETE | `/api/tutorials/:id` | Delete |
| GET | `/api/tutorials?title=xyz` | Search |

---

# 🌍 Deployment Steps (AWS EC2)

### 1. Install Docker
```
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
```

### 2. Install Docker Compose
```
sudo apt install docker-compose-plugin -y
```

### 3. Clone Repo
```
git clone <repo-url>
cd discover-dollar-devops-assignment
```

### 4. Start Containers
```
docker compose up -d --build
```

### 5. Configure Nginx
File: `/etc/nginx/sites-available/default`

```
server {
    listen 80;

    location / {
        proxy_pass http://localhost:3000;
    }

    location /api/ {
        proxy_pass http://localhost:5000/api/;
    }
}
```

```
sudo systemctl restart nginx
```

---

# 🌐 Public URL
```
http://13.51.150.216
```

---

# 🎉 Final Notes

This deployment demonstrates:
- Docker containerization  
- Multi-service orchestration  
- Nginx reverse proxy  
- Cloud deployment on EC2  
- Full MEAN stack integration  
