# Credit Card Fraud Detection System


## Overview

A comprehensive machine learning solution for detecting fraudulent credit card transactions in real-time. This project features a FastAPI backend and Streamlit frontend for seamless fraud detection.

## 🎯 Key Features

- **Machine Learning Model** - Advanced fraud detection classifier
- **FastAPI Backend** - High-performance REST API
- **Streamlit Frontend** - Interactive web interface
- **Docker Support** - Easy containerized deployment
- **Real-time Detection** - Instant fraud classification
- **Batch Processing** - Process multiple transactions at once
- **API Documentation** - Interactive Swagger UI and ReDoc

## 📋 Prerequisites

- Python 3.8 or higher
- Docker & Docker Compose (optional)
- pip package manager


## 📁 Project Structure

```
Credit-Card-Fraud-Detection-main/
├── backend/              # FastAPI backend service
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
├── frontend/             # Streamlit frontend
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
├── Notebook/             # Jupyter analysis notebook
├── README/               # Documentation
│   ├── README.md
│   ├── INSTALLATION.md
│   ├── USAGE.md
│   ├── API_DOCUMENTATION.md
│   └── PROJECT_STRUCTURE.md
└── docker-compose.yml    # Container orchestration
```

## 🔧 Technologies Used

| Component | Technology |
|-----------|-----------|
| Backend | FastAPI, Uvicorn |
| Frontend | Streamlit |
| ML Framework | Scikit-learn |
| Data Processing | Pandas, NumPy, SciPy |
| Containerization | Docker, Docker Compose |
| Server | Gunicorn, Uvloop |

## 💾 Dependencies

### Backend Requirements
- fastapi==0.68.0
- uvicorn==0.14.0
- pandas==1.3.1
- scikit-learn==1.0.2
- numpy==1.21.6
- pydantic==1.9.1
- joblib==1.0.1

### Frontend Requirements
- streamlit==1.10.0
- numpy==1.21.6
- requests==2.23.0

## 🎮 Usage

### Web Interface

1. Open http://localhost:8501
2. Enter transaction details:
   - Hour (0-23)
   - Amount
   - Transaction type
   - Additional features
3. Click "Predict"
4. View fraud classification and confidence score

### API Integration

**Check API Status:**
```bash
curl http://localhost:8000/
```

**Make Single Prediction:**
```bash
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{
    "hour": 14,
    "amount": 100.50,
    "type": "online"
  }'
```

**Batch Processing:**
```bash
curl -X POST "http://localhost:8000/predict/file" \
  -F "file=@transactions.csv"
```


## 🤖 Model Details

- **Type**: Binary Classification (Fraud/Legitimate)
- **Algorithm**: Scikit-learn Classifier
- **Input Features**: Transaction characteristics
  - Hour of transaction
  - Amount
  - Transaction type
  - Additional metadata
- **Output**: Classification + Confidence score

## 📊 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | API information |
| POST | `/predict` | Single transaction prediction |
| POST | `/predict/file` | Batch prediction from CSV |
| GET | `/docs` | Swagger UI documentation |
| GET | `/redoc` | ReDoc documentation |

## 🐳 Docker Commands

```bash
# Build and run
docker-compose up --build

# Run in background
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f

# Rebuild specific service
docker-compose build backend
```

## 🔍 Troubleshooting

### Port Already in Use
```bash
# Kill process on port 8000
lsof -ti:8000 | xargs kill -9

# Run on different port
streamlit run frontend/app.py --server.port 8502
```

### Model Not Found
Ensure `credit_fraud.pkl` exists in the backend directory.

### Dependencies Issues
```bash
# Clear cache and reinstall
pip install --upgrade --force-reinstall -r requirements.txt
```

### Docker Build Fails
```bash
docker-compose down
docker system prune
docker-compose up --build
```

## 📈 Performance

- **Backend**: Processes predictions in milliseconds
- **Frontend**: Real-time response via Streamlit
- **Scalability**: Docker containers allow horizontal scaling
- **Batch Processing**: Handle thousands of transactions efficiently

## 🔐 Security Features

- Input validation via Pydantic
- Error handling prevents information leakage
- Model protection (serialized format)
- Can integrate authentication (recommended for production)

