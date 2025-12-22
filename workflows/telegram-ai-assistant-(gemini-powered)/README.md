## 🚀 Telegram AI Assistant (Gemini-powered)

This workflow connects **Telegram** with **Google Gemini AI** using **n8n**, enabling an intelligent Telegram chatbot that responds to user messages in real time.

The workflow listens for incoming Telegram messages, forwards them to a Gemini-powered AI agent for processing, and sends the AI-generated response back to the same Telegram chat.

---

## 🧠 Workflow Overview

**Flow:**

```
Telegram Trigger → AI Agent (Gemini Model) → Send Message to Telegram
```

### Nodes Used:

1. **Telegram Trigger**

   - Listens for incoming messages from users.
   - Acts as the entry point for the workflow.

2. **AI Agent**

   - Receives the user’s message.
   - Uses a connected Google Gemini chat model to generate intelligent responses.

3. **Google Gemini Chat Model**

   - Provides the Large Language Model (LLM) capabilities.
   - Processes natural language queries and returns AI-generated answers.

4. **Telegram – Send Message**

   - Sends the AI-generated response back to the user on Telegram.

---

## ⚙️ How It Works

1. A user sends a message to the Telegram bot.
2. The **Telegram Trigger** captures the message.
3. The message text is passed to the **AI Agent**.
4. The AI Agent uses **Google Gemini** to generate a response.
5. The response is sent back to the user via **Telegram Send Message**.

---

## 🛠 Requirements

- **n8n** (Self-hosted or Cloud)
- **Telegram Bot Token**
- **Google Gemini (PaLM) API Key**
- Public HTTPS webhook (ngrok, cloud, or VPS)

---

## 🔐 Environment & Credentials

This workflow uses **credentials stored securely inside n8n**.
⚠️ **Never expose API keys or tokens in public repositories.**

Before importing this workflow:

- Create Telegram credentials in n8n
- Create Google Gemini API credentials in n8n
- Reconnect credentials after importing the workflow

---

## 📦 Importing the Workflow

1. Open n8n
2. Go to **Workflows → Import**
3. Paste or upload the workflow JSON file
4. Reconnect credentials
5. Activate the workflow

---

## ⚠️ Security Notice

This repository **does not include any API keys or secrets**.
All credentials must be configured manually in your n8n instance.

---

## 📌 Use Cases

- AI-powered Telegram chatbots
- Customer support automation
- Learning assistants
- AI Q&A bots
- Educational bots

---

## 📄 License

Made by Sammer Hussain

