# FastAPI - Books Example

Overview

This repository contains a small example FastAPI application that demonstrates:

- Connecting to a SQLite database using SQLAlchemy
- Defining a simple `Book` model and CRUD-style endpoints
- Running the app with Uvicorn and automatic reload for development

The project is intentionally minimal so it's easy to read and adapt.

Repository layout

- `books.py` - the FastAPI application and route definitions
- `models.py` - SQLAlchemy ORM models (e.g. `Book`)
- `database.py` - database engine and session setup
- `README.md` - this file
- `.gitignore` - ignores virtualenv, notebooks, and OS files

Requirements

- Python 3.10+ (tested with Python 3.13 in this workspace)
- Virtual environment recommended (a venv is included at `FastAPI/`)
- Install dependencies:

```bash
pip install fastapi uvicorn sqlalchemy
```

Quick start (developer)

1. Activate the project's virtualenv:

```bash
source FastAPI/bin/activate
```

2. Install dependencies (if not already installed):

```bash
pip install -r requirements.txt  # or pip install fastapi uvicorn sqlalchemy
```

3. Create the database tables (one-time):

```bash
python -c "from database import Base, engine; Base.metadata.create_all(bind=engine)"
```

4. Run the FastAPI app with auto-reload:

```bash
uvicorn books:app --reload
```

5. Open the interactive docs in your browser:

```text
http://127.0.0.1:8000/docs
```

What to look for

- `models.py` should define a `Book` model with a primary key (e.g. `id = Column(Integer, primary_key=True)`).
- `database.py` configures a SQLite file `books.db` and exposes `SessionLocal` and `Base`.
- `books.py` contains API endpoints that use SQLAlchemy sessions to access the DB.

Development notes

- This repo uses `Base.metadata.create_all()` for simplicity. For real projects use Alembic for migrations.
- Add a `.env` to store any environment-specific configuration and add it to `.gitignore`.
- Keep the `FastAPI/` virtualenv out of source control (already in `.gitignore`).

Contributing

- Create a fork, make changes, and open a pull request. Keep changes focused and include tests when possible.

License

Replace this section with a license of your choice (MIT is a good permissive default).

Contact

If you want help adapting this to a different DB (Postgres, MySQL) or adding Alembic, tell me what you'd like and I can make the changes.
