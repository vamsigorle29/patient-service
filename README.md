# Patient Service

Microservice for managing patient information in the Hospital Management System.

## Overview

The Patient Service provides CRUD operations for patient data with PII masking in logs, API versioning, and OpenAPI documentation.

## Features

- ✅ Full CRUD operations for patients
- ✅ Search by name/phone
- ✅ PII masking in logs (email, phone, name)
- ✅ API version `/v1`
- ✅ OpenAPI 3.0 documentation at `/docs`
- ✅ Standard error schema with correlation ID
- ✅ Pagination support (`skip`, `limit`)
- ✅ Filtering support

## Quick Start

### Prerequisites

- Python 3.8+
- pip

### Installation

```bash
pip install -r requirements.txt
```

### Running Locally

```bash
python app.py
```

The service will start on `http://localhost:8001`

### Using Docker

```bash
docker build -t patient-service:latest .
docker run -p 8001:8001 patient-service:latest
```

### Using Docker Compose

```bash
docker-compose up
```

## API Documentation

Once the service is running, visit:
- Swagger UI: http://localhost:8001/docs
- ReDoc: http://localhost:8001/redoc

## Endpoints

- `GET /v1/patients` - List all patients (with pagination and filtering)
- `GET /v1/patients/{patient_id}` - Get patient by ID
- `POST /v1/patients` - Create a new patient
- `PUT /v1/patients/{patient_id}` - Update patient
- `DELETE /v1/patients/{patient_id}` - Delete patient
- `GET /v1/patients/{patient_id}/exists` - Check if patient exists
- `GET /health` - Health check endpoint

## Environment Variables

- `PORT` - Service port (default: 8001)
- `DATABASE_URL` - Database connection string (default: sqlite:///./patient.db)

## Kubernetes Deployment

```bash
kubectl apply -f k8s/deployment.yaml
```

## Database Schema

**Patients Table:**
- `patient_id` (Integer, Primary Key)
- `name` (String)
- `email` (String, Unique)
- `phone` (String)
- `dob` (Date)
- `created_at` (DateTime)

## PII Masking

The service automatically masks PII in logs:
- Email: `jo***@example.com`
- Phone: `12***90`
- Name: `Jo***`

## Contributing

This is part of a microservices architecture. For integration with other services, see the main Hospital Management System documentation.

## License

Academic use only.

