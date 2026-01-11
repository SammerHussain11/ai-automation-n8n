# LinkedIn Content Research & Image Generation Workflow

> Professional n8n workflow to research topics, generate LinkedIn posts, and produce AI images.

## Overview

This workflow accepts a simple form submission (Email, Research Topic, Target Audience), performs deep research, generates a high-quality LinkedIn post, creates an AI image prompt, produces an image, and emails the results to the submitter.

## Key Features

- Structured research-driven LinkedIn post generation
- Visual prompt engineering and AI image generation
- Optional direct posting to LinkedIn (disabled by default)
- Email delivery of post + image

## Architecture & Nodes

- `On form submission` — collects `Email`, `Research Topic`, `Target Audience`.
- `LinkedIn Post Agent` — performs deep research and drafts the post.
- `Image Prompt Agent` — generates a single image-generation prompt.
- `Generate Image` — calls an image-generation API.
- `HTTP Request` — downloads the generated image.
- `Send a message` — emails the post and image to the requester.

## Prerequisites

- n8n (self-hosted or desktop) with access to import workflows
- Accounts / API keys for:
  - Google Gemini / PaLM (language model)
  - Image generation API (Google or other)
  - Tavily (web research tool) — optional if research step is used
  - Gmail OAuth2 (to send emails) or replace with preferred SMTP/email node

## Installation & Setup

1. Open n8n and import the workflow file: `workflow.json`.
2. For each credential referenced in the workflow, create a matching credential in your n8n instance.
3. Replace placeholders (see next section) with your actual credential IDs and API keys inside n8n credential configuration — do NOT store secrets directly in the JSON file.

## Placeholders (redacted)

The exported workflow file has been sanitized. Replace these placeholders by configuring credentials within n8n:

- `<GOOGLE_PALM_CRED_ID>` — your Google Gemini / PaLM credential id in n8n
- `<TAVILY_HEADER_CRED_ID>` — Tavily HTTP header credential id in n8n
- `<TAVILY_API_KEY>` — Tavily API key (set in the credential in n8n)
- `<GOOGLE_API_KEY>` — API key used for the image generation endpoint
- `<GMAIL_OAUTH2_CRED_ID>` — your Gmail OAuth2 credential id in n8n

Important: Do not commit actual secrets or API keys to this repository. Use n8n's credential manager or environment variables.

## Execution Flow (detailed)

1. A user completes the embedded form (Email, Research Topic, Target Audience).
2. `On form submission` triggers the workflow and passes inputs to the `LinkedIn Post Agent`.
3. `LinkedIn Post Agent` performs structured research, drafts an optimized LinkedIn post, and passes the output to `Image Prompt Agent`.
4. `Image Prompt Agent` builds a single, high-quality prompt suitable for image-generation models.
5. `Generate Image` calls the configured image API with the prompt. The resulting image URL is fetched by `HTTP Request` and converted to a file.
6. `Send a message` emails the draft post and image to the submitter's email address.
7. (Optional) The `Create a post` LinkedIn node can publish the post directly; it is disabled by default.

## Testing

- Use a test email account and a non-public API key in a dev n8n instance.
- Monitor workflow executions in n8n's Executions view and review node outputs for errors.

## Security Best Practices

- Keep all API keys and OAuth credentials inside n8n's credential manager.
- Use environment variables or secrets manager for deployment automation.
- Rotate keys periodically and limit scopes to least privilege.

## Troubleshooting

- If the image generation fails, check the `Generate Image` node logs and verify the `<GOOGLE_API_KEY>` credential permissions.
- If email fails, re-authorize the Gmail OAuth credential or switch to SMTP.

## License

This README and workflow export are provided without warranty. Check licensing for any third-party APIs you use.

---

If you'd like, I can also:

- Create a `.gitignore` snippet for n8n exports
- Strip additional metadata from the export before you push
