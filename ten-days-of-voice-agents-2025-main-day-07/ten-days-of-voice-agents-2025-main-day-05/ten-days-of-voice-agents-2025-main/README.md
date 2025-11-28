# Reliance Group AI Assistant

Welcome to the **Reliance Group AI Assistant**! This project is a sophisticated voice agent designed to represent Reliance Group, India's largest private sector enterprise.

## About the Project

This is an **Intelligent Sales Development Representative (SDR)** that engages users in natural conversation to explore Reliance's diverse ecosystem—from Digital Services (Jio) to Retail and New Energy.

**Key Features:**
-   **Professional Persona**: A warm, corporate Indian voice representing Reliance's "Growth is Life" philosophy.
-   **Knowledge Base**: Expert on Reliance verticals:
    -   **Jio**: Digital services and connectivity.
    -   **Retail**: India's largest retail chain.
    -   **O2C**: Oil to Chemicals.
    -   **New Energy**: Green hydrogen and solar solutions.
-   **Lead Capture**: Intelligently collects user details (Name, Company, Interest) and saves them for follow-up.
-   **Premium UI**: A modern, split-layout interface with dynamic visuals and Reliance branding.

## Repository Structure

This is a **monorepo** containing:

```
ten-days-of-voice-agents-2025/
├── backend/          # LiveKit Agents backend (Python) with Reliance Persona
├── frontend/         # Next.js frontend with Reliance Blue/Red Theme
├── shared-data/      # Shared content (reliance_content.json) and leads
├── start_app.sh      # Script to start all services
└── README.md         # This file
```

### Backend
Based on LiveKit's agent framework.
-   **Agent**: `RelianceSDRAgent` in `src/agent.py`.
-   **Content**: `reliance_content.json` drives the agent's knowledge and FAQs.

### Frontend
Modern Next.js application.
-   **Theme**: Custom "Reliance" Blue/Red theme with glassmorphism effects.
-   **UI**: Split-layout landing page and interactive session view.

## Quick Start

### Prerequisites

Make sure you have the following installed:

-   Python 3.9+ with [uv](https://docs.astral.sh/uv/) package manager
-   Node.js 18+ with pnpm
-   [LiveKit CLI](https://docs.livekit.io/home/cli/cli-setup) (optional but recommended)
-   [LiveKit Server](https://docs.livekit.io/home/self-hosting/local/) for local development

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd ten-days-of-voice-agents-2025
```

### 2. Backend Setup

```bash
cd backend

# Install dependencies
uv sync

# Copy environment file and configure
cp .env.example .env.local

# Edit .env.local with your credentials:
# - LIVEKIT_URL
# - LIVEKIT_API_KEY
# - LIVEKIT_API_SECRET
# - DEEPGRAM_API_KEY (for STT/TTS)
# - GOOGLE_API_KEY (for Gemini LLM)

# Download required models
uv run python src/agent.py download-files
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
pnpm install

# Copy environment file and configure
cp .env.example .env.local

# Edit .env.local with the same LiveKit credentials
```

### 4. Run the Application

#### Option A: Use the convenience script (runs everything)

```bash
# From the root directory
chmod +x start_app.sh
./start_app.sh
```

This will start:
-   LiveKit Server (in dev mode)
-   Backend agent (listening for connections)
-   Frontend app (at http://localhost:3000)

#### Option B: Run services individually

```bash
# Terminal 1 - LiveKit Server
livekit-server --dev

# Terminal 2 - Backend Agent
cd backend
uv run python src/agent.py dev

# Terminal 3 - Frontend
cd frontend
pnpm dev
```

Then open http://localhost:3000 in your browser!

## License

This project is based on templates from LiveKit. See individual LICENSE files in backend and frontend directories for details.
