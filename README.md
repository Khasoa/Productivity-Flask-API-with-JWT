# Productivity Task API with JWT

A full-stack productivity project built with a Flask backend API and a React frontend client using JWT authentication. Users can register, log in securely, stay authenticated after refresh, and manage personal tasks through protected API endpoints.

This project demonstrates backend authentication, authorization, RESTful API design, frontend integration, and secure user-owned resource management.

---

## Project Structure

- `backend/` – Flask API, models, routes, migrations, tests, and seed data  
- `client-with-jwt/` – React frontend client  
- `README.md` – Main project documentation  

---

## Features

### Authentication

- User signup  
- User login  
- JWT token authentication  
- Persistent login using stored token  
- Protected routes  

### Task Management

Each user can only manage their own tasks.

- Create tasks  
- View tasks  
- View one task  
- Update tasks  
- Delete tasks  
- Paginated task listing  

### Security

- Passwords hashed with bcrypt  
- JWT required for task routes  
- Users cannot access another user's tasks  
- Ownership enforced on backend  

---

## Tech Stack

### Backend

- Python 3.8+
- Flask
- Flask-SQLAlchemy
- Flask-Migrate
- Flask-Bcrypt
- Flask-JWT-Extended
- Marshmallow
- Faker
- Pytest

### Frontend

- React
- JavaScript
- Fetch API
- localStorage

---

## How the Application Works

### Signup Flow

The frontend sends a username and password to `/signup`.  
The backend hashes the password, creates the user, generates a JWT token, and returns both the user and token.

### Login Flow

The frontend sends credentials to `/login`.  
If valid, the backend returns a JWT token.

### Persistent Sessions

The frontend stores the token in localStorage.  
On refresh, it sends the token to `/me` to keep the user logged in.

### Task Ownership

Every task request uses the JWT token identity.  
Only the logged-in user's tasks are returned.

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
2. Backend Setup
cd backend
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
3. Create Environment Variables

Inside the backend/ folder, create a .env file:

SECRET_KEY=your-secret-key
JWT_SECRET_KEY=your-jwt-secret-key

Generate secure values:

python -c "import secrets; print(secrets.token_hex(32))"
Database Setup

Inside the backend/ folder run:

export FLASK_APP=run.py
flask db init
flask db migrate -m "initial migration"
flask db upgrade
python seed.py

This creates the database and inserts sample data.

Running the Backend
flask run

or

python run.py

Backend URL:

http://localhost:5555
Running the Frontend

Open a new terminal:

cd client-with-jwt
npm install
npm start

Frontend URL:

http://localhost:3000
Connecting Frontend to Backend

If needed, add this to the frontend package.json:

"proxy": "http://localhost:5555"
API Endpoints
Authentication
Method	Endpoint	Description
POST	/signup	Register new user
POST	/login	Login user
GET	/me	Get current user
Tasks
Method	Endpoint	Description
GET	/tasks?page=1	Get paginated tasks
GET	/tasks/<id>	Get one task
POST	/tasks	Create task
PATCH	/tasks/<id>	Update task
DELETE	/tasks/<id>	Delete task
Example Requests
Signup
{
  "username": "lydia",
  "password": "mypassword"
}
Create Task
{
  "title": "Finish project",
  "description": "Submit by Friday",
  "priority": "High"
}

Authenticated requests require:

Authorization: Bearer <token>
Running Tests

Inside the backend folder:

pytest tests/ -v

Tests include:

Signup
Login
/me
CRUD operations
Pagination
Unauthorized access
Cross-user protection
Seed Data
python seed.py

Creates:

3 users
5 tasks each

Default password:

password123
Why This Project Matters

This project demonstrates:

Secure authentication systems
REST API architecture
Database relationships
Frontend/backend integration
Authorization logic
Testing
Professional project organization
Author

Lydia Khasoa

License

Educational use and portfolio demonstration.