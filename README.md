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
- **Database**: SQLite
- **Other**: JWT or Flask sessions for user authentication (optional enhancement)

---

## Project Structure

```
eduplanner/
├── backend/
│ ├── app.py     # Flask app and route definitions
│ ├── models.py     # SQLAlchemy models (User, Course, Task, StudyGroup, Membership)
│ ├── schemas.py    # (Optional) Marshmallow schemas for serialization
│ ├── routes/
│ │ ├── courses.py    # Course-related endpoints
│ │ ├── tasks.py     # Task CRUD endpoints
│ │ ├── studygroups.py   # Study group and membership endpoints
│ │ └── users.py    # User registration/login (optional)
│ ├── database.py    # DB initialization and session management
│ └── requirements.txt    # Backend dependencies
│
├── frontend/
│ ├── public/
│ │ └── index.html    # Main HTML file
│ ├── src/
│ │ ├── components/
│ │ │ ├── Navbar.js    # Navigation bar component
│ │ │ ├── CourseList.js     # Lists courses
│ │ │ ├── TaskList.js    # Lists tasks with filters
│ │ │ ├── StudyGroupList.js    # Study groups listing and join form
│ │ │ ├── TaskForm.js    # Create/edit task form with validation
│ │ │ └── StudyGroupForm.js     # Create study group form
│ │ ├── pages/
│ │ │ ├── CoursesPage.js     # Page component for courses route
│ │ │ ├── TasksPage.js    # Page component for tasks route
│ │ │ ├── StudyGroupsPage.js   # Page component for study groups route
│ │ │ └── Dashboard.js    # Overview with deadlines and groups
│ │ ├── App.js    # Main React app, routing setup
│ │ ├── index.js    # Entry point
│ │ └── api.js    # Fetch API wrapper functions
│ └── package.json    # Frontend dependencies
│
├── README.md 
└── .gitignore
```

---

## How It Works

### Backend

- **Flask API** exposes RESTful endpoints to handle CRUD operations for Courses, Tasks, Study Groups, and Membership.
- **SQLAlchemy ORM** manages data models and relationships:
  - Users have many Courses.
  - Courses have many Tasks.
  - Users belong to many StudyGroups through Membership, which records the user’s role.
- The backend validates input data before committing to the database.
- Endpoints support JSON requests and responses consumed by the React frontend.

### Frontend

- React app with **React Router** for navigating between different pages (`/courses`, `/tasks`, `/studygroups`, `/dashboard`).
- **Formik** handles forms with validation rules:
  - Required fields (e.g., task title).
  - Date format validation for deadlines.
  - Role validation in group membership.
- On each page:
  - Data is fetched from Flask API using `fetch()`.
  - Users can add, view, update, or delete tasks.
  - Users can view courses, create new courses, and join or create study groups.
- A persistent navigation bar allows easy switching between views.
- Tasks and groups are displayed with filtering options (e.g., filter tasks by course or status).

---

## Getting Started

### Prerequisites

- Python 3.8+
- Node.js 14+
- npm or yarn

### Backend Setup

1. Navigate to the backend folder:
   ```bash
   cd backend

2. Create and activate a virtual environment:
```
python -m venv venv
source venv/bin/activate    # Linux/macOS
venv\Scripts\activate       # Windows
```

3. Install dependencies:
```
pip install -r requirements.txt
```

4. Initialize the database:
```
flask db init
flask db migrate
flask db upgrade
```

5. Run the Flask server:
```
flask run
```

### Frontend Setup

1. Navigate to the frontend folder:
```
cd frontend
```

2. Install dependencies:
```
npm install
```

3. Start the React development server:
```
npm start
```

4. Open your browser at ```http://localhost:3000``` to view the app.

## API Endpoints Overview

| Resource      | Endpoint                | Methods             | Description                            |
|---------------|-------------------------|----------------------|----------------------------------------|
| Courses       | `/api/courses`          | GET, POST           | List all courses / Create a new course |
| Course Detail | `/api/courses/<id>`     | GET                 | Retrieve a specific course             |
| Tasks         | `/api/tasks`            | GET, POST           | List all tasks / Create a new task     |
| Task Detail   | `/api/tasks/<id>`       | GET, PUT, DELETE    | Get / Update / Delete a specific task  |
| Study Groups  | `/api/studygroups`      | GET, POST           | List / Create study groups             |
| Group Detail  | `/api/studygroups/<id>` | GET                 | Retrieve a specific study group        |
| Memberships   | `/api/memberships`      | POST                | Join a study group with a role         |

## Validation

All forms in the EduPlanner application use **Formik** for handling input and validation. Below are the key validation rules implemented throughout the app:

### ✅ Task Form Validation
- **Title**: Required field (min 3 characters).
- **Due Date**: Must be a valid date format (`YYYY-MM-DD`) and cannot be in the past.
- **Status**: Must be one of: `Pending`, `In Progress`, or `Completed`.
- **Course**: Task must be associated with an existing course.

### ✅ Study Group Form Validation
- **Group Name**: Required field (min 3 characters).
- **Meeting Time**: Must be a valid time string (e.g., `18:00` or `6:00 PM`).
- **Description**: Optional, but limited to 300 characters.

### ✅ Membership (Join Group) Validation
- **Role**: Required and must be one of the following:
  - `Leader`
  - `Member`
  - `Note-taker`
- Only one membership per user per group is allowed (validated on backend).

### ✅ Course Form Validation
- **Course Name**: Required field (min 3 characters).
- **Instructor Name**: Optional, but must be alphabetic if provided.

### ✅ User Registration (Optional Feature)
- **Email**: Must be a valid email format.
- **Password**: Minimum 6 characters, with at least one number and one uppercase letter.
- **Confirm Password**: Must match the password field.

### 🛠 Backend Validations (Flask)
- Backend re-validates critical fields (e.g., dates, relationships, foreign keys).
- Duplicate study group names and duplicate user memberships are prevented.

## Future Enhancements

Here are some planned or potential features that could improve the EduPlanner application:

- 🔐 **User Authentication**: Add user login and registration using JWT or Flask sessions.
- 🔔 **Deadline Reminders**: Email or in-app notifications for upcoming task deadlines and group meetings.
- 📈 **Analytics Dashboard**: Visual progress tracking using charts and graphs.
- 💬 **Real-Time Chat**: Allow members of a study group to chat in real-time using WebSockets.
- 📱 **Mobile Responsive Design**: Improve usability on tablets and smartphones.
- 📤 **File Uploads**: Attach resources or notes to tasks and study groups.
- 🌐 **Multi-language Support**: Add localization and language options.
- 📅 **Calendar View**: Visual timeline or calendar for tasks and meetings.

---

## Contributing

Contributions are welcome and encouraged! 🎉

To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Create a new Pull Request.

Please ensure code quality and add comments where necessary.

---

## License

This project is licensed under the **MIT License**.

You are free to use, modify, and distribute this project for personal or commercial purposes. See the [LICENSE](LICENSE) file for more details.

---

## Contact

For questions, support, or collaboration inquiries:

**Your Name**  
📧 your.email@example.com  
🔗 [LinkedIn](https://www.linkedin.com/in/your-profile)  
🌐 [Portfolio](https://your-portfolio.com)

---

> Thank you for using EduPlanner!  
> Happy studying and good luck with your academic journey! 🎓📚✨

