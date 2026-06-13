# Voice Forge 2

Voice Forge 2 is a state-of-the-art, low-latency voice cloning application designed to replicate high-fidelity human speech from minimal audio samples. Built with a modular architecture, it combines advanced deep learning synthesis with a lightweight, developer-friendly interface for real-time applications.

## 🚀 Features

- **Few-Shot Cloning**: Clone a target voice with as little as 5 to 10 seconds of clean reference audio.
- **Low Latency Inference**: Optimized for real-time speech generation, making it ideal for interactive conversational agents.
- **Multi-Lingual & Cross-Lingual Support**: Transfer structural vocal characteristics across different languages smoothly.
- **Prosody Control**: Fine-tune pacing, emotional inflection, and emphasis directly via markup or API parameters.
- **Streaming Output**: Stream audio chunks dynamically as they are generated to reduce time-to-first-byte (TTFB).

## 🛠️ Tech Stack

- **Core AI Layer**: PyTorch, Custom Diffusion/Autoregressive Transformer Architectures
- **Audio Processing**: Librosa, SoundFile, HiFi-GAN Vocoder / BigVGAN
- **Backend API**: FastAPI, WebSockets (for low-latency streaming)
- **Frontend UI**: Next.js / TailwindCSS (or Gradio for rapid prototyping)

## 💻 Getting Started

### Prerequisites

Ensure you have the following installed on your host machine:

- Python 3.10 or higher
- CUDA Toolkit 11.8+ (strongly recommended for GPU acceleration)
- FFmpeg

### Installation

Follow these steps to set up the development environment:

#### 1. Clone the Repository

Clone the codebase locally and navigate into the project root:

```bash
git clone https://github.com/your-organization/voice-forge-2.git
cd voice-forge-2
```

#### 2. Set Up Virtual Environment

Create a clean Python virtual environment and activate it:

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

#### 3. Install Dependencies

Install the core dependencies along with the appropriate PyTorch/CUDA wheels:

```bash
pip install -r requirements.txt
```

#### 4. Download Pre-trained Weights

Fetch the necessary model checkpoints using the setup script:

```bash
python scripts/download_models.py --model base-v2
```

## 📖 Quick Start

### Running the Application

You can spin up the full web interface or run a quick inference script via the command line.

#### Web UI

To launch the interactive dashboard:

```bash
python app.py --host 0.0.0.0 --port 7860
```

#### Command Line Interface (CLI)

To run a quick test clone directly from your terminal:

```bash
python infer.py \
  --reference_audio /path/to/target_voice.wav \
  --text "Hello world! This is Voice Forge 2 running a local inference test." \
  --output_path /outputs/cloned_speech.wav
```

## 🔌 API Reference

Voice Forge 2 exposes a robust REST and WebSocket API.

### Generate Voice (REST)

**POST** `/api/v2/synthesize`

**Request Body:**

```json
{
  "text": "The quick brown fox jumps over the lazy dog.",
  "reference_audio_url": "https://example.com/audio/sample.wav",
  "temperature": 0.7,
  "speed": 1.0,
  "stream": false
}
```

**Response:** Returns a standard JSON payload with a direct download link to the compiled audio file, or an audio stream buffer if "stream": true.

## 📄 License

This project is licensed under the Apache 2.0 License - see the LICENSE file for more details.
