# JeevanSetu Full-Stack Prototype

This package preserves the existing JeevanSetu HTML portal UI and adds a shared FastAPI + SQLite backend. It also repairs a malformed report script discovered during the source audit and changes live updates to poll the API when the optional Socket.IO browser client is not present.

## What is included

- `static/index.html` — the existing portal UI with syntax-repaired report script and REST polling fallback.
- `backend/app.py` — login/session API, incident database, location updates, escalation/cancellation, responder actions, user list and admin audit log.
- `requirements.txt` — backend dependencies.
- `tests/test_api.py` — API smoke/security tests.
- `run_windows.bat` — Windows setup and launch.
- `run_local.sh` — macOS/Linux setup and launch.

## Run locally on Windows

1. Install Python 3.11 or newer.
2. Extract this folder.
3. Open Command Prompt in this folder.
4. Run `run_windows.bat`.
5. Open `http://127.0.0.1:8000`.

Demo accounts (for local prototype testing only):

| Portal | Username | Password |
|---|---|---|
| Admin | `admin` | `admin` |
| Citizen | `citizen` | `citizen` |
| Police | `police` | `police` |
| Hospital | `hospital` | `hospital` |

Change these before any non-demo deployment by setting `JS_ADMIN_PASSWORD`, `JS_CITIZEN_PASSWORD`, `JS_POLICE_PASSWORD`, and `JS_HOSPITAL_PASSWORD` before the first startup. See `DEPLOYMENT.md`; the sample `.env.example` is documentation and is not automatically loaded. These demo defaults are not safe for a public deployment.

## Important design notes

- SQLite is shared by every portal served by this backend on the same host.
- Live incident updates are fetched by the frontend every 3 seconds when no Socket.IO client is loaded.
- Browser GPS requires HTTPS in deployed environments or localhost during development, permission, and working device location services.
- This is a prototype. It records escalation requests but does not dispatch real emergency services, contact police/hospitals, or send SMS/calls. Use official emergency services for real emergencies.
- Before public deployment, add HTTPS, strong secrets, account provisioning/reset, rate limiting, CSRF protection, backup/restore, operational monitoring, and security review. Do not expose the development server directly to the public internet.
