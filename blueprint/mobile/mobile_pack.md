# VisionX – Architecture & Build Documentation

> This document describes the **actual system architecture, execution flow, and build process** for VisionX (Makfouf Assist). It is written to be used as a long-term reference and onboarding document.

---

## 1. System Philosophy

VisionX is a **local-first perception system** designed to assist visually impaired users by interpreting the environment using computer vision and audio, then translating that understanding into actionable feedback.

**Key principle:**

* Python is the *perception and decision engine*
* Mobile app is the *interaction layer*
* No cloud dependency
* Privacy-first

---

## 2. High-Level Architecture

```
┌───────────────────────────┐
│        Mobile UI          │
│  (Android Native)         │
│                           │
│  - Buttons / Voice        │
│  - Screen Reader          │
│  - Haptics                │
└─────────────┬─────────────┘
              │ Local IPC (HTTP)
┌─────────────▼─────────────┐
│     VisionX Engine        │
│        (Python)           │
│                           │
│  Perception → Context →   │
│  Decision → Output        │
└───────────────────────────┘
```

---

## 3. Repository Layout

```
visionx/
│
├── app.py                     # Entry point
├── requirements.txt
├── buildozer.spec
│
├── perception/
│   ├── __init__.py
│   ├── vision/
│   │   ├── __init__.py
│   │   ├── camera.py
│   │   ├── preprocess.py
│   │   └── detector.py
│   └── audio/
│       ├── __init__.py
│       ├── mic.py
│       ├── preprocess.py
│       └── asr.py
│
├── core/
│   ├── __init__.py
│   ├── context.py
│   ├── decision.py
│   └── state.py
│
├── output/
│   ├── __init__.py
│   ├── speech.py
│   └── haptics.py
│
├── api/
│   ├── __init__.py
│   └── server.py
│
└── models/
    ├── yolo.tflite
    └── labels.txt
```

---

## 4. Runtime Execution Flow

### App Startup

```
Android Launch
 ↓
Permissions Check
 ↓
Start Python Interpreter
 ↓
Load Models (TFLite / ASR)
 ↓
Start Local API Server
 ↓
UI Ready
```

### Detection Sequence

```
User Trigger
 ↓
UI → POST /detect
 ↓
Camera Capture
 ↓
Vision Inference
 ↓
Context Analysis
 ↓
Decision Engine
 ↓
Narration Builder
 ↓
JSON Response
 ↓
UI Output (Speech / Haptics)
```

---

## 5. Python Engine Internal Flow

### Perception Layer

* Camera frame capture
* Resize / normalize
* Model inference (YOLO TFLite)

### Context Layer

* Object priority
* Direction estimation
* Distance approximation

### Decision Layer

* Filter noise
* Resolve conflicts
* Select response strategy

### Output Layer

* Natural language generation
* TTS
* Optional vibration patterns

---

## 6. API Contract Example

**Request:**

```
POST /detect
```

**Response:**

```json
{
  "narration": "شخص أمامك على بعد مترين",
  "priority": "high",
  "objects": [
    {
      "label": "person",
      "direction": "front",
      "distance": "near"
    }
  ]
}
```

---

## 7. Build Process (Buildozer)

### Development Phase

* Python runs directly
* Full logging
* Uncompressed models

### Build Phase

* Freeze dependencies
* Package Python interpreter
* Bundle models
* Generate APK / AAB

### Runtime on Device

* Python runs as local process
* API exposed on localhost
* UI communicates internally

---

## 8. Why This Architecture Works

* Clear separation of concerns
* Replaceable UI or engine
* Future migration to C++ possible
* Suitable for MVP and research

---

## 9. Future Extensions

* GPS integration
* OCR module
* Spatial audio
* Edge TPU / NNAPI acceleration

---

## 10. Mental Model Summary

VisionX is not a mobile app.

It is a **perception system** deployed inside a mobile environment.

The mobile device is the container, not the brain.

