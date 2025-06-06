---
layout: post
title: "Building an End-to-End MLOps Pipeline for Text Classification"
subtitle: "From data ingestion to model monitoring in production"
date: 2024-12-07 14:00:00
tags: [project, mlops, pipeline, aws, docker, kubernetes, monitoring]
comments: true
author: Omid Sar
---

This is a **sample project showcase template** - a reference for presenting completed ML projects.

## Project Overview

**Problem Statement**: Build a scalable text classification system that can handle high-volume real-time predictions while maintaining model performance and providing monitoring capabilities.

**Solution**: End-to-end MLOps pipeline using modern cloud-native tools and practices.

**Tech Stack**: 
- **ML**: PyTorch, Hugging Face Transformers, scikit-learn
- **MLOps**: MLflow, DVC, Kubeflow
- **Infrastructure**: AWS (EKS, S3, RDS), Docker, Kubernetes
- **Monitoring**: Prometheus, Grafana, Evidently AI
- **CI/CD**: GitHub Actions, ArgoCD

## Architecture Overview

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Data Sources  │───▶│  Data Pipeline  │───▶│  Feature Store  │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                                                        │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Monitoring    │◀───│  Model Serving  │◀───│  Model Training │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## Key Features

### 🚀 **Automated Training Pipeline**
- Automatic data validation and preprocessing
- Hyperparameter optimization with Optuna
- Model versioning and experiment tracking
- Automated model evaluation and validation

### 🔄 **Continuous Deployment**
- GitOps-based deployment with ArgoCD
- Blue-green deployment strategy
- Automated rollback on performance degradation
- Environment promotion (dev → staging → prod)

### 📊 **Real-time Monitoring**
- Model performance metrics (accuracy, latency, throughput)
- Data drift detection using statistical tests
- Business metrics tracking
- Alert system for anomalies

### 🔧 **Infrastructure as Code**
- Kubernetes manifests for all services
- Terraform for AWS infrastructure
- Helm charts for application deployment
- Environment-specific configurations

## Implementation Details

### Data Pipeline

```python
# data_pipeline/processor.py
from typing import Dict, List
import pandas as pd
from sklearn.model_selection import train_test_split

class DataProcessor:
    def __init__(self, config: Dict):
        self.config = config
        
    def load_raw_data(self) -> pd.DataFrame:
        """Load data from multiple sources"""
        # Implementation for data loading
        pass
        
    def validate_data(self, df: pd.DataFrame) -> bool:
        """Validate data quality and schema"""
        # Data validation logic
        pass
        
    def preprocess(self, df: pd.DataFrame) -> pd.DataFrame:
        """Clean and preprocess the data"""
        # Preprocessing steps
        pass
        
    def create_features(self, df: pd.DataFrame) -> pd.DataFrame:
        """Feature engineering pipeline"""
        # Feature creation logic
        pass
```

### Model Training

```python
# training/trainer.py
import mlflow
from transformers import AutoTokenizer, AutoModelForSequenceClassification
from transformers import TrainingArguments, Trainer

class ModelTrainer:
    def __init__(self, config: Dict):
        self.config = config
        
    def setup_experiment(self):
        """Setup MLflow experiment tracking"""
        mlflow.set_experiment(self.config['experiment_name'])
        
    def train(self, train_data, val_data):
        """Train the model with experiment tracking"""
        with mlflow.start_run():
            # Model training code
            # Log parameters, metrics, and artifacts
            pass
            
    def evaluate(self, test_data):
        """Comprehensive model evaluation"""
        # Evaluation metrics calculation
        pass
```

### Model Serving

```python
# serving/api.py
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel
import torch
from transformers import pipeline

app = FastAPI(title="Text Classification API")

class PredictionRequest(BaseModel):
    text: str
    
class PredictionResponse(BaseModel):
    label: str
    confidence: float
    latency_ms: float

@app.post("/predict", response_model=PredictionResponse)
async def predict(request: PredictionRequest):
    """Make prediction with monitoring"""
    start_time = time.time()
    
    try:
        # Model inference
        result = model(request.text)
        latency = (time.time() - start_time) * 1000
        
        # Log metrics
        metrics_logger.log_prediction(
            input_length=len(request.text),
            confidence=result['confidence'],
            latency=latency
        )
        
        return PredictionResponse(
            label=result['label'],
            confidence=result['confidence'],
            latency_ms=latency
        )
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))
```

