# ai-gym-coach
AI Real-Time Gym Coach

A real-time AI fitness coach that watches your workout through your webcam, tracks your form with pose detection, counts reps, and gives you spoken feedback powered by an LLM.

Live demo: [add your Streamlit app link here]

Features
Real-time pose detection using MediaPipe, running on live webcam video
Exercise detection and rep counting for squats, push-ups, lunges, biceps curls, and shoulder press
Form analysis that flags posture issues as you move (joint angles, range of motion)
AI voice coaching: issues are sent to a Groq-hosted LLM, which returns short, natural coaching feedback that is spoken aloud
Session tracking for reps and workout metrics
Landing page to introduce the project
Tech Stack
Area	Tools
Frontend / App	Streamlit, Streamlit-WebRTC
Computer Vision	MediaPipe Pose Landmarker, OpenCV
LLM Coaching	Groq API (openai/gpt-oss-120b)
Language	Python 3.12
Project Structure
ai-gym-coach/
├── Main App/
│   ├── main.py              # Streamlit entry point
│   ├── core/                # Base exercise logic
│   ├── detectors/           # Per-exercise form detectors
│   ├── services/            # Coaching (LLM, TTS), vision, tracking, state, UI
│   ├── ml_models/           # MediaPipe pose model
│   ├── static/              # Styles and fonts
│   ├── requirements.txt
│   └── packages.txt
└── LandingPage/             # Static landing page (HTML/CSS)
Getting Started
Prerequisites
Python 3.11 or 3.12 (MediaPipe 0.10.14 does not support newer versions)
A webcam and microphone/speakers
A free Groq API key
Installation
bash
git clone https://github.com/biradarrevansidda/ai-gym-coach.git
cd ai-gym-coach

python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate

cd "Main App"
pip install -r requirements.txt
Set your API key

Create Main App/.streamlit/secrets.toml:

toml
GROQ_API_KEY = "your_key_here"

Or set it as an environment variable:

bash
# Windows (cmd)
set GROQ_API_KEY=your_key_here
# macOS / Linux
export GROQ_API_KEY=your_key_here
Run
bash
streamlit run main.py

Open http://localhost:8501 and allow camera access when prompted.

Deployment

Deployed on Streamlit Community Cloud:

Main file path: Main App/main.py
Python version: 3.12
Secret: GROQ_API_KEY
Notes
Never commit your API key. secrets.toml and .env are git-ignored.
On some networks, WebRTC may need a STUN/TURN server to connect the camera in the deployed app.
Author

Revansidda Biradar GitHub
