# AI-powered LinkedIn Lead Outreach Automation (n8n workflow)

A reusable n8n workflow that automates LinkedIn lead outreach: reads leads from Google Sheets, uses an AI agent to draft/send outreach emails, and updates the sheet status.

## Features

- Read leads from Google Sheets
- Per-row processing (split in batches)
- AI agent (LangChain) + Google Gemini (PaLM) integration for drafting actions
- Send email via Gmail and update sheet status

## Prerequisites

- n8n instance (self-hosted or cloud)
- Google Sheets API credentials (OAuth2)
- Gmail OAuth2 credentials
- Google PaLM / Gemini API credentials (if using the AI model)
- This repository contains the exported n8n workflow JSON (sensitive values redacted)

## Setup / How to import

1. Import `Send Invoice.json` into n8n (Workflows → Import).
2. Reconfigure credentials in n8n:
   - Google Sheets OAuth2 credential
   - Gmail OAuth2 credential
   - Google PaLM / Gemini credential
3. Replace placeholders in the imported workflow where noted:
   - `<REDACTED_SHEET_ID>` and `<REDACTED_SHEET_URL>` → your Google Sheet ID/URL (or reselect the sheet in node settings)
   - `recipient@example.com` → desired recipient address or change to dynamic expression (e.g. `={{ $json.Email }}`)
   - Any credential IDs/names will be set automatically when you choose credentials inside n8n

## Security & Privacy

- All sensitive credential IDs, webhook IDs, and direct personal emails were redacted from the checked-in JSON. Do not commit credentials or private keys to the repository.
- Store and configure credentials securely inside your n8n instance or via environment variables managed outside version control.

## Notes

- Verify node mappings and column names match your sheet before running.
- Test the workflow in a non-production environment first.

If you want, I can produce a version of the workflow that uses environment variables or expressions for all dynamic values to make reconfiguration easier.
