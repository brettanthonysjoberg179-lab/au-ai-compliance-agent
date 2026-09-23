# AU AI Compliance Playbook Agent

Autonomous agent that generates, assembles, and publishes "The AU AI Compliance Playbook: Small Business Guide to Privacy Act 1988 + Automated Decisions" using Google Drive + Composio tooling.

## Features

- **Drive Integration**: Scans Google Drive for existing outlines, drafts, and assets via Composio
- **Chapter Generation**: Auto-generates missing chapters using Ollama (local) or Gemini (cloud)
- **Google Docs Sync**: Uploads generated chapters as Google Docs for collaborative editing
- **PDF Assembly**: Downloads all chapters, assembles into final A4 PDF via pandoc
- **Gumroad Ready**: Placeholder for one-click publishing to Gumroad

## Usage

```bash
# Install dependencies
pip install -r requirements.txt

# Set up environment
cp .env.example .env
# Edit .env with your API keys

# Scan Drive for existing files
python au_ai_compliance_agent.py --scan

# Generate missing chapters
python au_ai_compliance_agent.py --generate

# Assemble final PDF
python au_ai_compliance_agent.py --assemble

# Publish to Gumroad (coming soon)
python au_ai_compliance_agent.py --publish
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `COMPOSIO_API_KEY` | Composio API key |
| `GEMINI_API_KEY` | Google Gemini API key (fallback) |
| `OLLAMA_BASE_URL` | Ollama endpoint (default: http://localhost:11434) |
| `OLLAMA_MODEL` | Ollama model (default: llama3.2:latest) |
| `GUMROAD_ACCESS_TOKEN` | Gumroad API token for publishing |

## Architecture

```
au_ai_compliance_agent.py
├── scan_drive()         # List AU AI files via Composio
├── generate_chapters()  # Create missing chapter drafts
│   ├── generate_with_ollama()   # Local LLM
│   └── generate_with_gemini()   # Cloud LLM
├── assemble_pdf()       # Build final PDF from chapters
└── publish_gumroad()    # Upload to Gumroad
```

## License

MIT
