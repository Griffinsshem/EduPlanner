# 🎯 EduPlanner MVP – Minimum Viable Product

EduPlanner is a full-stack web application that helps students manage their academic life through course tracking, task management, and study group collaboration.

This MVP (Minimum Viable Product) outlines the essential features that make the app functional and useful without extra complexity.

---

## 🧩 Core MVP Features

### 1. 📚 Course Management
- Add a course (course name required, instructor optional).
- View a list of courses.
- Input validation (course name: min 3 characters).

### 2. ✅ Task Management
- Create a task (title, due date, status, associated course).
- View a list of tasks.
- Filter tasks by status (Pending, In Progress, Completed).
- Edit and delete tasks.
- Validation:
  - Title required (min 3 characters).
  - Due date must be valid (YYYY-MM-DD) and not in the past.
  - Status must be one of: Pending, In Progress, Completed.
  - Associated course must exist.

### 3. 👥 Study Groups
- Create a study group (group name, meeting time).
- Join a study group by selecting a role:
  - Leader
  - Member
  - Note-taker
- View study groups and their members.
- Backend prevents duplicate memberships per user per group.
- Validation:
  - Group name: min 3 characters.
  - Meeting time: valid time format.

### 4. 🧭 Multi-Page Navigation
- Single-page application (SPA) with routing via React Router:
  - `/courses` – Course list and form
  - `/tasks` – Task list and form
  - `/studygroups` – Study group list and form

### 5. 🔄 Frontend–Backend Communication
- React frontend interacts with Flask backend via Fetch API.
- JSON-based request and response structure.
- RESTful API endpoints:
  | Resource | Endpoint | Methods |
  |----------|----------|---------|
  | Courses | `/api/courses` | GET, POST |
  | Course Detail | `/api/courses/<id>` | GET |
  | Tasks | `/api/tasks` | GET, POST |
  | Task Detail | `/api/tasks/<id>` | GET, PUT, DELETE |
  | Study Groups | `/api/studygroups` | GET, POST |
  | Group Detail | `/api/studygroups/<id>` | GET |
  | Memberships | `/api/memberships` | POST |

### 6. 📝 Form Validation with Formik
- All forms include real-time input validation using Formik.
- Error messages shown to the user for incorrect inputs.

---

## 🚫 Out of Scope (Future Enhancements)

The following features are **not** part of the MVP and will be considered for future development:

- 🔐 User authentication (login/register)
- 🔔 Deadline notifications (email, in-app)
- 💬 Real-time group chat
- 📈 Task analytics and progress charts
- 📅 Calendar view
- 📱 Mobile optimization
- 📤 File uploads
- 🌐 Multi-language support

---

## 🛠️ Tech Stack

| Layer      | Technology                  |
|------------|-----------------------------|
| Frontend   | React, React Router, Formik |
| Backend    | Flask, Flask-RESTful        |
| Database   | SQLite + SQLAlchemy ORM     |
| Communication | Fetch API (JSON)        |

---

## 📦 MVP Deliverables

- Functional web app with:
  - Course management
  - Task tracking
  - Study group creation/join
- Validated inputs via Formik (frontend) and backend checks
- REST API with CRUD operations
- SQLite database with relevant models
- Basic styling for desktop
- GitHub repo with:
  - `README.md`
  - `/frontend` and `/backend` structure
  - Clear setup instructions

---

## 🚀 MVP Launch Checklist

- [x] Users can add, view, and manage tasks and courses.
- [x] Users can join/create study groups with roles.
- [x] Forms are validated on both frontend and backend.
- [x] SPA navigation works across all pages.
- [x] Backend provides working API endpoints.
- [x] Codebase is modular and clean.

---
