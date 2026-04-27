# 📨 NeuralGate: AI-Powered Email-to-WhatsApp Sentinel

[![n8n](https://img.shields.io/badge/Workflow-n8n-FF6D5B?style=flat-square&logo=n8n)](https://n8n.io)
[![OpenAI](https://img.shields.io/badge/AI-OpenAI_GPT--4o-412991?style=flat-square&logo=openai)](https://openai.com)
[![Twilio](https://img.shields.io/badge/Messaging-Twilio-F22F46?style=flat-square&logo=twilio)](https://twilio.com)

**NeuralGate** is an intelligent automation workflow that acts as a 24/7 personal assistant. It monitors your Gmail, filters out the noise using AI, and sends high-priority notifications directly to your WhatsApp.

---

## ✨ Key Features
- **Smart Classification:** Uses LLM logic to distinguish between recruiters, clients, and newsletters.
- **Noise Suppression:** Multi-layer filtering (Keywords + AI Confidence) to keep your notifications clean.
- **Cost Efficient:** Pre-filters emails before sending them to AI to minimize token usage.
- **Aesthetic Alerts:** Delivers structured, easy-to-read WhatsApp summaries.

---

## 🏗️ The Architecture
The workflow follows a 4-step professional pipeline:

1.  **Trigger:** Watches Gmail for new incoming mail.
2.  **Sanitization:** Cleans HTML junk and filters common spam (unsubscribe/no-reply).
3.  **Brain (AI):** OpenAI analyzes the intent and assigns a `Confidence Score`.
4.  **Action:** If `Confidence > 75`, a formatted alert is sent via Twilio WhatsApp API.

---

## 🚀 Setup Guide

### 1. Prerequisites
- **n8n** (Self-hosted or Cloud)
- **OpenAI API Key** (For classification)
- **Twilio Account** (For WhatsApp notifications)
- **Gmail API** (Google Cloud Console credentials)

### 2. Installation
1. Download the `workflow.json` file from this repo.
2. Open your n8n instance.
3. Click **Import from File** and select the JSON.
4. Update the credentials for Gmail, OpenAI, and Twilio.

### 3. AI Configuration
The AI is tuned via a system prompt to return a strict JSON output:
```json
{
  "status": "IMPORTANT",
  "category": "job_opportunity",
  "reason": "Recruiter from Google reached out for a Lead role.",
  "confidence": 95
}
