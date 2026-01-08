# ProjectPulse — Slack Project Assistant

Professional, secure n8n workflow ("ProjectPulse") to power a Slack Project Assistant that reads from Google Sheets and responds via Slack using an LLM.

## Overview

This n8n workflow listens for Slack mentions/messages, routes the message through a short-term Redis memory, identifies the relevant project using an AI agent, reads authoritative project data from one of several Google Sheets, formats a concise reply using Google Gemini (PaLM), and posts the response back to Slack.

## What's in this repo

- `workflow.json` — n8n workflow (secrets replaced with placeholders).

## Placeholders in the workflow

Before importing the workflow into n8n, replace the following placeholders with your actual values via the n8n UI or by editing the JSON locally:

- `<SLACK_CHANNEL_ID>` — Slack channel ID where the bot listens and posts.
- `<SLACK_CREDENTIAL_ID>` — n8n Slack credential ID (created in n8n Credentials UI).
- `<SLACK_TRIGGER_WEBHOOK_ID>` — Slack trigger webhook identifier (n8n internal; optional to keep).
- `<SLACK_SEND_WEBHOOK_ID>` — Slack send node webhook identifier (n8n internal; optional to keep).
- `<GOOGLE_PALM_CREDENTIAL_ID>` — n8n credential ID for Google PaLM/Gemini API.
- `<GOOGLE_SHEETS_SPREADSHEET_ID>` — Google Sheets spreadsheet ID used as the Projects store.
- `<GOOGLE_SHEETS_CREDENTIAL_ID>` — n8n Google Sheets OAuth2 credential ID.
- `<GOOGLE_SHEETS_URL_PLACEHOLDER>` — Placeholder URL (for safety in repo).
- `<REDIS_CREDENTIAL_ID>` — n8n Redis credential ID.
- `<INSTANCE_ID_PLACEHOLDER>` — n8n instance identifier placeholder.

## Prerequisites

- n8n running (cloud or self-hosted). See https://docs.n8n.io/ for installation.
- Slack workspace where you can create a bot app and add it to a channel.
- Google Cloud project with access to Google Sheets and PaLM (Gemini) APIs.
- A Redis instance (for short-term chat memory).

## Quick Setup (UI import)

1. Open your n8n editor (e.g., `http://localhost:5678` or your hosted URL).
2. Click the top-right menu → `Import` → `Paste JSON` and paste the contents of `piepdrive-test (1).json`.
3. Save the workflow.

## Configure Credentials (n8n)

1. Slack

   - Create a Slack App at https://api.slack.com/apps.
   - Add `bot` token scopes required for reading channel messages and posting (e.g., `chat:write`, `channels:history`, `channels:read`, `app_mentions:read`).
   - Install the app to your workspace and obtain the Bot User OAuth Token.
   - In n8n, go to Credentials → Create `Slack` credential → paste the token and save. Use that credential in the workflow.

2. Google Sheets (OAuth2)

   - Follow n8n docs to create OAuth2 credentials for Google APIs and enable the Google Sheets API.
   - In n8n credentials, create a `Google Sheets OAuth2` credential and authorize it.
   - Update the workflow node(s) to use the created credential.

3. Google Gemini (PaLM) / LLM

   - Enable the PaLM API (or add your provider) in Google Cloud and create an API key or service account.
   - In n8n, add a `Google PaLM/Gemini` credential (as used by the `Google Gemini Chat Model` node) and set its ID in the workflow.

4. Redis
   - Provide Redis host, port, and password (if any).
   - In n8n Credentials add a `Redis` credential and reference it in the `Redis Chat Memory` node.

## Replacing placeholders

Two approaches:

- Recommended (UI): After importing the workflow, open each node with a placeholder and select the appropriate credential from the dropdowns and paste the actual channel ID.

- File edit: Edit `piepdrive-test (1).json` locally and replace placeholder strings before import.

How to get common values:

- Slack Channel ID: open Slack, right-click the channel name → `Copy Link` → the channel ID is the last segment (or use `@channel` inspect). Alternatively run `conversations.list` via Slack API.
- Google Sheets spreadsheet ID: the long ID in the sheet URL: `https://docs.google.com/spreadsheets/d/<ID>/edit`.

## Testing the workflow

1. Ensure all credentials are configured and the workflow is activated (or run manually).
2. Post a message in Slack mentioning the bot (e.g., `@YourBot status Project Alpha`).
3. Check n8n execution logs and Slack for the bot reply.

## Security & Privacy

- This repo intentionally contains placeholders instead of secrets. Never commit real tokens or private keys.
- Limit OAuth scopes to the minimum necessary.
- Protect your n8n instance (HTTPS, auth, IP restrictions) if publicly accessible.

## Troubleshooting

- Common issue: credential not authorized — re-authorize in n8n Credentials.
- LLM errors: verify Google PaLM API quota and valid credential.
- Google Sheets access: ensure the Sheets user/account has at least Viewer access to the spreadsheet.

## Contributing

If you improve this workflow or add new features (e.g., multi-workspace support, richer parsing), open a PR with a clear description and update this README with new configuration steps.

## License

Choose an appropriate license for your repository before publishing. If unsure, consider `MIT`.

---

If you want, I can also:

- Update the JSON to keep placeholder values but add comments with how to obtain each value.
- Provide a sample `.env` with recommended environment variable names for credentials.
- Commit changes to a Git branch and prepare a recommended `.gitignore`.

Tell me which next step you'd like.
