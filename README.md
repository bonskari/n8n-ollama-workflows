# Free n8n + Ollama AI Workflow Templates

**Run powerful AI automations locally. No API keys. No cloud. No monthly fees. Complete privacy.**

This repository contains **3 free, ready-to-import n8n workflow templates** that use [Ollama](https://ollama.com) for local AI processing. Every workflow runs entirely on your machine -- your data never leaves your network.

These are free samples from the **Self-Hosted AI Workflow Pack**, which includes 11 production-ready workflows covering document processing, email automation, content generation, lead scoring, and more.

---

## Included Workflows

### 1. AI Text Summarizer
**File:** [`workflows/text-summarizer.json`](workflows/text-summarizer.json)

Accepts any text via webhook and returns a structured summary with:
- One-line executive summary
- 3-5 key bullet points
- Detected tone of the text

**How it works:**
```
Webhook (POST) --> Validate Input --> Ollama Summarize --> Format Response --> Return JSON
```

**Test it:**
```bash
curl -X POST http://localhost:5678/webhook/summarize \
  -H "Content-Type: application/json" \
  -d '{"text": "Paste a long article or document here..."}'
```

---

### 2. AI Sentiment Analyzer
**File:** [`workflows/sentiment-analyzer.json`](workflows/sentiment-analyzer.json)

Analyzes the sentiment of one or multiple texts. Returns structured results with:
- Sentiment label (POSITIVE, NEGATIVE, NEUTRAL, MIXED)
- Confidence score (0.0 - 1.0)
- Detected emotions (joy, anger, sadness, etc.)
- Brief reasoning

Supports batch analysis -- send up to 10 texts at once.

**How it works:**
```
Webhook (POST) --> Validate Input --> Ollama Analyze --> Parse Results --> Return JSON
```

**Test it (single text):**
```bash
curl -X POST http://localhost:5678/webhook/analyze-sentiment \
  -H "Content-Type: application/json" \
  -d '{"text": "I absolutely love this product! Best purchase I have made all year."}'
```

**Test it (batch):**
```bash
curl -X POST http://localhost:5678/webhook/analyze-sentiment \
  -H "Content-Type: application/json" \
  -d '{"texts": ["Great service, very happy!", "Terrible experience, never again.", "The meeting is at 3pm tomorrow."]}'
```

---

### 3. AI Keyword & Entity Extractor
**File:** [`workflows/keyword-extractor.json`](workflows/keyword-extractor.json)

Extracts structured data from any text:
- Top keywords and phrases
- Named entities (people, organizations, locations, dates, products)
- Main topics/themes
- Content category

**How it works:**
```
Webhook (POST) --> Validate Input --> Ollama Extract --> Parse Results --> Return JSON
```

**Test it:**
```bash
curl -X POST http://localhost:5678/webhook/extract-keywords \
  -H "Content-Type: application/json" \
  -d '{"text": "Apple CEO Tim Cook announced the new iPhone 16 at the September 2024 event in Cupertino, California. The device features an A18 chip and Apple Intelligence capabilities."}'
```

---

## Requirements

| Requirement | Version | Notes |
|---|---|---|
| **n8n** | 1.0+ | Self-hosted ([install guide](https://docs.n8n.io/hosting/)) |
| **Ollama** | 0.1.0+ | Local AI runtime ([ollama.com](https://ollama.com)) |
| **llama3.1:8b** | - | Default model used by all workflows |

### Quick Setup

1. **Install Ollama** (if you haven't already):
   ```bash
   curl -fsSL https://ollama.com/install.sh | sh
   ```

2. **Pull the required model:**
   ```bash
   ollama pull llama3.1:8b
   ```

3. **Make sure Ollama is running:**
   ```bash
   ollama serve
   ```

4. **Verify it works:**
   ```bash
   curl http://localhost:11434/api/tags
   ```

---

## Installation

1. Open your n8n instance (usually `http://localhost:5678`)
2. Go to **Workflows** > **Add Workflow** > **Import from File**
3. Select any `.json` file from the `workflows/` folder
4. Activate the workflow
5. Test using the `curl` commands above

> **Tip:** You can swap `llama3.1:8b` for any Ollama model. Smaller models like `phi3:mini` are faster; larger models like `llama3.1:70b` give better results.

---

## Want All 11 Workflows?

These 3 free templates are just the beginning. The complete **Self-Hosted AI Workflow Pack** includes **11 production-ready workflows**:

| # | Workflow | Description |
|---|---|---|
| 1 | AI Text Summarizer | Summarize any text via API *(included here)* |
| 2 | AI Sentiment Analyzer | Analyze sentiment with emotions *(included here)* |
| 3 | AI Keyword Extractor | Extract keywords & entities *(included here)* |
| 4 | AI Email Auto-Responder | Classify & draft replies to emails |
| 5 | AI Blog Writer | Generate full blog posts from topics |
| 6 | AI Social Content Generator | Create platform-specific social posts |
| 7 | AI Document Summarizer & Q&A | Summarize docs + generate Q&A |
| 8 | AI Lead Scorer | Score and prioritize leads |
| 9 | AI Support Ticket Router | Auto-classify and route tickets |
| 10 | AI Meeting Notes | Extract action items from transcripts |
| 11 | AI Data Extractor | Pull structured data from unstructured text |

All workflows use **Ollama** for local AI -- no API keys, no recurring costs, complete data privacy.

### [Get the complete Self-Hosted AI Workflow Pack](https://bonskari.github.io/n8n-ai-workflows/)

---

## Customization Tips

- **Change the model:** Edit the `model` field in the Ollama HTTP Request node. Try `mistral`, `phi3`, `gemma2`, or any model from the [Ollama library](https://ollama.com/library).
- **Adjust creativity:** Lower `temperature` (0.1) for factual tasks, higher (0.7+) for creative output.
- **Increase output length:** Raise `num_predict` in the request options for longer responses.
- **Add authentication:** Enable header auth on the Webhook node for production use.

---

## Troubleshooting

| Issue | Solution |
|---|---|
| "Connection refused" on Ollama calls | Make sure Ollama is running: `ollama serve` |
| Slow responses | Try a smaller model: `phi3:mini` or `gemma2:2b` |
| "Model not found" | Pull the model first: `ollama pull llama3.1:8b` |
| Webhook not responding | Ensure the workflow is **activated** in n8n |
| Timeout errors | Increase the timeout in the HTTP Request node options |

---

## Like These Workflows? Give This Repo a Star!

If these templates saved you time or taught you something new, **please consider starring this repo** -- it helps other n8n users find these free resources and motivates us to release more.

### More from Bonskari

| Resource | Description |
|---|---|
| [**Self-Hosted AI Workflow Pack**](https://bonskari.github.io/n8n-ai-workflows/) | All 11 production-ready n8n + Ollama workflows. One-time purchase, lifetime updates, no subscriptions. |
| [**n8n-ai-workflows**](https://github.com/bonskari/n8n-ai-workflows) | Landing page and documentation for the full workflow pack. |
| [**n8n-workflow-pack**](https://github.com/bonskari/n8n-workflow-pack) | Additional workflow templates and resources for n8n power users. |

### Why Self-Hosted AI?

- **Zero recurring costs** -- no per-token API fees, no monthly subscriptions
- **Complete data privacy** -- your documents, emails, and business data never leave your machine
- **No rate limits** -- process as much as you want, as fast as your hardware allows
- **Works offline** -- no internet dependency for AI processing

> **New here?** Start with the 3 free workflows above, then check out the [full pack](https://bonskari.github.io/n8n-ai-workflows/) when you're ready to automate more.

---

## License

These workflow templates are provided free for personal and commercial use. Attribution is appreciated but not required.

---

**Built with [n8n](https://n8n.io) + [Ollama](https://ollama.com)**
