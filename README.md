# Flask User Auth App with Signup/Login and SQLite

This is a simple Flask web application that supports user signup, login, logout, and a decorative welcome page with a user avatar. It uses SQLite for storing user credentials and password hashing for security. The app is Dockerized and served using Gunicorn for production.

---

## Features

- User Signup with unique username and hashed passwords  
- User Login with session management  
- Logout functionality  
- SQLite database with SQLAlchemy ORM  
- Decorative welcome page with user avatar and CSS styling  
- Docker containerization with Gunicorn  
- Static file serving (for user avatar image)

---


## Getting Started

### Prerequisites

- Docker installed on your machine  
- (Optional) Python 3.9+ for local runs without Docker

---

### Running with Docker

1. Build the Docker image (force no-cache to get latest files):

   ```bash
   docker build --no-cache -t pythonapp .

2. Run the container:
   
   docker run -p 8080:8000 pythonapp

3. Open your browser and visit:
   
   http://localhost:8080
