# 📝 Django Notes App

A production-style Notes Application built with **Django**, containerized using **Docker**, deployed behind **Nginx Reverse Proxy**, secured with **HTTPS**, and integrated with **MySQL**.

This project demonstrates end-to-end deployment practices including containerization, reverse proxy configuration, database integration, and secure application delivery.

---

## 🚀 Features

* Create and manage notes
* Django-based backend
* Responsive UI
* MySQL database integration
* Docker containerization
* Nginx reverse proxy setup
* HTTPS enabled using SSL
* Static file management
* Production-ready deployment workflow

---

## 🛠️ Tech Stack

| Layer            | Technology     |
| ---------------- | -------------- |
| Backend          | Django         |
| Database         | MySQL          |
| Containerization | Docker         |
| Reverse Proxy    | Nginx          |
| Orchestration    | Docker Compose |
| Security         | SSL / HTTPS    |
| OS               | Linux          |

---

## 📂 Project Structure

```bash
django-notes-app/
│
├── api/
├── data/
├── nginx/
│   └── default.conf
├── notesapp/
├── mynotes/
├── ssl/
├── staticfiles/
├── Dockerfile
├── docker-compose.yaml
├── manage.py
├── requirements.txt
├── Procfile
├── README.md
```

---

## ⚙️ Setup & Installation

### Clone Repository

```bash
git clone https://github.com/Akashbora02/django-notes-app.git
cd django-notes-app
```

---

## 🐳 Run Using Docker

Build containers:

```bash
docker compose up --build -d
```

Verify:

```bash
docker ps
```

Expected services:

```text
django_notes
nginx_proxy
mysql_db
```

---

## 🗄 Database Migration

Run migrations:

```bash
docker exec -it django_notes python manage.py migrate
```

Create admin user:

```bash
docker exec -it django_notes python manage.py createsuperuser
```

---

## 🔐 HTTPS Configuration

Generate SSL certificates:

```bash
mkdir ssl

openssl req \
-x509 \
-nodes \
-days 365 \
-newkey rsa:2048 \
-keyout ssl/server.key \
-out ssl/server.crt
```

Configure Nginx:

```nginx
listen 443 ssl;

ssl_certificate /etc/nginx/ssl/server.crt;

ssl_certificate_key /etc/nginx/ssl/server.key;
```

Restart:

```bash
docker compose restart
```

---

## 🌐 Access Application

Application:

```text
https://PUBLIC_IP
```

Admin:

```text
https://PUBLIC_IP/admin
```

---

## 📦 Docker Commands

View logs:

```bash
docker logs django_notes
docker logs nginx_proxy
docker logs mysql_db
```

Stop containers:

```bash
docker compose down
```

Rebuild:

```bash
docker compose up --build
```

---

## 🔍 DevOps Practices Implemented

✅ Docker Containerization
✅ Reverse Proxy Architecture (Nginx)
✅ Infrastructure Automation
✅ Secure Communication (HTTPS/SSL)
✅ Multi-Service Deployment
✅ Database Integration
✅ Production Troubleshooting
✅ Service Dependency Management

---

## 📸 Deployment Preview

Application successfully deployed using:

Django → Docker → MySQL → Nginx → HTTPS

---

## 👨‍💻 Author

Akash Bora

GitHub:
https://github.com/Akashbora02

LinkedIn:
https://www.linkedin.com/in/akash-bora/

---

## ⭐ Support

If you found this project useful:

⭐ Star this repository
🍴 Fork the project
🤝 Connect and collaborate
