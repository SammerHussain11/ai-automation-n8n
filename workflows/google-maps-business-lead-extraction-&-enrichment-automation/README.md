# Google Maps Business Lead Extraction & Enrichment Automation

A reusable n8n workflow that extracts business listings from Google Maps, scrapes contact emails from listing pages, deduplicates results, and appends leads to a Google Sheet.

## Features

- Search Google Maps by query
- Extract listing URLs and scrape email addresses
- Deduplicate and aggregate results
- Append leads to Google Sheets

## Prerequisites

- n8n (cloud or self-hosted)
- Google Sheets OAuth2 credentials with access to the target spreadsheet
- Permission to scrape the target sites and comply with terms of service

## Setup

1. Import the workflow into your n8n instance.
2. Open the Google Sheets node and:
   - Add or select a Google Sheets OAuth2 credential in n8n.
   - Set the Spreadsheet ID (replace `REDACTED_SHEET_ID`) and Sheet name (replace `REDACTED_SHEET_NAME`).
3. Review other nodes for any site-specific adjustments (queries, regexes, batch sizes).
4. Test the workflow using the manual trigger.

## Security / Notes

- Sensitive items (OAuth credential IDs, spreadsheet IDs, and cached URLs) have been redacted in the committed workflow. Reconfigure them in your n8n environment; do not commit secrets to version control.
- Ensure scraping complies with target sites' terms of service and local laws.

## Contributing

- Open an issue or PR with improvements or bug fixes.
- Keep secrets out of commits; use environment variables or n8n credential storage.

## License

MIT
