# 📚 Library Management API

A simple and modular **FastAPI + PostgreSQL + Docker** based project to manage books.  
It supports CRUD operations and includes automatic API documentation using Swagger UI.

---

## 🚀 Features

- 🔥 FastAPI backend with automatic docs
- 🐳 Docker containerization (app + PostgreSQL)
- 🧱 SQLAlchemy ORM
- 🧪 Easy local development with hot reload
- 🔐 Environment variable-based configuration

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python 3.11, FastAPI |
| Database | PostgreSQL |
| ORM | SQLAlchemy |
| Container | Docker & Docker Compose |

---

## 📦 Installation & Setup

### 1️⃣ Clone the repository

```sh
git clone https://github.com/<your-username>/LibraryManagement.git
cd LibraryManagement
```

### 2️⃣ Create .env file

Make a copy of `.env.example` and rename it to `.env`:

```env
POSTGRES_USER=libraryuser
POSTGRES_PASSWORD=librarypass
POSTGRES_DB=librarydb
POSTGRES_HOST=postgres
POSTGRES_PORT=5432

DATABASE_URL=postgresql://libraryuser:librarypass@postgres:5432/librarydb
```

### 3️⃣ Run using Docker

```sh
docker compose up --build
```

This will:
- Build the FastAPI Docker image
- Start PostgreSQL
- Auto-create database tables

### 4️⃣ Access the API

| Endpoint | URL |
|----------|-----|
| Home | http://localhost:8000/ |
| Swagger Docs | http://localhost:8000/docs |
| OpenAPI JSON | http://localhost:8000/openapi.json |

---

## 🧪 Example Request

### Create a Book (POST /book/)

```json
{
  "title": "Atomic Habits",
  "author": "James Clear",
  "genre": "Self Help",
  "year": 2018,
  "available": true
}
```

---

## 📁 Folder Structure

```
📦 LibraryManagement
├── 📁 routes
│   └── book_route.py
├── 📁 services
│   └── book_service.py
├── 📁 sql
│   ├── models.py
│   ├── crud.py
│   └── database.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── main.py
└── README.md
```

---

## 🧠 Why It Now Works Properly

Originally, the backend attempted connecting to PostgreSQL before the DB was ready.

**Fixes applied:**
- `depends_on` was added in `docker-compose.yml`
- Correct Docker networking hostname was used: `postgres` instead of `localhost`
- SQLAlchemy auto-created tables using `Base.metadata.create_all(engine)`

Now the app waits until the DB is ready and initializes tables automatically.

---

## 🐙 GitHub Notes

### ✔ Safe to commit:
- `Dockerfile`
- `docker-compose.yml`
- `.env.example`
- `requirements.txt`

### ❌ Do NOT commit:
- `.env`
- `__pycache__/`
- `.venv/`

---

## ❤️ Contributing

Contributions are welcome!  
Feel free to fork and submit a PR.

---

## 📄 License

Distributed under the MIT License.

---

Made with 💙 using **FastAPI**, **SQLAlchemy**, and **Docker**.

