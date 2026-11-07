<div align="center">

# 🔮 OptiVision AI

### Intelligent Video Analytics & Real-Time Surveillance Platform

*Next-generation computer vision system for automated object detection, intelligent tracking, and predictive event analytics with edge-optimized inference.*

[![Python 3.12+](https://img.shields.io/badge/Python-3.12+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![YOLO](https://img.shields.io/badge/YOLO-v8-00FFFF?style=flat-square)](https://github.com/ultralytics/ultralytics)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.140+-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](./LICENSE)

**Developed by [Keshav](https://github.com/keshav) • 2026**

</div>

---

## 🌟 Overview

**OptiVision AI** is an enterprise-grade video analytics platform that transforms traditional surveillance into intelligent monitoring. Built to handle real-world production challenges: continuous video processing, advanced object detection, persistent identity tracking, spatial analytics, automated event generation, and deployment optimization.

### ✨ What Sets OptiVision AI Apart

More than a simple detection demo, OptiVision AI is a **complete intelligent surveillance ecosystem**:

- 🧩 **Modular Architecture**: Plug-and-play detection backends and tracking algorithms
- 🎯 **Smart Analytics Engine**: Zone monitoring, boundary detection, temporal analysis, and safety alerts
- ⚡ **Performance Optimized**: ONNX, OpenVINO FP16/INT8 quantization pipelines
- 🌐 **Production APIs**: RESTful endpoints with live MJPEG streaming
- 🐳 **Enterprise Ready**: Docker orchestration with multi-camera support
- 🧪 **Test-Driven**: Complete synthetic dataset for CI/CD validation

---

## 🎬 System Architecture

```text
📹 Input Stream (RTSP / Video / Webcam)
        │
        ▼
   🎞️ Frame Processing Engine
        │
        ▼
 🎯 Object Detection Layer ────────── Test Backend (Synthetic)
        │                              Production Backend (YOLO)
        ▼
 🔍 Multi-Target Tracking ──────────── Centroid Tracker (Testing)
        │                              ByteTrack (Production)
        ▼
 ⚡ Intelligence & Analytics
   ├─ Spatial zone monitoring
   ├─ Temporal dwell analysis
   ├─ Boundary crossing detection
   └─ Proximity-based safety alerts
        │
        ▼
 🌐 API Gateway + Live Dashboard + Telemetry
        │
        ▼
 🚀 Optimized Deployment Pipeline
```

---

## 🚀 Core Capabilities

### 🎯 **Detection & Tracking**
- ✅ Interchangeable detection engines (synthetic + YOLO)
- ✅ Flexible tracking systems (centroid + ByteTrack)
- ✅ Pre-configured YOLO dataset for immediate testing
- ✅ Built-in dataset validation toolkit

### 📊 **Analytics & Intelligence**
- ✅ Zone-based entry/exit detection with dwell metrics
- ✅ Virtual boundary crossing analytics
- ✅ Collision avoidance and near-miss alerting
- ✅ Trajectory path visualization
- ✅ Annotated video output generation

### 🌐 **API & Visualization**
- ✅ FastAPI with auto-generated OpenAPI docs
- ✅ Real-time MJPEG video streaming
- ✅ Multi-camera concurrent processing
- ✅ Live metrics and event broadcasting

### ⚡ **Optimization & Performance**
- ✅ PyTorch to ONNX model conversion
- ✅ OpenVINO export (FP32/FP16/INT8)
- ✅ Neural Network Compression Framework (NNCF)
- ✅ Comprehensive latency benchmarking
- ✅ CPU optimization strategies

### 🛠️ **DevOps & Quality**
- ✅ Multi-stage Docker builds
- ✅ CI/CD with GitHub Actions
- ✅ Full test coverage
- ✅ IDE integration (PyCharm)

---

## ⚡ Quick Start Guide

### Prerequisites
- Python 3.12+
- Virtual environment recommended

### 1️⃣ Clone & Environment Setup

```powershell
# Clone repository
git clone <your-repo-url>
cd optivision-ai

# Create and activate virtual environment
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1

# Update pip
python -m pip install --upgrade pip
```

### 2️⃣ Install Dependencies

**Complete computer vision stack:**
```powershell
pip install -r requirements.txt
```

**Quick demo mode only:**
```powershell
pip install -r requirements-demo.txt
```

### 3️⃣ Verify Installation

```powershell
pytest
```

### 4️⃣ Run Demo Pipeline

```powershell
python -m visionguard demo --source datasets/demo/demo_scene.mp4
```

**Output:** `outputs/demo_annotated.mp4`

### 5️⃣ Launch Live System

```powershell
python -m visionguard serve
```

**Access Points:**
- **Dashboard:** http://127.0.0.1:8000
- **API Documentation:** http://127.0.0.1:8000/docs

Click **Start demo** to view real-time annotated video with live analytics!

---

## 📦 Included Dataset

OptiVision AI ships with a synthetic validation dataset:

```text
datasets/demo/
├── images/
│   ├── train/          # Training images
│   └── val/            # Validation images
├── labels/
│   ├── train/          # YOLO format annotations
│   └── val/            # YOLO format annotations
├── dataset.yaml        # Dataset configuration
└── demo_scene.mp4      # Sample video
```

### Object Classes

| ID | Class | Use Case |
|---:|:------|:---------|
| 0 | person | Pedestrian tracking, loitering detection |
| 1 | forklift | Industrial safety monitoring |
| 2 | car | Vehicle tracking, parking management |

### Validate Dataset Integrity

```powershell
python training/dataset_validator.py --data datasets/demo/dataset.yaml
```

> **Note:** This synthetic dataset ensures reproducible testing. For production deployment, integrate domain-specific real-world data with manual annotation review.

---

## 🎓 Custom Model Training

```powershell
# Train custom detection model
python training/train.py ^
  --model yolo26n.pt ^
  --data datasets/demo/dataset.yaml ^
  --epochs 50 ^
  --device cpu
```

```powershell
# Evaluate trained checkpoint
python training/evaluate.py ^
  --model runs/train/visionguard/weights/best.pt ^
  --data datasets/demo/dataset.yaml
```

**Metrics reported:** Precision, Recall, F1-Score, mAP@50, mAP@50-95

---

## 🔌 Production Configuration

Edit `configs/cameras.yaml` for live deployment:

```yaml
cameras:
  - id: warehouse_cam_01
    source: rtsp://user:password@192.168.1.100/stream
    backend: yolo
    tracker: bytetrack
    model: models/best.pt
    confidence: 0.35
    device: cpu
    enabled: true
```

---

## ⚙️ Analytics Rules

Configure zones and detection rules in `configs/analytics.yaml`:

```yaml
zones:
  - name: restricted_area
    points:
      - [360, 80]
      - [610, 80]
      - [610, 330]
      - [360, 330]
    classes: [person]
    dwell_seconds: 2.0
```

---

## 🚀 Model Export & Optimization

### ONNX Export

```powershell
# Standard precision
python optimization/export_onnx.py --model runs/train/visionguard/weights/best.pt

# Half precision
python optimization/export_onnx.py --model runs/train/visionguard/weights/best.pt --quantize 16
```

### OpenVINO Export

```powershell
# FP32 (full precision)
python optimization/export_openvino.py --model runs/train/visionguard/weights/best.pt

# FP16 (half precision)
python optimization/export_openvino.py --model runs/train/visionguard/weights/best.pt --quantize 16

# INT8 (8-bit quantization with calibration)
python optimization/export_openvino.py ^
  --model runs/train/visionguard/weights/best.pt ^
  --quantize 8 ^
  --data datasets/demo/dataset.yaml
```

---

## 📊 Performance Benchmarking

Measure and compare model performance across formats:

```powershell
python optimization/benchmark.py ^
  --model path/to/model ^
  --source datasets/demo/demo_scene.mp4 ^
  --frames 200 ^
  --output benchmarks/result.json
```

**Benchmark Metrics:**
- Mean & P95 latency
- Frames per second (FPS)
- Precision format
- mAP scores
- Hardware utilization

---

## 🌐 REST API Reference

| Method | Endpoint | Description |
|:------:|:---------|:------------|
| **GET** | `/health` | Health check & version info |
| **GET** | `/api/v1/cameras` | List camera configurations |
| **POST** | `/api/v1/cameras/{id}/start` | Activate camera worker |
| **POST** | `/api/v1/cameras/{id}/stop` | Deactivate camera worker |
| **GET** | `/api/v1/cameras/{id}/mjpeg` | Live video stream |
| **GET** | `/api/v1/events` | Query analytics events |
| **GET** | `/api/v1/metrics` | System performance metrics |
| **GET** | `/api/v1/models` | List available models |
| **WS** | `/ws/events` | WebSocket event stream |

**Interactive Documentation:** http://127.0.0.1:8000/docs

---

## 📁 Project Structure

```text
OptiVision-AI/
├── 📂 src/visionguard/      # Core application
│   ├── analytics/            # Event processing engine
│   ├── detection/            # Object detection backends
│   ├── tracking/             # Target tracking systems
│   ├── api.py                # FastAPI server
│   ├── cli.py                # Command-line interface
│   ├── config.py             # Configuration loader
│   ├── demo.py               # Demo mode
│   ├── domain.py             # Data models
│   ├── factory.py            # Component factory
│   ├── pipeline.py           # Processing pipeline
│   ├── rendering.py          # Video annotation
│   └── runtime.py            # Multi-camera runtime
├── 📂 training/              # Model training toolkit
├── 📂 optimization/          # Export & benchmarks
├── 📂 datasets/              # Training data
├── 📂 configs/               # System configuration
├── 📂 models/                # Model checkpoints
├── 📂 benchmarks/            # Performance results
├── 📂 tests/                 # Test suite
├── 📂 web/                   # Web dashboard
├── 📂 .github/workflows/     # CI/CD automation
├── 🐳 Dockerfile             # Container definition
├── 🐳 docker-compose.yml     # Service orchestration
└── 📄 pyproject.toml         # Package metadata
```

---

## 🐳 Docker Deployment

```bash
docker compose up --build
```

**Access dashboard:** http://localhost:8000

---

## 🧪 Quality Assurance

OptiVision AI includes:
- ✅ Comprehensive test suite
- ✅ End-to-end validation pipeline
- ✅ Automated CI/CD workflows
- ✅ Python 3.12 & 3.13 compatibility

Detailed testing documentation: [`TESTING.md`](TESTING.md)

---

## 🎯 Production Readiness Roadmap

1. ✨ Integrate production-grade dataset with ground truth
2. 📊 Execute complete model training with experiment tracking
3. 🔍 Perform systematic error analysis (FP/FN investigation)
4. ⚡ Deploy optimized models (OpenVINO INT8)
5. 📈 Conduct hardware benchmark comparisons
6. 🎥 Test with live RTSP camera feeds
7. 📐 Implement pixel-to-world coordinate calibration
8. 💾 Add persistent storage and access control
9. 🔒 Implement enterprise security measures

---

## ⚙️ Technical Specifications

- **Python Version:** `>=3.12, <3.15`
- **OpenVINO:** Fixed at `2026.2.1`
- **Model Storage:** Not version controlled
- **Credentials:** Externalized configuration
- **Test Backend:** Deterministic for CI/CD
- **Safety Systems:** Portfolio demonstration only

---

## 📜 License

Licensed under the **MIT License**

Copyright © 2026 **Keshav**

Full license text: [LICENSE](./LICENSE)

---

## 🙏 Technology Stack

Powered by:
- [Ultralytics YOLO](https://github.com/ultralytics/ultralytics)
- [FastAPI](https://fastapi.tiangolo.com/)
- [OpenCV](https://opencv.org/)
- [PyTorch](https://pytorch.org/)
- [OpenVINO](https://docs.openvino.ai/)

---

<div align="center">

**Built with 💡 by Keshav**

⭐ Star this repository if you find it valuable!

[Report Issue](../../issues) • [Request Feature](../../issues) • [Documentation](../../wiki)

</div>
