# 🔐 Session-Based Authentication API

A robust backend authentication system built using **Node.js**, **Express**, and **PostgreSQL**, implementing secure **session-based authentication** with protected routes and user management.

---

## 🚀 Features

- **User Registration:** Secure signup flow.
- **User Login:** Authenticates users and creates an active session.
- **Session-Based Authentication:** Validates active users via session IDs.
- **Protected Routes:** Custom middleware to secure specific endpoints.
- **Profile Management:** Allow users to update their profile information.
- **Containerized Database:** PostgreSQL integration using Docker.
- **Type-Safe Queries:** Database interactions managed by Drizzle ORM.
- **Ready-to-Test:** Includes a complete Postman collection.

---

## 🛠 Tech Stack

- **Backend:** Node.js, Express.js  
- **Database:** PostgreSQL  
- **ORM:** Drizzle ORM  
- **Containerization:** Docker  
- **API Testing:** Postman  

---

## 📁 Project Structure

```text
.
├── db/
│   ├── index.js          # Database connection
│   └── schema.js         # Tables schema
├── routes/
│   └── user.routes.js    # Auth routes
├── postman/
│   └── session-auth.postman_collection.json
├── docker-compose.yml
├── index.js              # Entry point
├── drizzle.config.js
├── package.json
└── .gitignore
```

---

## ⚙️ Setup Instructions

### Prerequisites
Make sure you have the following installed on your machine:
* Node.js
* pnpm (or npm/yarn)
* Docker & Docker Compose

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd session-auth-nodejs
```

### 2. Install dependencies

```bash
pnpm install
```

### 3. Setup environment variables

Create a `.env` file in the root directory and add the following:

```env
DATABASE_URL=postgres://postgres:password@localhost:5432/postgres
DB_PASSWORD=password
PORT=8000
```

### 4. Start PostgreSQL using Docker

```bash
docker compose up -d
```

### 5. Run the server

```bash
pnpm dev
```
*The server will start at: `http://localhost:8000`*

---

## 🔑 API Endpoints

| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :---: |
| `POST` | `/users/signup` | Register a new user | ❌ |
| `POST` | `/users/login` | Login and create session | ❌ |
| `GET` | `/users` | Get current user | ✅ |
| `PATCH`| `/users` | Update user profile | ✅ |

---

## 🔐 Authentication Flow

This project utilizes **stateful session-based authentication**:

1. On successful login, the server generates a unique `SESSION_ID`.
2. The client must include this ID in the headers of subsequent requests:
   ```http
   session-id: <SESSION_ID>
   ```
3. Custom middleware checks the `session-id` against the database/store to grant access to protected routes.

---

## 🧪 API Testing

A ready-to-use Postman collection is included to test all endpoints.

**File Location:** `/postman/session-auth.postman_collection.json`

**Steps to use:**
1. Open Postman and click **Import**.
2. Select the provided `.json` file.
3. Set the required Collection Variables:
   * `BASE_URL` (e.g., `http://localhost:8000`)
   * `USER-EMAIL`
   * `USER_PASSWORD`
   * `SESSION-ID`
4. Run the endpoints!

---

## 📦 Future Improvements

- [ ] Add a `/logout` endpoint to explicitly destroy sessions.
- [ ] Implement session expiration and cleanup routines.
- [ ] Hash user passwords using `bcrypt` before database insertion.
- [ ] Add rate limiting to prevent brute-force attacks.
- [ ] Explore migrating to stateless JWT-based authentication.

---

## 📌 Author

Built by **Biswajit Samal** *(Link to your [GitHub](https://github.com/Samal-Biswajit))*