# 🤖 Distributed Transformers Training with HuggingFace, Accelerate & SageMaker

This repository contains a fully containerized training pipeline to fine-tune **HuggingFace Transformers** models on distributed GPUs using **SageMaker** and **Accelerate**. It loads datasets from **S3**, performs validation, training, evaluation, and saves outputs back to S3.

---

## 🚀 Features

- Multi-GPU distributed training with `accelerate`
- Uses `transformers`, `datasets`, `scikit-learn`, and `boto3`
- Custom Docker image deployable to SageMaker
- Validates HuggingFace datasets before training
- Uploads trained models and logs to Amazon S3
- Compatible with SageMaker Estimator API

---

## 🐳 Docker Image

Build and push your image to Amazon ECR:

```bash
docker build -t proyecto_2_distributed .
aws ecr get-login-password | docker login --username AWS --password-stdin <your-ecr-repo>
docker tag proyecto_2_distributed:latest <your-ecr-uri>:latest
docker push <your-ecr-uri>:latest
```

## ☁️ Launch Training in SageMaker

Update launch_distributed_training.py with your role, region, and ECR image URI:

```bash
python launch_distributed_training.py
```

---
