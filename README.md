# CodeCraftHub

A lightweight Learning Management System (LMS) — a small Node.js + Express REST API to track learning goals and courses using JSON file storage (no database required).

**Table of Contents**

- **Overview**: What this project does
- **Features**: Key capabilities
- **Requirements**: Software needed to run
- **Quick Start**: Install and run the server
- **API**: Endpoints and example requests
- **Storage**: How data is persisted
- **Project Structure**: Files and purpose
- **Troubleshooting**: Common fixes
- **Contributing & License**

**Overview**

CodeCraftHub provides simple CRUD operations for managing courses you want to learn. It's ideal for learning REST concepts or as a starter backend for small projects.

**Features**

- **Full CRUD**: Create, read, update, delete courses
- **JSON file storage**: Persistent storage in `data/courses.json`
- **RESTful routes**: Simple, predictable endpoints
- **Minimal dependencies**: Built with Express

**Requirements**

- Node.js 14+ and npm

**Quick Start**

1. Install dependencies:

```bash
npm install
```

2. Start the server (default port 5000):

```bash
npm start
```

Server will be available at: http://localhost:5000

**API**

Base URL: `http://localhost:5000/api/courses`

- Add a course — POST /api/courses

  Request JSON:

  ```json
  {
    "name": "Python Basics",
    "description": "Learn Python fundamentals",
    "target_date": "2025-12-31",
    "status": "Not Started"
  }
  ```

  Example curl:

  ```bash
  curl -X POST http://localhost:5000/api/courses \
    -H "Content-Type: application/json" \
    -d '{"name":"Python Basics","description":"Learn Python fundamentals","target_date":"2025-12-31","status":"Not Started"}'
  ```

- Get all courses — GET /api/courses

  ```bash
  curl http://localhost:5000/api/courses
  ```

- Get a single course — GET /api/courses/:id

  ```bash
  curl http://localhost:5000/api/courses/1
  ```

- Update a course — PUT /api/courses/:id

  Request (partial allowed):

  ```json
  { "status": "In Progress" }
  ```

  ```bash
  curl -X PUT http://localhost:5000/api/courses/1 \
    -H "Content-Type: application/json" \
    -d '{"status":"In Progress"}'
  ```

- Delete a course — DELETE /api/courses/:id

  ```bash
  curl -X DELETE http://localhost:5000/api/courses/1
  ```

**Storage**

Data is stored in `data/courses.json` (created automatically). Each course object typically includes `id`, `name`, `description`, `target_date`, and `status`.

**Project Structure**

```
codecrafthub/
├── app.js             # Main Express application and route mounting
├── package.json       # Project metadata and scripts
├── routes/
│   └── courses.js     # Course route handlers
├── utils/
│   └── fileHandler.js # Helpers for reading/writing JSON files
└── data/
    └── courses.json   # Persistent JSON storage (auto-created)
```

**Troubleshooting**

- "Cannot find module 'express'": run `npm install`
- "Port already in use": stop the conflicting process or set `PORT` env var before starting:

```bash
PORT=4000 npm start
```

**Contributing**

- Bug reports and PRs welcome. Please follow the existing code style and keep changes small and focused.

**License**

- MIT (or update to your preferred license)

---

If you'd like, I can also add example Postman collection, detailed response schemas, or README badges next.
