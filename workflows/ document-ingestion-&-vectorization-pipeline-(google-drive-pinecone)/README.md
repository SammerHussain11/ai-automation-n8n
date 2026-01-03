# Document Ingestion & Vectorization Pipeline (Google Drive → Pinecone)

## Overview

This n8n workflow searches a Google Drive folder, downloads files, processes them in batches, generates embeddings via Google Gemini, and inserts vectors into a Pinecone index.

## Removed sensitive information

To make this repository safe for public push, all credential identifiers and environment instance IDs have been removed from the workflow JSON. Placeholders were used where needed:

- Google Drive folder ID: REPLACE_WITH_DRIVE_FOLDER_ID
- All node credential objects were cleared.

## How to configure locally

1. Copy this workflow JSON back into n8n (Import).
2. For each node that requires credentials, open the node and re-select or create credentials in your local n8n instance:
   - Google Drive: set up OAuth2 credentials in n8n UI.
   - Google Gemini (PaLM): add your Google API credentials.
   - Pinecone: add your Pinecone API key and environment.
3. Replace the placeholder folder ID with the actual Google Drive folder ID in the node's filter.

## Security best practices

- Never commit API keys, OAuth client secrets, or provider-specific credential IDs.
- Use environment variables or n8n's credential manager for secrets.
- Rotate keys if they have been accidentally committed in the past.

## Running

1. Ensure credentials are added in n8n.
2. Import the workflow and activate or execute manually for testing.

## Support

For issues with node configuration, consult n8n documentation:
https://docs.n8n.io/
