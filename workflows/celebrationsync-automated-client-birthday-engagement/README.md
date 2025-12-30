# 🎂 CelebrationSync — Automated Birthday Engagement

[![n8n workflow](https://img.shields.io/badge/n8n-workflow-blue?logo=n8n&style=flat)](https://n8n.io) [![License](https://img.shields.io/badge/license-UNSPECIFIED-lightgrey?style=flat)](LICENSE)

> Automated, personalized birthday outreach for clients and employees using Airtable + Gmail.

> — Runs daily and delivers friendly, templated email greetings.

---

## Features

- **Daily scheduling:** Executes automatically each morning for reliable outreach.
- **Airtable integration:** Filters records by day/month to match today's birthdays.
- **Personalized delivery:** Sends templated, individualized emails via Gmail.
- **Scalable batching:** Uses split/batch processing to handle large contact lists safely.

## Prerequisites

- n8n (cloud or self-hosted) with access to credentials management.
- Airtable base with `First Name`, `Email`, and `Birthday` fields.
- Gmail (OAuth2) or another mail provider configured as credentials in n8n.

# ## Quick Start — Import & Configure

1. Open n8n → Import → From File, then paste the `workflow.json` from this repository.
2. Add credentials in n8n:
   - Airtable: Personal Access Token / API key.
   - Gmail: OAuth2 credentials.
3. Update the Airtable node to reference your base/table and verify field mappings.
4. Activate the workflow; the schedule trigger will run at its configured time.

## Workflow Overview

- `Schedule Trigger` — Runs daily at the configured hour.
- `Airtable (Search Records)` — Uses a day/month formula to find today's birthdays.
- `SplitInBatches` — Processes records in batches for stability.
- `Gmail (Send Email)` — Sends personalized messages using templated fields.

## Recommended Airtable Formula

Use this formula to match month/day and ignore year:

```text
AND( DAY({Birthday}) = DAY(TODAY()), MONTH({Birthday}) = MONTH(TODAY()) )
```

## Customization Ideas

- Use an `If` node to send different templates for clients, VIPs, or employees.
- Add an Airtable `Update` node to log that an email was sent (timestamp).
- Add Slack/Teams notifications for internal visibility on VIP birthdays.

## Troubleshooting

- No matches: confirm `Birthday` is a proper date field and populated.
- Email failures: verify Gmail OAuth credentials and check n8n execution logs.

## Contributing & Support

Contributions welcome — open an issue or submit a pull request describing the change.

## License & Contact

This repository contains workflow configuration and documentation. Add or clarify licensing information as needed.

For setup help or questions, open an issue or contact the maintainer.

---

_Last updated: December 2025_
