# Session-Based Authentication API

A backend authentication system built using Node.js, Express, PostgreSQL, and Docker.

## 🚀 Features
- User Signup
- User Login
- Session-based Authentication
- Protected Routes
- PostgreSQL with Docker
- Drizzle ORM

## 🛠 Tech Stack
- Node.js
- Express.js
- PostgreSQL
- Docker
- Drizzle ORM

## ⚙️ Setup

### 1. Clone the repo
git clone <repo-url>

### 2. Install dependencies
pnpm install

### 3. Start database
docker compose up -d

### 4. Run server
pnpm dev

## 🔑 API Endpoints

- POST /users/signup
- POST /users/login
- GET /users (Protected)
- PATCH /users (Protected)

## 🧪 Testing

Import Postman collection from `/postman` folder.
