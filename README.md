🍰 Bakery Management System – Full Stack App

An interactive and scalable Bakery Management System built with modern technologies:

🧠 FastAPI (Python) for backend APIs
🔐 User Authentication using hashed passwords
🧾 MongoDB for user storage
📦 RabbitMQ for order queuing
👩‍🍳 React (Next.js-style) frontend for user interaction
🧵 Worker Service to consume queued orders
🐳 Docker Compose to run everything seamlessly

🧱 Architecture Overview
Frontend (React/Next.js)
       |
       v
Backend (FastAPI) -- MongoDB (Users)
       |
       v
RabbitMQ <--- Worker (Python)
       |
       v
PostgreSQL (Orders)

🚀 Features
📝 User Sign Up and Login (MongoDB)
🧾 Secure password hashing with passlib (bcrypt)
📩 Orders published to RabbitMQ
⚙️ Worker stores order data in MongoDB
🌐 Fully containerized with Docker
🔧 REST API with CORS support

📂 Project Structure
Himanshu-bakery-app/
├── backend/           # FastAPI backend
│   ├── main.py
│   ├── auth.py
│   ├── auth_utils.py
│   ├── models.py
│   ├── database.py
│   └── requirements.txt
├── frontend/          # React frontend
│   ├── app/orders/page.tsx
│   ├── app/orders/layout.tsx
│   └── Dockerfile
├── worker/            # Worker for RabbitMQ and PostgreSQL
│   ├── worker.py
│   ├── requirements.txt
│   └── Dockerfile
├── docker-compose.yml
└── README.md

⚙️ Tech Stack
Layer	Technology
Frontend	React + TypeScript (Next.js-like)
Backend	FastAPI (Python)
Auth DB	MongoDB
Orders DB	MongoDB
Messaging	RabbitMQ
Async Jobs	Python Worker
Containers	Docker Compose

🧪 How to Run the Project
Clone the repository:
git clone https://github.com/Himanshu-Bhagwani/Himanshu-bakery-app.git
cd Himanshu-bakery-app

Build and run everything with Docker Compose:

docker-compose up --build
Available Services: | Service | URL | |-----------|-----------------------------| | Frontend | http://localhost:3000 | | Backend | http://localhost:8000 | | MongoDB | localhost:27017 (No web UI) | | RabbitMQ | Internal only | | PostgreSQL| Internal only |

🔐 Authentication (MongoDB)
➕ Sign Up
POST /signup

Request body:
{
  "username": "john",
  "password": "secure123"
}

🔑 Login
POST /login

Request body:
{
  "username": "john",
  "password": "secure123"
}

Uses bcrypt via passlib for secure password hashing.

🧾 Order Processing (RabbitMQ + PostgreSQL)
Worker service listens to the orders queue

Order messages are stored in PostgreSQL:

CREATE TABLE IF NOT EXISTS orders (
    id SERIAL PRIMARY KEY,
    item TEXT,
    quantity INTEGER,
    customer TEXT
);

🖥️ Frontend (React)
Located in frontend/app/orders/page.tsx

Provides a form for username and password

Supports Sign Up & Login

Talks to backend at http://localhost:8000

🐳 Docker Compose Overview
docker-compose.yml
services:
  backend:      # FastAPI + MongoDB
  frontend:     # React App
  mongo:        # MongoDB instance
PostgreSQL & RabbitMQ are hardcoded in the worker and expected to run in the same network. Add them to Docker Compose if needed.

📦 Install Python/Node Dependencies (for local dev)
Backend:
cd backend
pip install -r requirements.txt
Frontend:
cd frontend
npm install
npm run dev
🔐 Environment Variables
Add a .env file for backend with:

ini
Copy
Edit
MONGO_URI=mongodb://mongo:27017
✅ Future Enhancements
JWT Authentication for secure sessions

WebSocket-based real-time order updates

Admin dashboard for bakery owners

MongoDB order tracking for analytics

🙌 Credits
Developer: Himanshu Bhagwani

University: UPES Dehradun

Project: Dockerized Full-Stack Bakery App
