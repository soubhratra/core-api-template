
# core-api-template

core-api-template is a Django-based Rest API template repository that includes basic set up for a django ninja extra project to run standalone or inside a Docker container. It also includes dependencies line langchain and langgraphs which can be removed when not needed.

## Features
- Built with Django and Django Ninja Extra.
- Integrates AI libraries like `langchain`, `langsmith`, and `langgraph`.
- Easily deployable using Docker.

---

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- [Python 3.11](https://www.python.org/downloads/release/python-3110/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- Git

---

## Getting Started

Follow these steps to clone and run the project:

### 1. Clone the Repository
```bash
git clone https://github.com/soubhratra/core-api-template.git core-api-template
cd core-api-template
```
---

### 2. Set Up Environment Variables

Copy `.env.sample` file to create a `.env` file in the project root with the following content:

```plaintext
SECRET_KEY=your-secure-secret-key
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
```
---

### 3. Run locally

#### Create virtual env
```bash
python3.11 -m venv venv
source venv/bin/activate
```
#### Prerequisite
You may need to have wheel installed locally
https://wheel.readthedocs.io/en/stable/installing.html

#### Install dependencies
```bash
pip install -r requirements.txt
```

# Download the required spaCy model
python -m spacy download en_core_web_sm
```

#### Run Django server
```bash
python manage.py runserver
```

### 4. Optionally Build and Run with Docker

#### Build the Docker Image
```bash
docker compose build
```

#### Run the Application
```bash
docker compose up
```
---

### 5. Access the Application

Once the container is running, open your browser and go to:
```
http://localhost:8000
```

---

### 6. Stopping the Application

To stop the application, press `Ctrl+C` in the terminal where it is running, if running as docker, then shut down the Docker container:
```bash
docker compose down
```

---

### 6. Running Migrations (Optional)

If the database structure changes or migrations need to be applied, run the following command inside the container:
```bash
docker-compose run app python manage.py migrate
```
For the projects, that are not using Django ORM to connect to a database, diable the database management in the settings.py

---

## Troubleshooting

### Common Issues
1. **Port Already in Use**  
   If port `8000` is already in use, update the `docker-compose.yml` file to use a different port:
   ```yaml
   ports:
     - "8000:8000"  # Change this to "8080:8000" or any other port
   ```

2. **Database Errors**  
   Ensure you have run migrations:
   ```bash
   docker-compose run app python manage.py migrate
   ```

3. **Environment Variables Missing**  
   Ensure the `.env` file exists and contains all necessary variables.

---

## Contributing

If you'd like to contribute, please fork the repository and submit a pull request.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
