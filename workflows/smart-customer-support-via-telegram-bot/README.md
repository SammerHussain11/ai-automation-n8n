# TeleSupportX

Automated Telegram Customer Support & Ticket Logging Workflow built with n8n.

---

## 📌 Overview

TeleSupportX is a production-ready Telegram-based customer support automation workflow developed using n8n.  
It intelligently processes customer messages, categorizes requests, provides instant responses, escalates issues to human agents, and logs all interactions into Google Sheets for tracking and analysis.

---

## ✨ Features

- Telegram Bot integration
- Automatic user data extraction
- Intent-based request handling
- Order status support
- FAQ automation
- Billing & payment assistance
- Human agent escalation
- Google Sheets logging
- Default fallback responses
- Scalable and modular workflow design

---

## 🧠 Workflow Architecture

1. Telegram Bot Trigger receives incoming messages
2. User data is extracted and normalized
3. Message intent is detected using conditional logic
4. Appropriate response is sent to the user
5. Interaction data is logged in Google Sheets
6. Human escalation requests are notified and recorded

---

## 🧾 Supported Commands

| Command  | Description                     |
| -------- | ------------------------------- |
| /start   | Show welcome message            |
| /help    | Display help menu               |
| /faq     | Show frequently asked questions |
| /status  | Order status guidance           |
| /contact | Escalate to human support       |

---

## 📊 Logging & Monitoring

### Bot Interaction Logs

Stored in Google Sheets with the following fields:

- Timestamp
- User ID
- Username
- Message
- Chat ID

### Support Escalation Logs

- User details
- Message content
- Escalation time
- Chat ID

---

## 🛠️ Tech Stack

- Automation Platform: n8n
- Messaging Platform: Telegram Bot API
- Data Storage: Google Sheets
- Deployment: Self-hosted n8n (Local / VPS / Docker)

---

## ⚙️ Setup Instructions

### Requirements

- n8n (self-hosted)
- Telegram Bot Token
- Google Sheets OAuth credentials

### Installation Steps

1. Import the workflow JSON into n8n
2. Configure Telegram Bot credentials
3. Update placeholder values:
   - YOUR_WEBHOOK_ID
   - YOUR_SUPPORT_TEAM_CHAT_ID
4. Connect Google Sheets credentials
5. Activate the workflow

---

## 🔐 Security Notes

- Keep Telegram Bot tokens private
- Restrict Google Sheets access
- Use environment variables in production environments

---

## 🚀 Future Enhancements

- AI-based intent classification
- Ticket ID generation
- CRM integrations
- SLA monitoring
- Admin dashboard
- Multi-language support

---

## 📄 License

This project is available for educational and commercial use.  
You are free to modify and extend it.

---

## 🔗 References

- n8n Documentation: https://docs.n8n.io
- Telegram Bot API: https://core.telegram.org/bots/api
- Google Sheets API: https://developers.google.com/sheets/api
