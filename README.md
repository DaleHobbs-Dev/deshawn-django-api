# DeShawn API (Django Backend)

## Project Setup

This project was initialized using `pipenv` and a setup script provided by Nashville Software School.

### Steps used to create the project

```bash
pipenv shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/nashville-software-school/course-bash-scripts/main/python/deshawn-setup.sh)"
````

Running these commands created the entire Django project structure, installed dependencies, and configured the backend API.

---

## What the Setup Script Does

The setup script automates the initial configuration of a Django REST API project. Instead of manually creating files and wiring everything together, the script builds a working backend from scratch.

### 1. Installs Dependencies

Installs required Python packages using `pipenv`, including:

* Django
* Django REST Framework
* CORS headers (for frontend communication)
* Pylint + Django plugin
* Autopep8

---

### 2. Creates the Django Project and App

* Creates a Django project: `deshawnproject`
* Creates an app: `deshawnapi`

---

### 3. Replaces Default Django Structure

Django normally starts with single files like:

* `models.py`
* `views.py`

The script removes those and replaces them with a more modular structure:

```text
deshawnapi/
  models/
    city.py
    walker.py
    dog.py
  views/
    city_view.py
    walker_view.py
    dog_view.py
  serializers/
```

This makes the codebase easier to scale and organize as the project grows.

---

### 4. Configures Project Settings

The script **overwrites** the default Django settings and URLs with a preconfigured setup:

#### `settings.py`

* Adds `rest_framework`, `corsheaders`, and `deshawnapi` to installed apps
* Enables token authentication
* Configures CORS for a frontend running on `localhost:3000`
* Sets up middleware for API usage

#### `urls.py`

* Replaces default routes with a REST Framework router
* Registers endpoints for:

  * `/cities`
  * `/walkers`
  * `/dogs`

---

### 5. Creates Models and Relationships

Defines the core data structure:

* **City**
* **Walker** (belongs to a city)
* **Dog** (belongs to a walker)

---

### 6. Creates API Views and Serializers

Each resource includes:

* `list()` → get all records
* `retrieve()` → get a single record

Serializers convert model data into JSON responses.

---

### 7. Sets Up Database and Seed Data

* Runs migrations to create database tables
* Loads fixture data from JSON files:

  * `cities.json`
  * `walkers.json`
  * `dogs.json`

This provides initial data for testing the API immediately.

---

### 8. Adds Development Tooling

* Creates `.vscode` debug configuration for running Django
* Configures `pylint` for Django projects
* Adds a `.pylintrc` file to reduce unnecessary warnings

---

## Result

After running the setup script, the project includes:

* A fully configured Django REST API
* Organized project structure (models, views, serializers)
* Predefined API endpoints
* Seeded database with sample data
* Development tooling ready to go

You can immediately run the server and access endpoints like:

```text
/cities
/walkers
/dogs
```

---

## Notes

* The setup script **overwrites some default Django files** (such as `settings.py` and `urls.py`) to match the structure expected in this course.
* This project is intended as a starting point for building out additional API functionality.
