# ⚙️ Technical Requirement Document (TRD) - Smart Specs With Scanner & Voice Input (MARVIS)

## 1. System Architecture Overview
MARVIS utilizes a hybrid client-edge architecture combining real-time hardware frame acquisition, computer vision pre-processing, Web Socket / REST APIs, and local speech synthesis.

```
+---------------------+     +-----------------------+     +------------------------+
| Smart Specs / Cam   | --> | Image Preprocessor    | --> | OCR Engine             |
| (Webcam Capture)    |     | (OpenCV / Adaptive Threshold) | (Tesseract / Vision) |
+---------------------+     +-----------------------+     +------------------------+
                                                                      |
+---------------------+     +-----------------------+                 v
| Audio Speaker / TTS | <-- | Voice Command Parser  | <-- +------------------------+
| (Speech Synthesis)  |     | (Web Speech / PyTTSx3)|     | Text NLP Summarizer    |
+---------------------+     +-----------------------+     +------------------------+
```

---

## 2. Technical Stack Specifications

- **Language & Runtime**: Node.js 18+ / Python 3.10+
- **Frontend / Dashboard**: React, Tailwind CSS, Lucide Icons, WebSockets
- **Computer Vision & OCR**: OpenCV (`opencv-python`), Tesseract OCR / Vision APIs
- **Audio Processing**: Web Speech API / `pyttsx3` / SpeechRecognition
- **Local Application Server**: Express.js / Node HTTP Server running on `http://localhost:3001`

---

## 3. Component Details & Protocols

### 3.1 Frame Capture Pipeline
- Camera input ingested via OpenCV `VideoCapture(0)` or HTML5 `<video>` WebRTC stream.
- Resolution set to $1920 \times 1080$ HD for optimal OCR character clarity.

### 3.2 Image Processing Operations
```python
def preprocess_image(frame):
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    denoised = cv2.fastNlMeansDenoising(gray, h=10)
    thresh = cv2.adaptiveThreshold(
        denoised, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2
    )
    return thresh
```

### 3.3 Audio Synthesis & Speech Output
- Text extracted from OCR is segmented into sentences to minimize audio start delay.
- First sentence buffered and played immediately while remaining text processes in background.

---

## 4. API Endpoints & Interfaces

### `POST /api/scan`
- **Request Body**: `{ "image": "base64_encoded_jpeg_string" }`
- **Response**:
```json
{
  "success": true,
  "text": "Extracted document text goes here...",
  "confidence": 0.94,
  "timestamp": "2026-09-22T18:30:00Z"
}
```

### `GET /api/history`
- **Response**: Array of past scans with ID, thumbnail, text snippet, and timestamp.

---

## 5. Security & Hardware Requirements
- **Hardware**: USB Webcam / Wearable Smart Glass Module, Microphone, Bone-Conduction Earphones.
- **Privacy & Local Processing**: Local OCR options ensure document contents are processed on-device without leaking sensitive text.
