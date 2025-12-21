# Automated Business Outreach & Personalized Email Follow-Up

## Overview

This n8n workflow automates business outreach by fetching user information from a Google Sheets spreadsheet, sending personalized email follow-ups via Gmail, and updating the spreadsheet to track sent emails. The workflow is designed to streamline outreach efforts, ensuring each contact receives a tailored message based on their first name.

## Prerequisites

Before setting up and running this workflow, ensure you have the following:

- **n8n Instance**: An active n8n installation (self-hosted or cloud-based).
- **Google Account**: With access to Google Sheets and Gmail APIs.
- **OAuth Credentials**: Set up OAuth2 for Google Sheets and Gmail in n8n.
- **Google Sheets Document**: A spreadsheet containing user data with columns like "First Name", "Last Name", "Email", "submittedAt", etc.
- **Environment Variables**: Configure the `.env` file with necessary secrets (see Configuration section).

## Setup

1. **Clone or Download the Workflow**:

   - Import the `workflow.json` file into your n8n instance.

2. **Install Required Nodes**:

   - Ensure the following n8n nodes are available:
     - `n8n-nodes-base.manualTrigger`
     - `n8n-nodes-base.googleSheets`
     - `n8n-nodes-base.splitInBatches`
     - `n8n-nodes-base.gmail`

3. **Configure Credentials**:

   - In n8n, set up OAuth2 credentials for Google Sheets and Gmail.
   - Update the credential IDs in the workflow nodes to match your configured credentials.

4. **Prepare Google Sheets**:
   - Create or use an existing Google Sheets document.
   - Ensure the sheet has the required columns: "First Name", "Last Name", "Email", "submittedAt", "Email Sent", etc.
   - Share the document appropriately if needed.

## Configuration

Create a `.env` file in the root directory of your n8n project or wherever the workflow is hosted. Populate it with the following variables (replace placeholders with actual values):

```env
# Google Sheets Configuration
GOOGLE_SHEETS_DOC_ID=your_google_sheets_document_id
GOOGLE_SHEETS_OAUTH_CREDENTIAL_ID=your_google_sheets_oauth_credential_id

# Gmail Configuration
GMAIL_OAUTH_CREDENTIAL_ID=your_gmail_oauth_credential_id
RECIPIENT_EMAIL=your_recipient_email@example.com

# Webhook Configuration
WEBHOOK_ID=your_webhook_id
```

- **GOOGLE_SHEETS_DOC_ID**: The ID of your Google Sheets document (e.g., extracted from the URL).
- **GOOGLE_SHEETS_OAUTH_CREDENTIAL_ID**: The credential ID for Google Sheets OAuth2 in n8n.
- **GMAIL_OAUTH_CREDENTIAL_ID**: The credential ID for Gmail OAuth2 in n8n.
- **RECIPIENT_EMAIL**: The email address to send messages to (can be dynamic based on sheet data).
- **WEBHOOK_ID**: The webhook ID for the Gmail node (if applicable).

**Note**: Never commit the `.env` file to version control. Add it to your `.gitignore`.

## Running the Workflow

1. **Activate the Workflow**:

   - In n8n, activate the workflow to enable execution.

2. **Execute Manually**:

   - Click the "Execute Workflow" button in n8n to trigger the manual start node.

3. **Monitor Execution**:
   - View the execution logs in n8n to track progress and handle any errors.

## Workflow Explanation

The workflow consists of the following steps:

1. **Manual Trigger**: Initiates the workflow execution.

2. **Get Rows from Google Sheets**: Retrieves all rows from the specified Google Sheets document and sheet.

3. **Loop Over Items**: Processes each row individually using a batch splitter.

4. **Send Email via Gmail**: Sends a personalized email to the recipient using data from the sheet (e.g., "Hello, [First Name]").

   - Subject: "Hello, {{ $json['First Name'] }}"
   - Message: "How can I help you to grow your business."

5. **Update Google Sheets**: Marks the row as "Email Sent": "Success" and updates the "submittedAt" field.

6. **Loop Back**: Continues processing the next item in the batch.

## Notes

- **Error Handling**: Implement error handling nodes in n8n for production use to manage API failures or invalid data.
- **Rate Limits**: Be aware of Gmail and Google Sheets API rate limits to avoid throttling.
- **Personalization**: Customize the email content further by adding more dynamic fields from the sheet.
- **Security**: Ensure OAuth credentials are securely managed and rotated periodically.
- **Testing**: Test the workflow with sample data before running on live contacts.

## Contributing

If you wish to contribute improvements or modifications, please fork the repository and submit a pull request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
