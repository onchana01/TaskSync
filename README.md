 TaskTracker API

TaskTracker is a feature-rich task management API built with Django and Django REST Framework. It offers a robust set of tools for tracking daily activities, including role-based access control, real-time updates, third-party integrations, multi-lingual support, and data visualization capabilities. This project is ideal for developers looking to explore a modern API with advanced features or extend it for personal/team task management.

## Features

- **CRUD Operations**: Create, read, update, and delete tasks via a RESTful API.
- **Role-Based Access Control (RBAC)**: Supports `Admin` (full access) and `Regular User` (own tasks only) roles.
- **Real-Time Updates**: WebSocket integration using Django Channels for instant task change notifications.
- **Task History & Auditing**: Logs all task actions (create, update, delete) for review.
- **Export/Import Tasks**: Export tasks to JSON/CSV and import from these formats for backups or migration.
- **Data Visualization**: Provides task statistics (e.g., completion rates, overdue tasks) for frontend integration (e.g., Chart.js).
- **Third-Party Integrations**:
  - **Google Calendar**: Syncs tasks as events (requires OAuth setup).
  - **Trello**: Adds tasks to a "TaskTracker" board’s "To Do" list.
- **Internationalization (i18n)**: Supports English (`en`), Spanish (`es`), and French (`fr`) with translated responses.
- **Docker/Kubernetes Ready**: Includes groundwork for containerization (extendable).

## Prerequisites

- Python 3.9+
- PostgreSQL (recommended) or SQLite
- Redis (for WebSocket support)
- Git
- Google Cloud account (for Calendar integration)
- Trello account (for Trello integration)

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/tasktracker.git
   cd tasktracker

Set Up Virtual Environment:
bash

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

Install Dependencies:
bash

pip install -r requirements.txt

Configure Environment Variables:
Create a .env file in the root directory:
env

TRELLO_API_KEY=your-trello-api-key
TRELLO_TOKEN=your-trello-token
DB_NAME=tasktracker_db
DB_USER=your_postgres_user
DB_PASSWORD=your_postgres_password
SECRET_KEY=your-secret-key-here

Get Trello credentials from trello.com/app-key.

Set Up Google Calendar:
Create a project in Google Cloud Console.

Enable Calendar API, download credentials.json, and place it in the root directory.

Add your Google email as a test user under OAuth consent screen (Testing mode).

Run the app once to generate token.json via OAuth flow.

Database Setup:
Configure PostgreSQL in settings.py if using (SQLite works by default).

Apply migrations:
bash

python manage.py migrate

Create a superuser:
bash

python manage.py createsuperuser

Start Redis:
Install Redis (e.g., sudo apt-get install redis-server on Ubuntu).

Run:
bash

redis-server &

Compile Translations (for i18n):
bash

python manage.py compilemessages

Run the Server:
bash

python manage.py runserver

API available at http://127.0.0.1:8000/api/.

WebSocket at ws://127.0.0.1:8000/ws/tasks/.

Usage
API Endpoints
GET /api/tasks/: List all tasks (Admin) or user’s tasks (Regular User).

POST /api/tasks/: Create a new task.

GET /api/tasks/<id>/: Retrieve a task.

PUT /api/tasks/<id>/: Update a task.

DELETE /api/tasks/<id>/: Delete a task.

POST /api/tasks/bulk_create/: Create multiple tasks.

GET /api/tasks/history/: View task history.

GET /api/tasks/export/json/: Export tasks as JSON.

GET /api/tasks/export/csv/: Export tasks as CSV.

POST /api/tasks/import/: Import tasks from JSON/CSV.

GET /api/tasks/stats/: Get task statistics.

POST /api/token/: Obtain JWT token.

POST /api/token/refresh/: Refresh JWT token.

Authentication
Use JWT tokens via /api/token/ with username and password.

Include Authorization: Bearer <token> in all API requests.

WebSocket
Test real-time updates with websocket_test.html:
Replace <your-token-here> with a JWT token.

Serve: python -m http.server 8001.

Internationalization
Set Accept-Language header (e.g., es for Spanish, fr for French) to get translated responses.

Testing
Run unit/integration tests:
bash

python manage.py test tasks

Use api.http with VS Code REST Client for manual testing.

Contributing
Fork the repository.

Create a feature branch:
bash

git checkout -b feature-name

Commit changes:
bash

git commit -m "Add feature"

Push to your fork:
bash

git push origin feature-name

Open a Pull Request.

