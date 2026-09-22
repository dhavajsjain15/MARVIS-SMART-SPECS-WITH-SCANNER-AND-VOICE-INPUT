# 🔄 App Flow & User Journey - Smart Specs With Scanner & Voice Input (MARVIS)

## 1. Primary User Journey: Voice-Activated Document Scan

```mermaid
graph TD
    A[User Wears Smart Specs] --> B[User Speaks: "Scan Document"]
    B --> C{Microphone Listener Parses Command?}
    C -- Yes --> D[Audio Chime Plays & Camera Snapshot Captured]
    C -- No --> B
    D --> E[OpenCV Preprocesses Snapshot]
    E --> F[OCR Engine Extracts Text & Bounding Boxes]
    F --> G[TTS Segmenter Synthesizes First Sentence]
    G --> H[Audio Spoken to User via Earphones]
    H --> I[Text & Image Logged to Web Dashboard & Local History]
```

---

## 2. Detailed Flow Steps

### Step 1: Initialization
1. MARVIS service initializes camera feed on `http://localhost:3001`.
2. Voice recognition daemon listens continuously for wake triggers.

### Step 2: Image Acquisition & Pre-processing
1. Snapshot taken on trigger.
2. OpenCV applies grayscale conversion, noise reduction, and adaptive thresholding.

### Step 3: Text Processing & Reading
1. Text blocks extracted and sorted top-to-bottom.
2. Speech engine streams audio feedback immediately.

### Step 4: Storage & Review
1. Results uploaded to dashboard history tab.
2. User can issue voice command "Repeat" or "Summarize".
