# Deployment Guide

This document describes how to deploy the Pharmacy Management System.

## 1. Common Preparation (All Platforms)

1. Clone or upload the project source code.
2. Create and activate a Python virtual environment.
3. Install dependencies:

```bash
pip install django
# plus any extra libraries you use (if listed in requirements.txt)
```

4. Apply database migrations:

```bash
python manage.py migrate
```

5. Create an admin user:

```bash
python manage.py createsuperuser
```

6. Collect static files for production:

```bash
python manage.py collectstatic
```

7. Set environment variables for production:
- `DJANGO_SECRET_KEY`
- `DJANGO_DEBUG=False`
- `ALLOWED_HOSTS` (e.g. your-domain.com)

---

## 2. Local Deployment (Development)

```bash
python manage.py runserver 0.0.0.0:8000
```

Access via `http://127.0.0.1:8000/`.

---

## 3. Deployment on PythonAnywhere (Example)

1. Upload the project folder to PythonAnywhere.
2. Create a virtualenv on PythonAnywhere and install dependencies.
3. In the **Web** tab:
   - Set the source code directory to the `Pharmacyproject` folder.
   - Configure the WSGI file to point to `Pharmacyproject.wsgi.application`.
4. Set environment variables in the **Web** tab.
5. Run `python manage.py collectstatic` in the Bash console.
6. Reload the web app.

---

## 4. Deployment on Render / Railway (Generic Steps)

1. Push the project to a Git repository (GitHub, GitLab, etc.).
2. Create a new **Web Service** on Render/Railway and connect the repo.
3. Configure:
   - Build command: `pip install -r requirements.txt`
   - Start command: `gunicorn Pharmacyproject.wsgi`
4. Set environment variables:
   - `DJANGO_SECRET_KEY`, `DJANGO_DEBUG`, `ALLOWED_HOSTS`, etc.
5. (Optional) Use PostgreSQL instead of SQLite for better reliability.
6. Trigger a deploy and wait for the URL to become live.

---

## 5. Static Files in Production

In `settings.py`, ensure:

- `STATIC_URL` and `STATIC_ROOT` are properly configured.
- `DEBUG = False` in production.
- For some platforms, you may need an additional WhiteNoise or server configuration for static files.

---

## 6. Security Checklist

- Turn off `DEBUG`.
- Use a strong, unique `SECRET_KEY`.
- Restrict `ALLOWED_HOSTS`.
- Use HTTPS in production (via the hosting provider).