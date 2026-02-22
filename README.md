# Effective Mobile DevOps Test

## Overview
This project demonstrates a simple backend HTTP service written in Python running behind an Nginx reverse proxy using Docker Compose.

---

## Project Structure

.
├── backend/
│   ├── Dockerfile
│   └── app.py
├── nginx/
│   └── nginx.conf
├── docker-compose.yml
└── README.md

---

## How to Run

docker compose up -d --build

---

## How to Verify

curl http://localhost

Expected response:

Hello from Effective Mobile!

---

## Architecture

Client --> Nginx (port 80) --> Backend (port 8080, internal Docker network)

---

## Notes

- Only Nginx exposes port 80 to the host.
- Backend port 8080 is not published externally.
- Backend runs as a non-root user.
- Docker healthcheck is implemented.
