# Unitree SDK2 Python Wrapper (with Voice Control & Teleop)

This project integrates the Unitree SDK2 with advanced features like voice-controlled teleoperation, gesture control, and RealSense/Moondream VLA integration. Some large or licensed assets are not included in the Git repository and must be downloaded manually.

---

## 📦 Ignored or Removed Files

The following files and directories are intentionally excluded from Git to keep the repository lightweight:

| File/Folder                                      | Reason                      |
|--------------------------------------------------|-----------------------------|
| `cyclonedds/`                                     | Excluded to avoid nested Git repo. Clone separately if needed. |
| `vosk-model-hi-0.22.zip`                          | Large Vosk speech recognition model file. |
| `example/voice_controlled_teleop/large_model/`    | Contains large models for voice recognition. |
| `myenv/`                                          | Local virtual environment (Python). |
| `unitree_sdk2py.egg-info/`                        | Python packaging metadata. |

---

## 📥 Required Downloads

To fully run the voice control and teleoperation scripts, you must manually download the following:

### 1. **Vosk Hindi Model (`vosk-model-hi-0.22`)**
- **Download Link:** https://alphacephei.com/vosk/models
- **Model:** `vosk-model-hi-0.22`
- **Action:** Unzip the downloaded `.zip` file.
- **Place the extracted folder at:**
  ```bash
  example/voice_controlled_teleop/large_model/

