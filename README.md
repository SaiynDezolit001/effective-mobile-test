# Effective Mobile DevOps Test

## Overview
This project demonstrates a minimal backend HTTP service written in Python running behind an Nginx reverse proxy using Docker Compose.

The backend service is accessible only inside the Docker network, while Nginx exposes port **80** to the host.

---

## Architecture

```text
Client
  |
  v
Nginx (port 80)
  |
  v
Backend (port 8080, internal Docker network only)
Nginx acts as a reverse proxy.

Backend is not exposed to the host.

Communication happens via a Docker bridge network (service discovery via Docker DNS).
.
├── backend/
│   ├── Dockerfile
│   └── app.py
├── nginx/
│   └── nginx.conf
├── docker-compose.yml
├── .gitignore
└── README.md
How to Run
docker compose up -d --build
How to Verify
curl http://localhost

Expected response:

Hello from Effective Mobile!
Technical Notes

Official Docker images are used.

Backend runs as a non-root user.

Docker healthcheck is implemented.

Only required port (80) is exposed.

No hardcoded IP addresses (Docker DNS-based service discovery).
