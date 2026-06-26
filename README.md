# Price Inference Microservice

A simple end-to-end microservice template for deploying machine learning models. This project demonstrates a structured approach to building ML microservices with CI/CD integration, designed as a reference architecture for future ML service development.

**Dataset source:** [Amsterdam Housing Dataset](https://www.kaggle.com/datasets) - apartment price predictions based on property features.

## What it does

Send apartment details (size, bedrooms, year built, parking, etc.) to the API and get back a price prediction using a trained Random Forest model.

## Quick start

```bash
make run
```

This installs dependencies and starts the server on `http://localhost:5000`.

## Using the API

**GET request:**
```
http://localhost:5000/pred/?area=100&construction_year=2020&bedrooms=3&garden_area=50&balcony_present=1&parking_present=1&furnished=0&garage_present=0&storage_present=1
```

**POST request:**
```bash
curl -X POST http://localhost:5000/pred/ \
  -H "Content-Type: application/json" \
  -d '{
    "area": 100,
    "construction_year": 2020,
    "bedrooms": 3,
    "garden_area": 50,
    "balcony_present": 1,
    "parking_present": 1,
    "furnished": 0,
    "garage_present": 0,
    "storage_present": 1
  }'
```

The API will return something like:
```json
{
  "prediction": [450000]
}
```

## Requirements

- Python 3.11+
- Poetry (for dependency management)

## Project structure

- `app/api/` - API endpoints
- `app/services/` - Model inference logic
- `app/model/` - Pre-trained Random Forest model
- `app/schema/` - Input validation schemas
- `app/config/` - Configuration and settings
