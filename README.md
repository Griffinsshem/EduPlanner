# EduPlanner - Academic Planner & Study Group Tracker

## Introduction

EduPlanner is a full-stack web application designed to help students manage their academic life more effectively. It allows users to organize their courses, keep track of assignments and exams, and collaborate in study groups. EduPlanner solves the common problem of juggling multiple deadlines and group commitments by centralizing academic planning in one easy-to-use platform.

This project is built with a **React** frontend and a **Flask** backend API, demonstrating a real-world full-stack application with CRUD operations, complex data relationships, and client-server communication.

---

## Features

- **Course Management**: Add and view academic courses you're enrolled in.
- **Task Management**: Create, read, update, and delete tasks (assignments, exams, projects) linked to courses.
- **Study Groups**: Create or join study groups with fellow students.
- **User Roles in Groups**: When joining a study group, users can specify a role (e.g., leader, member).
- **Deadline Tracking**: Monitor due dates and status of tasks.
- **Validation & Forms**: All inputs validated using Formik for data integrity.
- **Multi-Route SPA**: Navigate smoothly between courses, tasks, and study groups via React Router.

---

## Tech Stack

- **Frontend**: React, React Router, Formik, Fetch API
- **Backend**: Flask, Flask-RESTful, SQLAlchemy (ORM)
- **Database**: SQLite (can be swapped for PostgreSQL or others)
- **Other**: JWT or Flask sessions for user authentication (optional enhancement)

---

## Project Structure

```
eduplanner/
├── backend/
│ ├── app.py # Flask app and route definitions
│ ├── models.py # SQLAlchemy models (User, Course, Task, StudyGroup, Membership)
│ ├── schemas.py # (Optional) Marshmallow schemas for serialization
│ ├── routes/
│ │ ├── courses.py # Course-related endpoints
│ │ ├── tasks.py # Task CRUD endpoints
│ │ ├── studygroups.py # Study group and membership endpoints
│ │ └── users.py # User registration/login (optional)
│ ├── database.py # DB initialization and session management
│ └── requirements.txt # Backend dependencies
│
├── frontend/
│ ├── public/
│ │ └── index.html # Main HTML file
│ ├── src/
│ │ ├── components/
│ │ │ ├── Navbar.js # Navigation bar component
│ │ │ ├── CourseList.js # Lists courses
│ │ │ ├── TaskList.js # Lists tasks with filters
│ │ │ ├── StudyGroupList.js # Study groups listing and join form
│ │ │ ├── TaskForm.js # Create/edit task form with validation
│ │ │ └── StudyGroupForm.js # Create study group form
│ │ ├── pages/
│ │ │ ├── CoursesPage.js # Page component for courses route
│ │ │ ├── TasksPage.js # Page component for tasks route
│ │ │ ├── StudyGroupsPage.js # Page component for study groups route
│ │ │ └── Dashboard.js # Overview with deadlines and groups
│ │ ├── App.js # Main React app, routing setup
│ │ ├── index.js # Entry point
│ │ └── api.js # Fetch API wrapper functions
│ └── package.json # Frontend dependencies
│
├── README.md # This file
└── .gitignore
```