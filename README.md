## Smart Webhook Digest | n8n Workflow

A powerful and customizable n8n workflow that collects data from multiple webhook sources (like form submissions, monitoring alerts, or API events) and bundles them into a single, organized digest message. The digest is sent on a schedule to your preferred channel (e.g., Slack, Email), reducing notification noise and providing a clear daily summary.

_____________

## 🌟 Features

-Multi-Source Aggregation: Collect data from any service that can send a webhook (e.g., Typeform, GitHub, monitoring tools, custom apps).

-Scheduled Digests: Receive summaries on your own schedule (e.g., daily, hourly, weekly) without constant interruptions.

-Multiple Outputs: Send the digest to Slack, Email, Microsoft Teams, or any other supported n8n service.

-Fully Customizable: Easily modify the code logic to format the digest, add new sources, or change conditions.

-Low-Code: Built visually in n8n with minimal JavaScript required.
______________________________________
## 🏗️ How It Works

### The workflow is built on a simple but powerful principle: Collect now, process later.

-Collection: Dedicated webhook nodes act as endpoints, receiving and storing payloads from external services.

-Trigger: A scheduler node (e.g., a daily cron job) activates the workflow.

-Processing: The workflow fetches all data received since the last trigger, processes it (e.g., counts events, formats messages), and generates a summary.

-Delivery: The final digest is sent to a notification channel like Slack.
______________________________________
## 📋 Prerequisites

### Before you import this workflow, ensure you have:

-An n8n instance (either self-hosted or n8n.cloud)

-Access to configure credentials in n8n (for Slack, Gmail, etc.)

-The URL of your n8n instance (e.g., https://your-n8n.example.com)
____________________________________________________
## 🚀 Installation & Setup
### 1. Import the Workflow
-Download the provided Smart-Webhook-Digest.json file from this repository.

-In your n8n instance, go to Settings > Workflows.

-Click Import and upload the JSON file.

### 2. Configure Webhook URLs
-The workflow will have two main webhook nodes. You need to get their unique URLs and provide them to your services.

-Activate the workflow.

-Open the Webhook node named 🪣 Receive Signups (or similar).

-Click Execute Node. n8n will generate a unique URL.

-Copy this URL and provide it to your form/service (e.g., in Typeform's "Webhook" section).

-Repeat the process for the 🪣 Receive Errors webhook node.

-Example Webhook URL: https://your-n8n.instance.com/webhook/signup

### 3. Configure the Schedule
-Open the Schedule Trigger node to set when you want to receive your digest.

-Cron Expression: Modify the cron expression to match your desired schedule.

-Example: 0 17 * * 1-5 (Every weekday at 5:00 PM UTC).

### 4. Configure the Destination (Slack/Email)
-For Slack:
-Ensure you have configured Slack API credentials in n8n.

-Open the Slack node.

-Select your authenticated Slack account.

-Choose the Channel where you want the digest to be posted.

-For Email (Gmail example):
-Configure Gmail API credentials in n8n.

-Open the Gmail node.

-Set the recipient email, subject, and body. Use expressions like {{ $json.summary }} to insert the digest content.

### 5. Test the Workflow
-Send test data to your webhook URLs using curl or Postman:

bash ```
# Test a signup
curl -X POST https://your-n8n.instance.com/webhook/signup \
-H "Content-Type: application/json" \
-d '{"email": "test@example.com", "name": "Test User"}'```

# Test an error
curl -X POST https://your-n8n.instance.com/webhook/error \
-H "Content-Type: application/json" \
-d '{"message": "Test Error", "severity": "high"}'```
