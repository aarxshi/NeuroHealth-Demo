# NeuroHealth

A local AI-powered symptom triage demo built for the [UCSC OSPO 2026 GSoC project](https://ucsc-ospo.github.io/project/osre26/nelbl/neurohealth/).

Describe your symptoms, get an urgency assessment - ER, doctor visit, or self-care, grounded in MedlinePlus medical knowledge.


<p align="center">
<img src="demo/ui.png" width="700">
</p>
<p align="center">
<img src="demo/example.png" width="700">
</p>


## How it works

User describes symptoms in plain language. A local knowledge base of MedlinePlus entries is searched for matching context, which gets injected into the prompt alongside the symptoms. Llama3 returns a structured JSON assessment and the UI renders urgency level, reasoning, and next steps.

This is a minimal RAG pipeline running entirely on your machine. No cloud APIs, no data leaves your device.

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

Open `http://localhost:3000`.

## Stack

- **Model**: Llama3 8B via Ollama
- **Retrieval**: keyword-matched local knowledge base (MedlinePlus)
- **Frontend**: vanilla HTML/CSS/JS, single file, zero dependencies

## About

This demo was built as part of a GSoC 2026 application for the [NeuroHealth project](https://ucsc-ospo.github.io/project/osre26/nelbl/neurohealth/) at UCSC OSPO, mentored by Linsey Pang and Bin Dong.

## Disclaimer

Research prototype only. Not a substitute for professional medical advice. In an emergency call your local emergency number immediately.
