# Week 5 — Python and Django Basics

**Dates:** 2 February – 6 February 2026
**Location:** 75Way Technologies, Mohali
**Track:** Multi-stack Training — Python

---

## Tasks Done

- Switched tracks from the MERN stack to the Python portion of the training curriculum, beginning with a quick refresher of Python fundamentals before moving on to web framework work.
- Reviewed Python core concepts including data types, control flow, functions, list and dictionary comprehensions, classes, inheritance, and the basics of exception handling using `try`, `except`, `else`, and `finally`.
- Set up the Python development environment with Python 3, virtual environments via `venv`, and Visual Studio Code with the official Python and Pylance extensions for type hints and intelligent autocomplete.
- Practised modular Python programming through the `import` system, including the difference between absolute and relative imports and the role of the `__init__.py` file in defining packages.
- Began the Django portion of the curriculum in the second half of the week with an introduction to its batteries-included philosophy and the model-template-view (MTV) architectural pattern.
- Installed Django through `pip` inside an isolated virtual environment and scaffolded the first project using `django-admin startproject`, then created an application within the project using `python manage.py startapp`.
- Studied the structure of a Django project, including the role of `settings.py` for global configuration, `urls.py` for URL routing, `models.py` for data models, `views.py` for request handlers, and the template directory for HTML rendering.
- Defined Django models using the ORM's field types and constraints, and used `python manage.py makemigrations` followed by `python manage.py migrate` to translate the model definitions into database tables.
- Explored the Django admin interface by registering models with `admin.site.register()` and observed how the admin panel automatically generates a fully functional CRUD interface for any registered model.
- Built a small blog application with two models (Author and Post) including a foreign key relationship, written corresponding views, mapped URLs in `urls.py`, and rendered the data using the Django template language with template inheritance.
- Used Django's built-in development server (`python manage.py runserver`) throughout the week and observed the auto-reload behaviour on source code changes during development.

---

## Technologies Used

- Python 3
- Django (latest stable LTS version)
- SQLite (Django's default development database)
- Django ORM and migrations
- Django Template Language
- pip and `venv` for dependency management
- Visual Studio Code with Python and Pylance extensions
- Git and GitHub

---

## Learnings

- Realised that switching from JavaScript to Python after four weeks of MERN was easier than expected, because the underlying programming concepts transfer cleanly across languages even though the syntax differs.
- Understood the practical value of Python's significant indentation, which forces a level of consistency in code formatting that JavaScript relies on conventions and linters to enforce.
- Picked up the rationale behind Django's batteries-included philosophy, where features like the admin panel, ORM, authentication, and forms are built-in rather than left to third-party libraries.
- Learned that the MTV pattern in Django is conceptually similar to the more widely known MVC pattern, with the template playing the role of the view and the view playing the role of the controller.
- Got first-hand experience of how powerful Django's auto-generated admin interface is for prototyping and internal tools, because a fully functional CRUD UI is available with virtually zero code.
- Understood that Django's migration system is one of its most important features, because it tracks schema changes over time and makes it safe to evolve the database alongside the source code.
- Observed that the Django Template Language is intentionally less powerful than full Python in templates, which encourages keeping business logic in views and models rather than scattered across HTML files.
