# Week 6 — FastAPI and Modern Python APIs

**Dates:** 9 February – 13 February 2026
**Location:** 75Way Technologies, Mohali
**Track:** Multi-stack Training — Python

---

## Tasks Done

- Continued the Python portion of the training track with a switch from the batteries-included Django framework to FastAPI, a modern Python web framework designed specifically for building high-performance REST and GraphQL APIs.
- Studied the philosophical differences between Django and FastAPI, with the mentor highlighting how Django is optimised for full-stack monolithic web applications while FastAPI is optimised for headless API services that power frontend or mobile clients.
- Installed FastAPI along with `uvicorn` as the ASGI server inside a fresh Python virtual environment, and scaffolded the first API project using a minimal `main.py` entry point.
- Explored the core building blocks of a FastAPI application, including the application object, path operation decorators (`@app.get`, `@app.post`, `@app.put`, `@app.delete`), path parameters, and query parameters.
- Learned how FastAPI uses Python type hints not just for editor autocompletion but for automatic request validation, response serialisation, and OpenAPI schema generation at runtime.
- Studied Pydantic models in depth, defining request and response schemas using `BaseModel` subclasses with typed fields, default values, and field-level validation through `Field` and validator functions.
- Practised the automatic interactive API documentation provided by FastAPI through the Swagger UI at `/docs` and the alternative ReDoc UI at `/redoc`, both generated automatically from the route signatures and Pydantic models.
- Built a complete CRUD REST API for a simple library management resource, including endpoints for creating, listing, retrieving, updating, and deleting books, with full Pydantic validation on every request and response.
- Introduced asynchronous request handlers using the `async def` syntax and discussed the role of asynchronous I/O in handling many concurrent requests with a small number of threads.
- Integrated FastAPI with SQLAlchemy as the ORM and SQLite as the development database, defining ORM models, configuring a session dependency, and using FastAPI's dependency injection system to provide a database session to each route handler.
- Implemented basic JWT-based authentication on selected routes, learning how FastAPI's security utilities work in conjunction with OAuth2 password flow and bearer token verification.

---

## Technologies Used

- Python 3
- FastAPI (modern Python web framework)
- Uvicorn (ASGI server)
- Pydantic for request and response validation
- SQLAlchemy ORM
- SQLite for development database
- Swagger UI and ReDoc (auto-generated API documentation)
- pip and `venv` for dependency management
- Visual Studio Code with Python and Pylance extensions
- Git and GitHub

---

## Learnings

- Realised that FastAPI's heavy reliance on Python type hints is one of its biggest selling points, because the same type annotations serve as validation rules, documentation, and editor autocomplete simultaneously.
- Understood the practical difference between WSGI and ASGI, and why ASGI is essential for any framework that wants to support asynchronous request handlers and long-lived connections such as WebSockets.
- Picked up the value of Pydantic as a standalone data validation library, because the same `BaseModel` patterns are useful far beyond FastAPI in any Python project that needs to validate structured data.
- Learned that automatic OpenAPI documentation is not a marginal convenience but a major productivity gain, because frontend and mobile developers can explore and test the API directly without waiting for separate documentation to be written.
- Got first-hand experience of FastAPI's dependency injection system and understood that it is far more flexible than the equivalent patterns in Django or Express, because dependencies can be composed and reused across many routes.
- Understood that the choice between Django and FastAPI is not a question of which framework is better but a question of which is appropriate for the use case, and that many real-world systems use them for different services within the same product.
- Observed that even though the Python ecosystem appears slower than JavaScript at first, the combination of FastAPI plus an async database driver delivers performance that is competitive with Node.js for most API workloads.
