# Physical AI Edu

## Overview

Physical AI Edu is a browser-based platform that bridges AI and physical computing for educational use.

Students train an AI model using [Google Teachable Machine](https://teachablemachine.withgoogle.com), then connect it to a physical computing device (such as a micro:bit) via USB serial. The AI classifies real-time camera or microphone input and sends the result to the device, which responds with physical outputs such as LEDs, motors, or sounds.

This project was built to help students experience the full **Sense → Think → Act** loop of a Physical AI system — without writing complex code from scratch.

---

## Key Features

- **Step 1 — Train:** Dedicated guide view for training an image, pose, or sound AI model in Google Teachable Machine, with tips for better accuracy
- **Step 2 — Build:** Embedded MakeCode editor with two starter code templates:
  - **Sound & LED** — displays custom LED patterns and plays tones for each class
  - **Servo Motor** — rotates a servo motor to a set angle (0°, 90°, 180°) for each class
- **Step 3 — Connect:** Paste a Teachable Machine model URL, select camera/microphone, and run real-time AI classification
- Real-time confidence bar display per class
- Web Serial API integration — sends classification results to micro:bit over USB at 115200 baud
- Auto-detects model type (image / pose / sound) from `metadata.json`
- Adjustable send threshold slider
- **Physical AI Basic Code** modal with template selector (Sound & LED / Servo Motor), Blocks notes, JavaScript and Python tabs
- **"Need any Help?"** modal with SENSE → THINK → ACT diagram and step-by-step guide
- Fully responsive single-file web app — no installation required

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| AI Runtime | TensorFlow.js v1.3.1 |
| Image/Pose Model | @teachablemachine/image v0.8, @teachablemachine/pose v0.8 |
| Sound Model | @tensorflow-models/speech-commands v0.4.0 |
| Physical I/O | Web Serial API (Chrome/Edge only) |
| AI Training | Google Teachable Machine (external) |
| Code Editor | Microsoft MakeCode for micro:bit (embedded iframe) |
| Hosting | GitHub Pages |

> No backend, no framework, no build step — the app is built as a single HTML file and uses external libraries/CDNs for AI runtime and embedded MakeCode resources.

---

## My Contributions

- Designed and built the full three-step educational workflow (Train → Build → Connect)
- Created Step 1 guide view with Teachable Machine workflow and training tips
- Embedded MakeCode editor as an interactive iframe in Step 2 view
- Built two original starter code templates (Sound & LED, Servo Motor) with JSDoc comments
- Added template selector synced across Step 2 view and Physical AI Basic Code modal
- Integrated Google Teachable Machine model loading with auto-type detection
- Implemented real-time prediction loop for image, pose, and audio models
- Built Web Serial API communication layer for micro:bit
- Resolved pose model rendering bug (`tmPose.drawKeypoints` module-level call)
- Fixed camera/microphone device enumeration to display real device names
- Designed complete UI with custom color palette (#D3D3FF, #9400D3, #D8BFD8, #ED80E9)

---

## Development Tools
Claude Code was used as an AI-assisted development tool for debugging, refactoring, and implementation support.

---

## Demo

**Live site:** [https://keunjae-kim.github.io/physical-ai-edu/](https://keunjae-kim.github.io/physical-ai-edu/)

> Requires **Google Chrome** or **Microsoft Edge** (Web Serial API is not supported in Firefox or Safari)

### How it works
1. **Step 1** — Follow the guide to train an AI model at Google Teachable Machine, export it, and copy the model URL
2. **Step 2** — Choose a starter template (Sound & LED or Servo Motor), edit the code in the embedded MakeCode editor, and download it to your micro:bit
3. **Step 3** — Connect your micro:bit via USB, paste the model URL, and watch your Physical AI system come alive

### Starter Code Templates

| Template | Output | MakeCode Project |
|---|---|---|
| Sound & LED | Custom LED pattern + tone per class | [Open](https://makecode.microbit.org/S98967-52089-03601-57632) |
| Servo Motor | Servo angle (0° / 90° / 180°) per class | [Open](https://makecode.microbit.org/S88332-90571-57477-53802) |

---

## Installation

No installation is needed. Open the live link in Google Chrome or Microsoft Edge.

To run locally, use a local server:

```bash
# Clone the repository
git clone https://github.com/keunjae-kim/physical-ai-edu.git

# Move into the project folder
cd physical-ai-edu

# Start a local server
python -m http.server 8000
```

Then open:

```
http://localhost:8000
```

Note: Web Serial API, camera access, and microphone access require a secure context such as HTTPS or localhost. GitHub Pages is recommended for classroom use.

---

## Browser Compatibility

| Browser | Supported |
|---|---|
| Chrome 89+ | ✅ |
| Edge 89+ | ✅ |
| Firefox | ❌ (no Web Serial API) |
| Safari | ❌ (no Web Serial API) |

---

## License

MIT License — feel free to use, modify, and share for educational purposes.
