# NeuroHealth

A local AI-powered symptom triage demo built for the [UCSC OSPO 2026 GSoC project](https://ucsc-ospo.github.io/project/osre26/nelbl/neurohealth/).

Describe your symptoms, get an urgency assessment — ER, doctor visit, or self-care — grounded in MedlinePlus medical knowledge.

## How it works

1. User describes symptoms in plain language
2. A local knowledge base (MedlinePlus entries) is searched for matching context
3. Relevant context is injected into the prompt alongside the symptoms
4. Llama3 returns a structured JSON assessment
5. The UI renders urgency level, reasoning, and next steps

This is a minimal RAG (Retrieval-Augmented Generation) pipeline running entirely on your machine — no cloud APIs, no data leaves your device.

## Setup

Install [Ollama](https://ollama.com) and pull the model:
```bash
ollama pull llama3:latest
```

Allow browser requests and start Ollama:
```bash
# macOS/Linux
OLLAMA_ORIGINS="*" ollama serve

# Windows (PowerShell)
$env:OLLAMA_ORIGINS="*"; ollama serve
```

Serve the file:
```bash
npx serve .
# or
python -m http.server 8000
```

Open `http://localhost:3000` in your browser.

## Stack

- **Model**: Llama3 8B via Ollama
- **Retrieval**: keyword-matched local knowledge base (MedlinePlus)
- **Frontend**: vanilla HTML/CSS/JS, single file, zero dependencies

## Roadmap

- [ ] Semantic search over a larger knowledge base (embeddings)
- [ ] Multi-turn conversation with clarifying questions
- [ ] Appointment routing suggestions
- [ ] Streaming responses
- [ ] Clinical safety evaluation

## Disclaimer

Research prototype only. Not a substitute for professional medical advice. In an emergency call your local emergency number immediately.
