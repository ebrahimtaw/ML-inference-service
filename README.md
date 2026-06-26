# Price Inference Microservice

I've built this simple service project so that future complex ML microservices could use this structured microservice approach. This microservice is local with end-to-end Continuous Integration that even builds the model when not present.

**Dataset source:** [Amsterdam Housing Dataset](https://www.kaggle.com/datasets) - apartment price predictions based on property features.

## What it does

Send apartment details (size, bedrooms, year built, parking, etc.) to the API and get back a price prediction using the Random Forest model.

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
