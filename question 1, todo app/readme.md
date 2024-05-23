# Simple Todo App

This is a Flask application that allows users to create, read, update, and delete todo items. The application has a single page that displays all the todo items, and users can add new items, mark items as completed, or delete items.

## Getting Started

1. Clone the repository to your local machine.
2. Create a new virtual environment and install the required dependencies listed in `requirements.txt`.
3. Navigate to the `app` directory and run the Flask application using `python run.py`.
4. Access the application at `http://localhost:5000` in your web browser.

## Folder Structure

todo-app/
├── README.md
├── app/
│   ├── init.py
│   ├── routes.py
│   ├── models.py
│   ├── templates/
│   │   ├── base.html
│   │   └── index.html
│   └── static/
│       └── styles.css
├── run.py
└── requirements.txt

- `app/`: This directory contains the Flask application code, including routes, models, templates, and static files.
- `run.py`: This file is used to run the Flask application locally.
- `requirements.txt`: This file lists the required Python packages and their versions for the project.

## Example Code

### Todo Model

```python
from datetime import datetime
from app import db

class Todo(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100), nullable=False)
    completed = db.Column(db.Boolean, default=False)
    created_at = db.Column(db.DateTime, default=datetime.utcnow)

    def __repr__(self):
        return f"<Todo '{self.title}'>"

Contributing

1. Fork the repository and create a new branch for your changes.
2. Make your changes and commit them with descriptive commit messages.
3. Push your changes to your forked repository.
4. Create a pull request to merge your changes into the main repository.