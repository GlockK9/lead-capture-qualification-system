# Lead Capture & Qualification System

An n8n workflow automation system designed to capture incoming leads, validate submitted information, evaluate lead quality, and manage lead records and notifications.

## Project Overview

The system receives lead submissions through a webhook, validates the information, calculates a qualification score, assigns a qualification status, and stores the results in Google Sheets.

Qualified leads can trigger automated email notifications, while leads that require further review are identified accordingly.

## Workflow Architecture

1. **Webhook Trigger:** Receives incoming lead submissions.
2. **Input Validation:** Checks submitted lead information.
3. **Lead Scoring:** Evaluates leads based on defined qualification criteria.
4. **Lead Classification:** Assigns a qualification status.
5. **Data Storage:** Records lead information and qualification results in Google Sheets.
6. **Notification:** Sends automated email notifications when applicable.
7. **Error Handling:** Supports failure detection and error management.

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
