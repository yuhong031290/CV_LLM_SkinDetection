# Skin Disease AI Assistant

An integrated mobile and backend system for AI-assisted skin disease diagnosis. This project combines a lightweight image classifier and a fine-tuned large language model (LLM), supporting on-device classification and interactive medical Q&A.

## 🩺 Motivation

Diagnosing skin diseases is challenging due to diverse symptoms and appearances. This system is designed for:
- Local image classification on mobile devices
- Protecting user privacy (no cloud uploads)
- Fast diagnostic assistance
- Medical Q&A with a fine-tuned LLM

## ✨ Features

| Feature            | Description                                             |
|-------------------|---------------------------------------------------------|
| 📱 **Mobile Inference** | On-device skin disease detection using a lightweight TFLite model.     |
| 🧠 **LLM Chatbot**       | Fine-tuned LLaMA model for answering medical questions.       |
| 🔐 **Privacy-Focused**   | Image classification runs entirely offline. No medical images are uploaded.          |
| 🚀 **Cross-Platform**   | Built with Flutter for a consistent experience on Android and iOS. |

## 🛠️ Technology Stack

| Component | Technology | Purpose |
|---|---|---|
| **Frontend** | Flutter, Dart | Cross-platform mobile application development. |
| **Backend** | Python | Serves the fine-tuned LLM for Q&A. |
| **CV Model** | MobileNetV2 (TFLite) | Lightweight, on-device image classification. |
| **LLM** | LLaMA3 + LoRA | Advanced, fine-tuned language model for medical dialogue. |

## 📂 Project Structure

```
CV_LLM_SkinDetection/
├── backend/
│   ├── inference.py          # Backend script to run the LLM.
│   ├── llm_fine_tuning.py    # Python script for fine-tuning the LLM.
│   └── llm_fine_tuning.ipynb # Jupyter Notebook for LLM fine-tuning experiments.
│
├── frontend/
│   ├── lib/
│   │   ├── main.dart           # Flutter app entry point.
│   │   ├── ImageClassifier.dart # Handles TFLite model loading and inference.
│   │   └── DiseaseInformation.dart # UI components for displaying results.
│   ├── assets/
│   │   └── *.tflite            # TFLite models for on-device classification.
│   └── pubspec.yaml          # Flutter project dependencies.
│
└── Demo.png                    # Screenshot of the application.
```

## 🧠 Models

### Image Classifier
- **Framework**: TFLite
- **Architecture**: Based on MobileNetV2 for efficient mobile performance.
- **Deployment**: Runs locally on the user's device via the Flutter app. The model files (`skin.tflite`, `model.tflite`, etc.) are stored in `frontend/assets/`.

### Language Model
- **Architecture**: LLaMA3 fine-tuned with LoRA (Low-Rank Adaptation).
- **Training**: The fine-tuning process is detailed in `backend/llm_fine_tuning.py` and the corresponding notebook.
- **Deployment**: Served by the Python backend (`backend/inference.py`).

## 🖼️ Demo

<p align="center">
  <img src="Demo.png" alt="Skin Disease AI Assistant Demo" width="800"/>
</p>

## � Getting Started

### Prerequisites
- Flutter SDK
- Python 3.8+
- An IDE like VS Code or Android Studio

### 1. Frontend (Flutter App) Setup
```bash
# Navigate to the frontend directory
cd frontend

# Install dependencies
flutter pub get

# Run the app on a connected device or emulator
flutter run
```

### 2. Backend (Python LLM Server) Setup
```bash
# Navigate to the backend directory
cd backend

# It's recommended to create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Install Python dependencies (assuming a requirements.txt exists)
# You may need to create one based on the imports in the .py files
pip install -r requirements.txt

# Run the inference server
python inference.py
```

## �📸 How It Works

Users can either **take a photo** or **upload an image** of their skin condition.
Here's the full inference pipeline:

1. 📷 **User provides a skin image** within the mobile app.
2. 📱 **The app executes the TFLite model locally** for disease classification.
   - All inference runs **on-device**, ensuring privacy and low latency.
3. � **The prediction result (text only)** is sent to the backend.
4. 🤖 **The backend's fine-tuned LLaMA model** receives the prediction.
   - It generates a detailed explanation, suggestions, and answers to follow-up questions.
5. 💬 **The response is displayed** to the user in the app's chat interface.



