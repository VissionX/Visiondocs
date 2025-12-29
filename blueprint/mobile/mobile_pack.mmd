# Blueprint Pack — VisionX Mobile

This section provides **all technical blueprints** required to start implementing VisionX Mobile immediately. Each blueprint is implementation-agnostic and focuses on *flow, responsibility, and contracts*.

---

## 1. System Architecture Blueprint

```mermaid
graph TD
    Camera --> VisionPreprocess
    VisionPreprocess --> ObjectDetection

    Microphone --> AudioPreprocess
    AudioPreprocess --> SpeechRecognition

    ObjectDetection --> ContextEngine
    SpeechRecognition --> ContextEngine

    ContextEngine --> DecisionEngine
    DecisionEngine --> AudioOutput
    DecisionEngine --> HapticOutput
```

### Responsibilities

* VisionPreprocess: resize, normalize, frame sampling
* ObjectDetection: TFLite YOLO inference
* AudioPreprocess: framing, noise handling
* SpeechRecognition: command-level ASR
* ContextEngine: spatial + priority reasoning
* DecisionEngine: converts context into actions

---

## 2. Runtime Sequence Blueprint

```mermaid
sequenceDiagram
    participant User
    participant App
    participant Camera
    participant Mic
    participant Vision
    participant ASR
    participant Context
    participant TTS

    User->>App: Launch
    App->>Camera: Start stream
    App->>Mic: Start listening

    Camera->>Vision: Frame
    Vision->>Context: Objects + positions

    Mic->>ASR: Audio frames
    ASR->>Context: Command / intent

    Context->>TTS: Spoken feedback
    TTS->>User: Audio output
```

---

## 3. Data Flow Blueprint

```mermaid
graph LR
    RawVideo -->|Frames| VisionDSP
    VisionDSP -->|Tensor| DetectionModel
    DetectionModel -->|Objects| Context

    RawAudio -->|Frames| AudioDSP
    AudioDSP -->|Features| ASRModel
    ASRModel -->|Intent| Context

    Context -->|Decision| Output
```

---

## 4. Folder Structure Blueprint

```text
VisionX-Mobile/
├── app/
│   └── main.py            # App entry point
├── perception/
│   ├── vision/
│   │   ├── camera.py
│   │   ├── preprocess.py
│   │   └── detector.py
│   └── audio/
│       ├── mic.py
│       ├── preprocess.py
│       └── asr.py
├── core/
│   ├── context.py
│   ├── decision.py
│   └── state.py
├── output/
│   ├── speech.py
│   └── haptics.py
├── models/
│   ├── yolo.tflite
│   └── vosk/
├── system/
│   ├── config.py
│   └── logger.py
└── docs/
    ├── architecture.md
    ├── flow.md
    └── sequences.md
```

---

## 5. Core State Machine Blueprint

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Listening
    Listening --> Detecting
    Detecting --> Speaking
    Speaking --> Idle

    Detecting --> Error
    Error --> Idle
```

---

## 6. Audio Processing Blueprint (DSP → ASR)

```mermaid
graph TD
    Mic --> ADC
    ADC --> Framing
    Framing --> Windowing
    Windowing --> Features
    Features --> ASR
```

* Windowing: Hamming / Hann
* Features: MFCC (default)
* Output: phoneme probabilities → words

---

## 7. Vision Processing Blueprint

```mermaid
graph TD
    Camera --> Resize
    Resize --> Normalize
    Normalize --> Tensor
    Tensor --> YOLO
    YOLO --> Objects
```

---

## 8. Decision Logic Blueprint

```mermaid
graph TD
    Objects --> PriorityFilter
    PriorityFilter --> DirectionAnalysis
    DirectionAnalysis --> Decision
    Decision --> Speak
```

Rules:

* Distance < Direction < Type
* One message at a time

---

## 9. Accessibility Contract

```mermaid
graph LR
    Event -->|Short message| TTS
    TTS --> User
```

Constraints:

* Max sentence length: 5 words
* No visual dependency

---

## 10. Implementation Order (Critical)

```text
1. Camera capture
2. Audio output (TTS)
3. Object detection
4. Context engine
5. Speech recognition
6. Decision refinement
```

---

## 11. Future Extension Hooks

```mermaid
graph TD
    Context --> GPS
    Context --> OCR
    Context --> Navigation
```

---

## 12. Definition of "Done"

* App runs offline
* Detects obstacles
* Speaks clearly
* No visual UI needed
* Stable for daily use

---

This blueprint pack is the **source of truth**. All implementations must conform to these flows, not the opposite.

