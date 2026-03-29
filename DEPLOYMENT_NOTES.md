Deployment Notes
================

Changes made:
- Updated `app/website/app/__init__.py` to load `SECRET_KEY` from the environment rather than using a hardcoded placeholder.
- Updated `app/website/app/__init__.py` to load `DATABASE_URI` from the environment for production deployment.

Environment variables for production:
- `SECRET_KEY`
- `DATABASE_URI`

If `DATABASE_URI` is not provided, the app now checks whether the Docker MySQL host `db` is available. If it is not available locally, the app falls back to a file-based SQLite database in the OS temporary directory, so the website can run on `http://127.0.0.1:5000` without Docker.

Vercel deployment files added at repo root:
- `requirements.txt`
- `server.py`
- `vercel.json`
- `runtime.txt`

To deploy on Vercel, point the project at this repository root. The app entrypoint is `server.py`, which imports the Flask application from `app/website`.