## Deployment Configuration

### Kubernetes Deployment

```yaml
# k8s/deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: text-classifier
spec:
  replicas: 3
  selector:
    matchLabels:
      app: text-classifier
  template:
    metadata:
      labels:
        app: text-classifier
    spec:
      containers:
      - name: api
        image: text-classifier:latest
        ports:
        - containerPort: 8000
        env:
        - name: MODEL_VERSION
          value: "v1.2.0"
        resources:
          requests:
            memory: "1Gi"
            cpu: "500m"
          limits:
            memory: "2Gi"
            cpu: "1000m"
        livenessProbe:
          httpGet:
            path: /health
            port: 8000
          initialDelaySeconds: 30
          periodSeconds: 10
```

### CI/CD Pipeline

```yaml
# .github/workflows/deploy.yml
name: Deploy ML Pipeline

on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run tests
      run: |
        python -m pytest tests/
        
  build-and-deploy:
    needs: test
    runs-on: ubuntu-latest
    steps:
    - name: Build Docker image
      run: |
        docker build -t text-classifier:${{ github.sha }} .
        
    - name: Deploy to staging
      run: |
        kubectl apply -f k8s/staging/
        
    - name: Run integration tests
      run: |
        python -m pytest tests/integration/
        
    - name: Deploy to production
      if: success()
      run: |
        kubectl apply -f k8s/production/
```

## Monitoring and Observability

### Key Metrics Tracked

1. **Model Performance**
   - Prediction accuracy: 94.2% (target: >90%)
   - Average latency: 45ms (target: <100ms)
   - Throughput: 1000 requests/minute

2. **Infrastructure Health**
   - CPU utilization: 65% average
   - Memory usage: 1.2GB average
   - Pod restarts: 0 in last 7 days

3. **Business Metrics**
   - Daily prediction volume: 50k requests
   - User satisfaction: 4.6/5.0
   - Cost per prediction: $0.002

### Alerting Rules

```yaml
# monitoring/alerts.yml
groups:
- name: ml-model-alerts
  rules:
  - alert: ModelAccuracyDrop
    expr: model_accuracy < 0.85
    for: 5m
    annotations:
      summary: "Model accuracy dropped below threshold"
      
  - alert: HighLatency
    expr: avg_response_time > 200
    for: 2m
    annotations:
      summary: "API response time is too high"
```

## Results and Impact

### Performance Metrics
- **Accuracy**: 94.2% on test set (2% improvement over baseline)
- **Latency**: 45ms average response time (60% faster than previous system)
- **Availability**: 99.9% uptime over 3 months
- **Cost**: 40% reduction in infrastructure costs

### Business Impact
- **Automated**: 85% of classification tasks (previously manual)
- **Scalability**: Handle 10x traffic increase without degradation
- **Reliability**: Zero data loss incidents since deployment
- **Developer Experience**: 70% faster model iteration cycle

## Lessons Learned

### What Worked Well
1. **Infrastructure as Code**: Made deployments reproducible and reliable
2. **Comprehensive Monitoring**: Early detection of issues prevented outages
3. **Automated Testing**: Caught regressions before production deployment
4. **Feature Store**: Consistent features across training and serving

### Areas for Improvement
1. **Data Drift Detection**: Need more sophisticated drift detection algorithms
2. **A/B Testing**: Implement framework for gradual model rollouts
3. **Cost Optimization**: Better resource allocation during off-peak hours
4. **Documentation**: Improve operational runbooks and troubleshooting guides

## Future Enhancements

- **Multi-model Serving**: Support for ensemble predictions
- **Real-time Training**: Implement online learning capabilities
- **Edge Deployment**: Deploy lightweight models to edge devices
- **Advanced Monitoring**: Add explainability and bias detection

## Resources and Links

- **Code Repository**: [GitHub Link](https://github.com/omid-sar/text-classification-mlops)
- **Live Demo**: [Demo Application](https://demo.text-classifier.com)
- **Documentation**: [Technical Docs](https://docs.text-classifier.com)
- **Monitoring Dashboard**: [Grafana Dashboard](https://monitoring.text-classifier.com)

---

*This project showcases a production-ready MLOps pipeline with modern best practices. The system handles thousands of daily predictions with high reliability and performance.* 