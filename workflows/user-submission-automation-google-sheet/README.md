# User Submission Automation (Google Sheets + Gmail)

## Overview

This n8n workflow automates the process of collecting user submissions from a web form and appending the data to a Google Sheets spreadsheet. The workflow is designed to streamline user registration processes by capturing essential information and storing it in a centralized, accessible format.

## Workflow Description

The automation consists of two main components:

1. **Form Trigger**: A web form that collects user information including:

   - First Name (required)
   - Last Name (required)
   - Email (required)

2. **Google Sheets Integration**: Automatically appends the collected data to a specified Google Sheets document, including additional metadata such as submission timestamp and form mode.

## Prerequisites

- n8n instance (self-hosted or cloud)
- Google account with access to Google Sheets
- Google Sheets API credentials configured in n8n

## Setup Instructions

1. **Import the Workflow**:

   - Import the `User Submission Automation (Google Sheets + Gmail).json` file into your n8n instance.

2. **Configure Environment Variables**:

   - Create a `.env` file in the same directory as the workflow file.
   - Add the following environment variables with your specific values:
     ```
     GOOGLE_SHEETS_DOCUMENT_ID=your_google_sheets_document_id
     GOOGLE_SHEETS_SHEET_NAME=your_sheet_name_or_gid
     WEBHOOK_ID=your_webhook_id
     GOOGLE_SHEETS_CREDENTIAL_ID=your_google_sheets_credential_id
     INSTANCE_ID=your_n8n_instance_id
     ```

3. **Configure Google Sheets Credentials**:

   - Ensure you have a Google Sheets OAuth2 API credential set up in n8n.
   - The credential ID should match the value in your `.env` file.

4. **Activate the Workflow**:
   - Set the workflow status to active in n8n.
   - The form will be accessible via the webhook URL provided by the "On form submission" node.

## Data Flow

1. User submits the form with their details.
2. n8n receives the form data via the webhook.
3. The data is automatically appended to the Google Sheets document.
4. Additional fields (submittedAt, formMode, City) are included in the sheet for enhanced tracking.

## Customization

- **Form Fields**: Modify the form fields in the "On form submission" node to add or remove required information.
- **Sheet Columns**: Adjust the column mapping in the "Append row in sheet" node to match your spreadsheet structure.
- **Additional Processing**: Extend the workflow by adding nodes for email notifications, data validation, or integrations with other services.

## Security Considerations

- Ensure proper access controls on the Google Sheets document.
- Consider implementing rate limiting or CAPTCHA on the form to prevent abuse.
- Regularly review and clean up collected data in accordance with privacy regulations.

## Troubleshooting

- Verify that Google Sheets API credentials are valid and have the necessary permissions.
- Check the n8n logs for any execution errors.
- Ensure the webhook URL is correctly configured and accessible.

## Future Enhancements

- Integration with Gmail for automated confirmation emails (as indicated in the workflow name).
- Data validation and sanitization steps.
- Dashboard for viewing submission analytics.

---

_This workflow is currently inactive. Activate it in n8n to start collecting user submissions._
