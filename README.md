# Lead Capture & Qualification System

An n8n workflow automation system designed to capture incoming leads, validate submitted information, evaluate lead quality, and manage lead records and notifications.

## Project Overview

The system receives lead submissions through a webhook, validates the information, calculates a qualification score, assigns a qualification status, and stores the results in Google Sheets.

Qualified leads can trigger automated email notifications, while leads that require further review are identified accordingly.

## Workflow Architecture

### 1. Lead Capture & Qualification Workflow

1. **Webhook Trigger:** Receives incoming lead submissions.
2. **Input Validation:** Checks submitted lead information.
3. **Lead Scoring:** Evaluates leads using defined qualification criteria.
4. **Lead Classification:** Assigns a qualification status.
5. **Data Storage:** Saves lead information and scoring results in Google Sheets.
6. **Notification:** Sends automated email notifications when applicable.

### 2. Lead Capture Error Handler

A separate error-handling workflow designed to manage failures within the main Lead Capture workflow.

- Detects workflow execution errors.
- Captures relevant error information.
- Supports centralized error monitoring and reporting.
- Helps make the automation more reliable.

### Workflow Integration

The main Lead Capture workflow handles lead processing, while the Error Handler manages execution failures separately.
## Technologies Used

- n8n
- Webhooks
- JavaScript
- JSON
- Google Sheets
- Gmail
- REST API concepts

## Key Features

- Automated lead capture.
- Input validation.
- Rule-based lead scoring.
- Lead qualification and classification.
- Google Sheets integration.
- Conditional email notifications.
- Error handling.

## Repository Contents

- Exported n8n workflow JSON.

## Setup

1. Import the JSON file into your n8n instance.
2. Configure the required Google Sheets and Gmail credentials.
3. Configure the webhook.
4. Review the scoring and qualification logic.
5. Activate the workflow and test with sample lead submissions.

**Note:** Credentials and environment-specific configurations are not included in the exported workflow.

## Project Purpose

Built to demonstrate workflow automation, API integration, data validation, conditional logic, lead

<img width="932" height="255" alt="Screenshot 1" src="https://github.com/user-attachments/assets/d979944a-1c96-4583-8643-e463d13d06d3" />
<img width="972" height="551" alt="Screenshot 2" src="https://github.com/user-attachments/assets/5848aaba-0dd1-4fe4-b600-4ca5db6d3bc7" />
<img width="1011" height="466" alt="Screenshot 3" src="https://github.com/user-attachments/assets/8d8cfacb-1010-450f-80d2-35e47825cba3" />
<img width="876" height="602" alt="Screenshot 9" src="https://github.com/user-attachments/assets/3d466961-3677-4958-a6b1-783ba972e957" />
