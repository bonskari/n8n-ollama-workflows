# n8n + Ollama AI Workflow Templates (Free, Self-Hosted)

**5 free n8n workflow templates powered by Ollama. Run AI automations locally — no API keys, no cloud, no monthly fees, complete data privacy.**

[![n8n](https://img.shields.io/badge/n8n-v1.0+-orange)](https://n8n.io)
[![Ollama](https://img.shields.io/badge/Ollama-local_AI-blue)](https://ollama.com)
[![License](https://img.shields.io/badge/license-free-green)](LICENSE)

Import any workflow JSON into your self-hosted n8n instance and start automating with local AI in under 5 minutes. Every workflow runs 100% on your machine using Ollama — your data never leaves your network.

> **Want all 11 workflows?** These 5 are free samples from the [Self-Hosted AI Workflow Pack](https://bonskari.github.io/n8n-ai-workflows/) ($39 one-time, no subscription). The full pack adds email auto-response, lead scoring, meeting notes extraction, competitor monitoring, content repurposing, and more.

---

## Workflows Included

| # | Workflow | What It Does | File |
|---|---------|-------------|------|
| 1 | **AI Social Media Content Generator** | Enter a topic → get ready-to-post content for Twitter/X, LinkedIn, Reddit, and Instagram with AI quality review | [`ai-social-content-generator.json`](workflows/ai-social-content-generator.json) |
| 2 | **AI Document Summarizer & Q&A** | Send any document via webhook → get structured summary + auto-generated Q&A pairs | [`ai-document-summarizer.json`](workflows/ai-document-summarizer.json) |
| 3 | **AI Text Summarizer** | POST any text → get executive summary, key bullet points, and tone detection | [`text-summarizer.json`](workflows/text-summarizer.json) |
| 4 | **AI Sentiment Analyzer** | Analyze sentiment of single or batch texts with emotions, confidence scores, and reasoning | [`sentiment-analyzer.json`](workflows/sentiment-analyzer.json) |
| 5 | **AI Keyword & Entity Extractor** | Extract keywords, named entities, topics, and categories from any text | [`keyword-extractor.json`](workflows/keyword-extractor.json) |

---

## 1. AI Social Media Content Generator

**The most popular workflow in the pack.** Enter a topic and get optimized posts for 4 platforms in one click. Includes a second AI review pass that catches errors and improves engagement.

```
You enter a topic + brand voice
        ↓
AI generates content for Twitter/X, LinkedIn, Reddit, Instagram
        ↓
AI reviews & polishes everything for quality + engagement
        ↓
Ready-to-post content for each platform
```

**Features:**
- Brand voice and audience targeting built in
- Platform-specific formatting (character limits, hashtags, tone)
- AI quality review catches errors and optimizes engagement
- One click, four platforms, zero cost

**Import:** Open n8n → Workflows → Import from File → select `workflows/ai-social-content-generator.json`

---

## 2. AI Document Summarizer & Q&A

Send any document or text to the webhook endpoint and get back a structured summary plus auto-generated question-and-answer pairs — useful for study guides, documentation review, or meeting prep.

```bash
curl -X POST http://localhost:5678/webhook/summarize \
  -H "Content-Type: application/json" \
  -d '{"text": "Paste your document text here..."}'
```

**Returns:** Executive summary, key points, Q&A pairs, word count, and reading time estimate.

---

## 3. AI Text Summarizer

Accepts any text via webhook and returns a structured summary with executive summary, key bullet points, and tone detection.

```bash
curl -X POST http://localhost:5678/webhook/summarize \
  -H "Content-Type: application/json" \
  -d '{"text": "Paste a long article or document here..."}'
```

---

## 4. AI Sentiment Analyzer

Analyzes sentiment of one or multiple texts. Returns sentiment label (POSITIVE/NEGATIVE/NEUTRAL/MIXED), confidence score, detected emotions, and reasoning. Supports batch analysis — send up to 10 texts at once.

```bash
# Single text
curl -X POST http://localhost:5678/webhook/analyze-sentiment \
  -H "Content-Type: application/json" \
  -d '{"text": "I absolutely love this product! Best purchase I made all year."}'

# Batch analysis
curl -X POST http://localhost:5678/webhook/analyze-sentiment \
  -H "Content-Type: application/json" \
  -d '{"texts": ["Great service!", "Terrible experience.", "The meeting is at 3pm."]}'
```

---

## 5. AI Keyword & Entity Extractor

Extracts keywords, named entities (people, organizations, locations, dates, products), topics, and content categories from any text.

```bash
curl -X POST http://localhost:5678/webhook/extract-keywords \
  -H "Content-Type: application/json" \
  -d '{"text": "Apple CEO Tim Cook announced the new iPhone 16 at the September 2024 event in Cupertino, California."}'
```

---

## Quick Start (5 minutes)

### Requirements

| Requirement | Version | Install |
|---|---|---|
| **n8n** | 1.0+ | [Self-hosted install guide](https://docs.n8n.io/hosting/) |
| **Ollama** | 0.1.0+ | [ollama.com/download](https://ollama.com/download) |
| **Model** | llama3.1:8b | `ollama pull llama3.1:8b` |

### Setup

```bash
# 1. Install Ollama (if you haven't)
curl -fsSL https://ollama.com/install.sh | sh

# 2. Pull the model
ollama pull llama3.1:8b

# 3. Verify Ollama is running
curl http://localhost:11434/api/tags
```

### Import a workflow

1. Open n8n (`http://localhost:5678`)
2. **Workflows** → **Add Workflow** → **Import from File**
3. Select any `.json` file from the `workflows/` folder
4. Click **Activate** (toggle in top-right)
5. Test with the `curl` commands above

> **Tip:** You can swap `llama3.1:8b` for any Ollama model. `phi3:mini` is faster; `llama3.1:70b` gives better results.

---

## Why Self-Hosted AI with Ollama?

| | Cloud AI (OpenAI, etc.) | Self-Hosted (Ollama) |
|---|---|---|
| **Cost** | $20-200+/month in API fees | $0 — runs on your hardware |
| **Privacy** | Data sent to third-party servers | Data never leaves your machine |
| **Rate limits** | Throttled at high volume | Unlimited — as fast as your GPU |
| **Offline** | Requires internet | Works completely offline |
| **GDPR** | Complex compliance | Automatic — no data transfer |

---

## The Full Pack: 11 Production-Ready Workflows

These 5 free workflows are a taste of what's possible. The complete **[Self-Hosted AI Workflow Pack](https://bonskari.github.io/n8n-ai-workflows/)** includes 11 workflows covering the most common AI automation needs:

| Category | Workflows |
|---|---|
| **Content & Marketing** | AI Blog Writer, Social Media Generator *(free)*, YouTube-to-Newsletter, Content Repurposer |
| **Sales & Business** | Lead Scoring & Enrichment, Competitor Intelligence Monitor, Email Auto-Responder, Support Ticket Router |
| **Productivity** | Document Summarizer *(free)*, Meeting Notes Summarizer, Data Extractor |

**$39 one-time** — no subscription, no recurring fees. All workflows use Ollama for zero ongoing costs.

### [→ Get the full Self-Hosted AI Workflow Pack](https://bonskari.github.io/n8n-ai-workflows/)

---

## Customization

- **Change the model:** Edit the `model` field in Ollama HTTP Request nodes. Try `mistral`, `phi3`, `gemma2`, or anything from the [Ollama library](https://ollama.com/library).
- **Adjust creativity:** Lower `temperature` (0.1) for factual tasks, higher (0.7+) for creative output.
- **Increase output length:** Raise `num_predict` for longer responses.
- **Add authentication:** Enable header auth on Webhook nodes for production use.

---

## Troubleshooting

| Issue | Solution |
|---|---|
| "Connection refused" on Ollama calls | Make sure Ollama is running: `ollama serve` |
| Slow responses | Try a smaller model: `phi3:mini` or `gemma2:2b` |
| "Model not found" | Pull the model first: `ollama pull llama3.1:8b` |
| Webhook not responding | Ensure the workflow is **activated** in n8n |
| Timeout errors | Increase timeout in the HTTP Request node options |

---

## Star This Repo

If these templates saved you time, **please star this repo** — it helps other n8n users discover these free resources.

---

## More Resources

- [**Self-Hosted AI Workflow Pack**](https://bonskari.github.io/n8n-ai-workflows/) — All 11 workflows, $39 one-time
- [**n8n Documentation**](https://docs.n8n.io/) — Official n8n docs
- [**Ollama Model Library**](https://ollama.com/library) — Browse available models

---

## License

These workflow templates are provided free for personal and commercial use. Attribution appreciated but not required.

**Built with [n8n](https://n8n.io) + [Ollama](https://ollama.com)**
