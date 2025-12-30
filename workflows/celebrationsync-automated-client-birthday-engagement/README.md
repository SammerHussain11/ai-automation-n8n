**CelebrationSync — Automated Birthday Engagement**

CelebrationSync is an n8n workflow that automates personalized birthday outreach for clients, employees, or contacts stored in Airtable. It runs daily, finds matching birthdays (ignoring year), and sends tailored emails via Gmail.

**Features**

- **Daily scheduling:** Runs automatically each morning to ensure timely outreach.
- **Airtable integration:** Queries records by day/month to find today's birthdays.
- **Personalized email delivery:** Sends individualized messages via Gmail using recipient fields.
- **Scalable batching:** Processes multiple recipients safely using split/batch logic.

**Prerequisites**

- n8n (self-hosted or cloud) with a working execution environment.
- An Airtable base containing contact records with at least `First Name`, `Email`, and `Birthday` fields.
- A Gmail account configured in n8n (OAuth2 credentials) or another mail provider node.

**Quick Start — Import & Configure**

1. Open n8n and choose Import > From File, then paste the `workflow.json` included in this repository.
2. Create credentials in n8n for Airtable and Gmail:
   - Airtable: Personal Access Token or API key with access to the target base and table.
   - Gmail: OAuth2 credentials configured in n8n.
3. Update the Airtable node to point to your Base and Table, and verify the date formula or filter field mappings.
4. Set the workflow to Active mode. The schedule trigger will run at its configured time.

**Workflow Overview (nodes summary)**

- `Schedule Trigger` — Runs daily at the chosen hour.
- `Airtable (Search Records)` — Finds records where DAY({Birthday}) = DAY(TODAY()) and MONTH({Birthday}) = MONTH(TODAY()).
- `SplitInBatches` — Processes individual records in manageable chunks.
- `Gmail (Send Email)` — Sends a personalized message to each matched contact; subject and body are templated with `{{ $json["First Name"] }}` and other fields.

**Recommended Airtable Formula**
Use a formula that ignores year and matches month/day, for example:

```text
AND( DAY({Birthday}) = DAY(TODAY()), MONTH({Birthday}) = MONTH(TODAY()) )
```

**Customization Ideas**

- Add an `If` node to use different templates for clients, VIPs, or employees.
- Add a CRM update node to write a timestamp back to Airtable after a message is sent.
- Add Slack or Teams notifications for internal visibility on VIP events.

**Troubleshooting**

- If no results are returned, confirm the `Birthday` field uses a valid date format and contains values.
- If emails are not sending, verify Gmail credentials and review n8n execution logs for SMTP/OAuth errors.

**Contributing & Support**
If you want enhancements or fixes, open an issue or submit a pull request outlining the change and rationale.

**License & Contact**
This repository contains workflow configurations and documentation. Clarify licensing or usage terms here if needed.

For questions or help with setup, open an issue or contact the maintainer.

---

_Last updated: December 2025_
