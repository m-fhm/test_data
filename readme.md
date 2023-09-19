
# Resume service 

This service provides a set of APIs to manage resumes. Users can upload resumes, fetch the list of uploaded resumes, and delete specific resumes.

## Prerequisites

1. **Docker & Docker Compose**
2. **AWS account and S3 bucket (for storing resumes)**
3. **AWS credentials (`AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`)**

## Setting up the environment

1. Clone the repository to your local machine.
2. Navigate to the project directory.
3. Create a `.env` file and provide your AWS credentials and S3 bucket name:

```
AWS_ACCESS_KEY_ID=YOUR_AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY=YOUR_AWS_SECRET_ACCESS_KEY
BUCKET_NAME=YOUR_S3_BUCKET_NAME
POSTGRES_USER=Your_BD_USER
POSTGRES_PASSWORD=YOUR_DB_PASS
POSTGRES_DB=YOUR_DB_NAME

```

4. Use Docker Compose to spin up the necessary services:

```bash
docker-compose up --build
```

This command will start the resume service, a PostgreSQL database, and an Nginx instance to handle requests.

## API Endpoints

### 1. Upload a Resume

- **Endpoint**: `/api/v1/postresume/`
- **Method**: `POST`
- **Body**: `multipart/form-data` containing the resume file
- **Response**: JSON containing a message and the ID of the uploaded resume

### 2. List Resumes

- **Endpoint**: `/api/v1/listresume/`
- **Method**: `GET`
- **Response**: JSON array containing the list of uploaded resumes with their IDs and URLs

### 3. Delete a Resume

- **Endpoint**: `/api/v1/deleteresume/{resume_id}`
- **Method**: `DELETE`
- **URL Params**: `resume_id` (ID of the resume to delete)
- **Response**: JSON containing a message indicating the result of the deletion

## Accessing the APIs using Postman

1. Launch Postman.
2. Set the appropriate HTTP method (GET, POST, DELETE) based on the API you want to test.
3. For the URL, use `http://localhost:8081` followed by the specific endpoint (e.g., `/api/v1/postresume/`) as whole it will look like 'http://127.0.0.1:8001/api/v1/postresume'.
4. For uploading a resume, select the "Body" tab in Postman, choose "form-data", and attach your resume file with the key "resume".
5. Send the request and check the response.
