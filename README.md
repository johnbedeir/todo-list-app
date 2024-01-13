# Todo List | Python - MySQL App

<div align=center>
<img src=cover.png width=200>
</div>

This is a simple Python Flask application that performs CRUD operations on a MySQL database, the project contains Docker and Docker Compose files for running the Python application with Mysql Database Locally.

## Prerequisites

Before you begin, ensure you have met the following requirements:

- [Python](https://www.python.org/downloads/)
- [MySQL For Ubuntu](https://dev.mysql.com/downloads/repo/apt/) | [MySQL For Windows](https://dev.mysql.com/downloads/installer/)
- [Docker](https://docs.docker.com/engine/install/) installed and configured
- [Beekeeper-Studio](https://www.beekeeperstudio.io/) `For Database Access`

## 1. Running the Application Locally

### Setting Up the Database

1. Start your MySQL server.
2. Create a new MySQL database for the application.
3. Update the database configuration in `app.py` to match your local MySQL settings:

   - DB_HOST: localhost
   - DB_USER: your MySQL username
   - DB_PASSWORD: your MySQL password
   - DB_DATABASE: your database name

4. Create a table in the database that will be used by your application
   ```
   CREATE TABLE tasks (
   id SERIAL PRIMARY KEY,
   title VARCHAR(255) NOT NULL,
   description TEXT,
   is_complete BOOLEAN DEFAULT false
   );
   ```

### Running the App

1. Clone the repository:

   ```
   git clone https://github.com/johnbedeir/End-to-end-DevOps-Python-MySQL
   cd End-to-end-DevOps-Python-MySQL/todo-app
   ```

2. Create a virtual environment and activate it:

   ```
   python3 -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required dependencies:

   ```
   pip3 install -r requirements.txt
   ```

4. Start the Flask application:

   ```
   python3 app.py
   ```

5. Access the application at `http://localhost:5000`.

## 2. Running with Docker (Optional)

1. Build the Docker image:

   ```
   docker build -t my-flask-app .
   ```

2. Run the Docker container with host network (to access the local MySQL server):

   ```
   docker run --network=host my-flask-app
   ```

3. Access the application at `http://localhost:5000`.

## 3. Running App and Database with Docker compose (Optional)

To run the application using docker compose:

```
docker-compose up
```

This will Run both the application and the database containers and will also create a table in the database using the sql script `init-db.sql`

To take it down run the following command:

```
docker-compose down
```
