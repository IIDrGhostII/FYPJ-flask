**5. Online Learning Platform**

```markdown
# Online Learning Platform

...

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

learning-platform/
├── README.md
├── app/
│   ├── __init__.py
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

