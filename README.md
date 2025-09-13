# FastAPI - Books Example

Simple FastAPI project that demonstrates a SQLite database connection with SQLAlchemy.

Requirements

- Python 3.10+ (this project uses a virtual environment at `FastAPI/`)
- Install dependencies in your venv, e.g. `pip install fastapi uvicorn sqlalchemy`.

Quick start

1. Activate the project's virtualenv:

```bash
source FastAPI/bin/activate
```

1. Create the database tables (the app may create them automatically if configured):

```bash
python -c "from database import Base, engine; Base.metadata.create_all(bind=engine)"
```

1. Run the app with automatic reload:

```bash
uvicorn books:app --reload
```

Endpoints

- GET / - root (if implemented)
- Other endpoints are defined in `books.py`.

Notes

- A `.gitignore` is included to avoid committing large and personal files.
- For production use, use Alembic for database migrations instead of `create_all()`.
