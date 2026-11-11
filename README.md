# SDI 4213 Week 11 - Cloud Deployment Starter

This repository contains the Help Desk / Service Request Tracker used for the Week 11 individual exercise.

## Week 11 Goal
Deploy the containerized application to a real cloud web service and connect it to a managed PostgreSQL database. The application should be publicly reachable through HTTPS and retain ticket data across application redeployments.

## Local Run

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

macOS/Linux activation:

```bash
source .venv/bin/activate
```

The local version uses SQLite unless `DATABASE_URL` is configured.

## Tests

```bash
python -m pytest -v
```

## Docker

```bash
docker build -t helpdesk-cloud:week11 .
docker run --rm -p 8501:8501 -e DEPLOY_ENV=Local-Docker helpdesk-cloud:week11
```

Open `http://localhost:8501`.

## Cloud Deployment
Follow the Week 11 Individual Exercise document in `docs/`.

## Security
- Do not commit `.env`.
- Do not place database passwords in source code.
- In the cloud dashboard, environment-variable names may be visible in screenshots, but secret values must be hidden.

## UPDATE
## Week 11 Cloud Deployment

The Help Desk application is deployed to Render using Docker.

### Deployment Information
- Cloud Platform: Render
- Application Version: 1.1.0
- Region: Ohio (US East)
- Database: Managed PostgreSQL
- Runtime: Docker
- Public URL: https://YOUR-SERVICE.onrender.com

### Deployment Process
1. Create a feature branch and make changes.
2. Commit and push the changes to GitHub.
3. Open a pull request.
4. Verify GitHub Actions CI passes.
5. Merge the pull request into main.
6. Render deploys the updated application.
7. Verify application health and database persistence.

### Data Persistence
Service requests are stored in managed PostgreSQL,
allowing records to survive web service redeployments.