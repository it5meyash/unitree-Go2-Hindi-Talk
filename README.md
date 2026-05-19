# Unitree Go2 Hindi Voice & Keyboard Teleoperation

This project provides a complete infrastructure to control the **Unitree Go2 Robot** using typed prompts and **real-time Hindi voice commands**. It leverages the standard `unitree_sdk2py` wrapper alongside the Kaldi-based **VOSK Speech Recognition** library.

---

## ✨ Features

- **Voice-Command Teleoperation (Hindi):** Speak natively in Hindi to command the Go2 robot (e.g. Move Forward, Turn, Sit, Dance).
- **Keyboard Prompt Teleoperation:** Use standard typed CLI commands as an alternative interactive control mode.
- **Offline & Responsive:** Uses an offline Vosk speech model meaning low-latency hardware performance without requiring internet API calls.
- **Structured Codebase:** Cleanly divides the `unitree_sdk` from the custom application code found in `src/go2_hindi_talk`.

---

## 🛠️ Project Structure

```
Go2_Hindi_Talk/
├── src/go2_hindi_talk/
│   ├── voice-prompt-controlled-teleop.py    (Hindi Voice Control Script)
│   └── input-prompt-control-teleop.py       (CLI Type-based Control Script)
├── models/
│   └── vosk-model-hi-0.22/                  (Required parameter folder for offline Speech To Text)
├── requirements.txt                         (Dependency list)
├── setup.py                                 (Unitree SDK setup)
└── README.md
```

---

## 📥 Prerequisites & Installation

### 1. Environment & Dependencies

Make sure you are using Python 3.8+ or higher. It is recommended to use a virtual environment.

```bash
# Optional: Create and activate virtual environment
python3 -m venv myenv
source myenv/bin/activate

# Install all the required packages
pip install -r requirements.txt
```

> **Note:** The `requirements.txt` includes modules like `vosk`, `sounddevice` (for mic input), `mediapipe`, and `pynput`. The project also requires `cyclonedds`. You may need to separately compile or ensure your CycloneDDS network environments are set.

### 2. Required AI Model Download 

The high-precision speech recognizer requires the VOSK Hindi model, which is excluded from Git due to its large size.

1. **Download Link:** [Vosk-Model-Hi-0.22](https://alphacephei.com/vosk/models) (Look for `vosk-model-hi-0.22`)
2. **Action:** Extract the `.zip` file.
3. **Placement:** Place the extracted folder inside the `models/` directory so the path matches exactly:
   ```bash
   models/vosk-model-hi-0.22/
   ```

---

## 🚀 How to Use

Connect to the Unitree Go2 via the typical SDK networking methodology (Ethernet or Robot's Wi-Fi network), and run one of the teleop scripts below:

### Option A: Hindi Voice Control (Microphone)

To start interacting with your robot using your microphone and speaking Hindi:

```bash
python src/go2_hindi_talk/voice-prompt-controlled-teleop.py
```

**Supported Hindi Voice Commands:**
- **Stand Up:** "खड़े हो", "खड़ा हो", "खड़े"
- **Sit Down:** "बैठ", "बैठो", "नीचे बैठो"
- **Move Forward:** "आगे", "आगे चलो"
- **Move Backward:** "पीछे", "पीछे चलो"
- **Move Left:** "बाएं", "बाएं चलो"
- **Move Right:** "दाएं", "दाएं चलो"
- **Jump Forward:** "कूद", "आगे कूद"
- **Give Hand/Wave:** "हाथ", "हाथ दो", "हाथ मिलाओ"
- **Dance/Wiggle:** "नाचो", "डांस करो"
- **Stop Program:** "रुको", "बंद करो", "ठहरो"

### Option B: Terminal Input Prompt Control

To use simple English text inputs in your terminal to drive the robot:

```bash
python src/go2_hindi_talk/input-prompt-control-teleop.py
```

**Supported Text Commands (English):**
- `stand up`
- `sit down`
- `right`
- `stop`

*(Type `stop` inside the prompt terminal to close the application.)*

---

## ⚠️ Notes & Troubleshooting
- Ensure your network interface is correctly configured for CycloneDDS (`CYCLONEDDS_URI` and network adapters) which is the backbone for the Unitree SDK communication.
- If you face audio input errors, ensure you have correctly installed PortAudio (e.g. `sudo apt install libportaudio2` on Ubuntu) for `sounddevice` to bind with your microphone hardware correctly.
