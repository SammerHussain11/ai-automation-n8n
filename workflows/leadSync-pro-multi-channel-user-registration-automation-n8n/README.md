# 🚀 LeadSync Pro – Multi-Channel User Registration Automation (n8n)

**LeadSync Pro** is a production-ready **n8n automation workflow** designed to capture user registrations through a public form and synchronize the data across **Airtable**, **Google Sheets**, and **Gmail** with guaranteed delivery tracking.

This workflow is ideal for **consulting agencies, SaaS platforms, startups, and service-based businesses** that require reliable lead intake, storage, and automated communication.

---

## ✨ Key Features

- ✅ Public **User Registration Form**
- 📊 Centralized CRM storage using **Airtable**
- 📄 Parallel logging in **Google Sheets**
- ✉️ Automated confirmation email via **Gmail**
- 🔄 Post-email status update in Google Sheets
- ⚙️ Modular, scalable, and production-safe workflow design

---

## 🧠 Workflow Logic Overview

User Form Submission
│
├──► Google Sheets (Append Row)
│
└──► Airtable (Create CRM Record)
│
└──► Gmail (Send Confirmation Email)
│
└──► Google Sheets (Update Status: Email Sent)

---

## 🧩 Nodes Used

| Node                   | Purpose                           |
| ---------------------- | --------------------------------- |
| Form Trigger           | Captures user input               |
| Airtable               | Stores structured lead data (CRM) |
| Google Sheets (Append) | Logs raw submissions              |
| Gmail                  | Sends confirmation email          |
| Google Sheets (Update) | Updates email delivery status     |

---

## 📝 Captured Form Fields

- **First Name** (Required)
- **Last Name** (Required)
- **Email Address** (Validated & Required)
- **Date of Birth** (Required)

---

## ⚙️ Requirements

Before using this workflow, make sure you have:

- n8n (Self-Hosted or Cloud)  
  https://docs.n8n.io/

- Airtable Personal Access Token  
  https://airtable.com/developers/web/api/introduction

- Google Sheets API credentials  
  https://developers.google.com/sheets/api

- Gmail API credentials  
  https://developers.google.com/gmail/api

---

## 📥 Installation Steps

1. Clone this repository
2. Import the workflow JSON into n8n
3. Configure credentials:
   - Airtable Personal Access Token
   - Google Sheets OAuth
   - Gmail OAuth
4. Update:
   - Airtable Base ID & Table ID
   - Google Sheet ID & Sheet Name
5. Activate the workflow
6. Share the public form URL

---

## 📧 Email Automation Behavior

- Automatically sends a confirmation email to the user
- Confirms successful delivery
- Updates Google Sheet row with **“Email Sent”** status
- Prevents silent failures and ensures traceability

---

## 🔐 Data Reliability Strategy

- Dual-storage architecture (Airtable + Google Sheets)
- API typecasting enabled to prevent schema conflicts
- Status-based updates instead of overwriting records

---

## 🎯 Use Cases

- Lead generation
- Free consultation requests
- Client onboarding
- Event registrations
- SaaS sign-up flows

---

## 🛠️ Recommended Enhancements

- Duplicate email detection
- Slack / Telegram admin alerts
- Error-handling & retry branches
- Spam filtering & CAPTCHA
- Webhook-based CRM extensions

---

## 👤 Author

**Samar Hussain**  
Automation Engineer | n8n Workflow Specialist

---

## 📄 License

This project is licensed for **educational and commercial use**.  
You are free to modify and extend it responsibly.
