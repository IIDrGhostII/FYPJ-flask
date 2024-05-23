**4. Recipe Manager**

```markdown
# Recipe Manager

This is a Flask application for managing recipes. The application allows users to:

- Create, read, update, and delete recipes
- Categorize recipes by cuisine, difficulty level, or dietary restrictions
- Search for recipes based on various criteria (e.g., ingredients, cuisine, cooking time)
- Add and manage a shopping list for ingredients needed for selected recipes

## Getting Started

1. Clone the repository to your local machine.
2. Create a new virtual environment and install the required dependencies listed in `requirements.txt`.
3. Navigate to the `app` directory and run the Flask application using `python run.py`.
4. Access the application at `http://localhost:5000` in your web browser.

## Folder Structure

recipe-manager/
├── README.md
├── app/
│   ├── init.py
│   ├── routes.py
│   ├── models.py
│   ├── forms.py
│   ├── templates/
│   │   ├── base.html
│   │   ├── index.html
│   │   ├── recipe.html
│   │   ├── edit_recipe.html
│   │   ├── search.html
│   │   └── shopping_list.html
│   └── static/
│       └── styles.css
├── run.py
└── requirements.txt

## Example Code

### Recipe Model

```python
from app import db

class Recipe(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100), nullable=False)
    description = db.Column(db.Text, nullable=False)
    cuisine = db.Column(db.String(50), nullable=False)
    difficulty = db.Column(db.Enum('Easy', 'Medium', 'Hard'), nullable=False)
    prep_time = db.Column(db.Integer, nullable=False)
    cook_time = db.Column(db.Integer, nullable=False)
    ingredients = db.relationship('Ingredient', backref='recipe', lazy='dynamic')

    def __repr__(self):
        return f"<Recipe '{self.name}'>"

class Ingredient(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100), nullable=False)
    quantity = db.Column(db.Float, nullable=False)
    unit = db.Column(db.String(20), nullable=False)
    recipe_id = db.Column(db.Integer, db.ForeignKey('recipe.id'), nullable=False)

    def __repr__(self):
        return f"<Ingredient '{self.name}, {self.quantity} {self.unit}'>"

