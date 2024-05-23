# Online Learning Platform

This is a Flask application for an online learning platform. The application includes the following features:

- User authentication (registration, login, logout)
- Course management (create, read, update, and delete courses)
- Enrollment and progress tracking for students
- Discussion forums for each course
- Instructor and student dashboards

## Getting Started

1. Clone the repository to your local machine.
2. Create a new virtual environment and install the required dependencies listed in `requirements.txt`.
3. Navigate to the `app` directory and run the Flask application using `python run.py`.
4. Access the application at `http://localhost:5000` in your web browser.

## Folder Structure
Sure, here's the full README file for the "Online Learning Platform" project, including the description:
markdownCopy code# Online Learning Platform

This is a Flask application for an online learning platform. The application includes the following features:

- User authentication (registration, login, logout)
- Course management (create, read, update, and delete courses)
- Enrollment and progress tracking for students
- Discussion forums for each course
- Instructor and student dashboards

## Getting Started

1. Clone the repository to your local machine.
2. Create a new virtual environment and install the required dependencies listed in `requirements.txt`.
3. Navigate to the `app` directory and run the Flask application using `python run.py`.
4. Access the application at `http://localhost:5000` in your web browser.

## Folder Structure
learning-platform/
├── README.md
├── app/
│   ├── init.py
│   ├── routes.py
│   ├── models.py
│   ├── forms.py
│   ├── templates/
│   │   ├── base.html
│   │   ├── index.html
│   │   ├── login.html
│   │   ├── register.html
│   │   ├── course.html
│   │   ├── new_course.html
│   │   ├── edit_course.html
│   │   ├── forum.html
│   │   ├── student_dashboard.html
│   │   └── instructor_dashboard.html
│   └── static/
│       └── styles.css
├── run.py
└── requirements.txt

- `app/`: This directory contains the Flask application code, including routes, models, forms, templates, and static files.
- `run.py`: This file is used to run the Flask application locally.
- `requirements.txt`: This file lists the required Python packages and their versions for the project.

## Example Code

### Course Model

```python
from app import db
from datetime import datetime

class Course(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100), nullable=False)
    description = db.Column(db.Text, nullable=False)
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
    instructor_id = db.Column(db.Integer, db.ForeignKey('user.id'), nullable=False)
    instructor = db.relationship('User', backref=db.backref('courses', lazy='dynamic'))
    lessons = db.relationship('Lesson', backref='course', lazy='dynamic')

    def __repr__(self):
        return f"<Course '{self.title}'>"

class Lesson(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100), nullable=False)
    content = db.Column(db.Text, nullable=False)
    course_id = db.Column(db.Integer, db.ForeignKey('course.id'), nullable=False)

    def __repr__(self):
        return f"<Lesson '{self.title}'>"

Contributing

1. Fork the repository and create a new branch for your changes.
2. Make your changes and commit them with descriptive commit messages.
3. Push your changes to your forked repository.
4. Create a pull request to merge your changes into the main repository.

