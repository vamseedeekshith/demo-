# Deployment notes

## Recommended first deployment
Deploy this package as one FastAPI web service (it serves both `/` and `/api/*`). The existing frontend uses same-origin API paths, so hosting only `static/index.html` on GitHub Pages while the API is on another origin will not work without an API-base/CORS/CSRF configuration change.

## Local Windows run
1. Install Python 3.11+.
2. Extract the ZIP.
3. Copy `.env.example` to `.env` and set strong passwords. The current launcher does not automatically load `.env`; set environment variables in the shell or update the launcher to load them before first startup.
4. Run `run_windows.bat`.
5. Open `http://127.0.0.1:8000`.

## Public deployment checklist
- Use HTTPS and set `JS_COOKIE_SECURE=1`.
- Change all demo passwords before first database initialization. Existing seeded accounts are not automatically rotated by changing environment variables after they already exist.
- Use a managed database/backups for production; SQLite is a single-host prototype database.
- Add CSRF protection, rate limiting, account provisioning/password reset, monitoring, backups, incident retention policy and a security/privacy review.
- Configure a real dispatch integration separately. This API logs escalation requests but does not contact emergency services, hospitals, SMS providers or phone networks.
- Confirm local legal/privacy requirements for location and health data.
