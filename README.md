# EEG Emotion Detection Project

## Overview
This project focuses on detecting emotions from EEG brain signals using the DEAP dataset. It includes:
- Jupyter notebooks for data preprocessing, feature extraction, and model training.
- A FastAPI backend for real-time streaming and inference.
- A frontend application for user interaction and visualization of results.

## Project Structure
```
.
├── notebooks
│   ├── data_preprocessing.ipynb  # Data preparation and cleaning
│   ├── feature_extraction.ipynb  # Extract features from EEG signals
│   ├── model_training.ipynb      # Train and evaluate machine learning models
├── backend
│   ├── main.py                   # FastAPI application
│   └── utils.py                  # Helper functions
├── frontend
│   ├── public
│   │   └── index.html            # Frontend HTML file
│   ├── src
│   │   ├── App.js                # React app entry point
│   │   └── components
│   │       ├── StreamDisplay.js  # Component for real-time streaming visualization
│   │       └── EmotionChart.js   # Component for displaying detected emotions
│   └── package.json              # Frontend dependencies
├── Dockerfile                    # Dockerfile for containerizing the app
├── requirements.txt              # Python dependencies
└── README.md                     # Project documentation
```

## Features
- Real-time emotion detection from EEG signals.
- Preprocessing pipeline for EEG signal cleaning and feature extraction.
- REST API for inference and data streaming.
- Interactive frontend for real-time emotion visualization.

## Installation

### Prerequisites
- Python 3.10+
- Node.js (for frontend)
- Docker

### Steps
1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/eeg-emotion-detection.git](https://github.com/benali-ayoub/eeg-emtion-detection.git)
   cd eeg-emotion-detection
   ```

2. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Install frontend dependencies:
   ```bash
   cd frontend
   npm install
   ```

4. Run the FastAPI backend:
   ```bash
   cd backend
   uvicorn main:app --reload
   ```

5. Run the frontend application:
   ```bash
   cd frontend
   npm start
   ```

6. Build and run the Docker container:
   ```bash
   docker build -t eeg-emotion-detection .
   docker run -p 8000:8000 eeg-emotion-detection
   ```

## API Endpoints
- `POST /predict`
  - Input: JSON containing EEG signal data
  - Output: Predicted emotion and confidence scores

### Example Request
```bash
curl -X POST "http://127.0.0.1:8000/predict" \
-H "Content-Type: application/json" \
-d '{"eeg_data": [[0.1, 0.2, 0.3, ...], [0.05, 0.15, 0.25, ...]]}'
```

### Example Response
```json
{
  "emotion": "Happy",
  "confidence": 0.87
}
```

## Notebooks
- **data_preprocessing.ipynb**: Load and clean EEG data from the DEAP dataset.
- **feature_extraction.ipynb**: Extract relevant features (e.g., PSD, Hjorth parameters) for model training.
- **model_training.ipynb**: Train models to classify emotions using extracted features.

## Frontend
The frontend is built using React and provides an interactive interface to:
- Visualize EEG signals in real-time.
- Display the detected emotions and their confidence levels.

### Key Components
- **StreamDisplay**: Displays live EEG signal data.
- **EmotionChart**: Visualizes the detected emotion in real-time.

## Docker Setup

### Dockerfile
```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . ./

CMD ["uvicorn", "backend.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### Build and Run
```bash
docker build -t eeg-emotion-detection .
docker run -p 8000:8000 eeg-emotion-detection
```

## Testing
Run unit tests for the backend and model:
```bash
pytest tests/
```

## Future Work
- Integrate additional features for enhanced emotion detection.
- Support multi-modal emotion recognition by integrating facial expression analysis.
- Deploy the application to cloud services (e.g., AWS, GCP).

## License
This project is licensed under the MIT License. See the LICENSE file for details.

---

Contributions and feedback are welcome! Submit issues or pull requests on GitHub to improve the project.
