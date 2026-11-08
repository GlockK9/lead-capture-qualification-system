# Lead Capture & Qualification System

An automated lead management system built with **n8n, Google Sheets, Gmail, and JavaScript**. It receives lead submissions through a webhook, validates customer information, checks for duplicate records, calculates qualification scores, stores lead data, and sends notifications for qualified leads.

The system includes both workflow-level failure handling and a dedicated error-handler workflow.

## Overview

The workflow automates the initial stages of lead management, reducing manual data entry and helping businesses identify potentially valuable leads.

Incoming submissions are evaluated using predefined qualification criteria. Each lead receives a score and is classified as either **Qualified** or **Needs Review**.

Qualified leads trigger an email notification, while all successfully processed leads are recorded in Google Sheets.

## Workflow Architecture

### 1. Lead Capture
An n8n Webhook receives incoming lead submissions through an HTTP POST request.

The system collects:
- Name
- Email
- Phone number
- Company
- Requested service
- Budget
- Message

### 2. Input Validation
The workflow checks whether the required name and email fields are present.

- Valid submissions continue processing.
- Missing required information returns an HTTP 400 response.

### 3. Duplicate Detection
Before saving a new lead, the workflow checks Google Sheets for an existing record with the same email address.

- New leads proceed to qualification.
- Duplicate submissions return an HTTP 409 Conflict response.

### 4. Lead Qualification
A JavaScript Code node calculates a qualification score using predefined criteria.

| Qualification Criteria | Points |
|---|---:|
| Budget of ₦100,000 or above | 2 |
| Service contains "automation" | 2 |
| Company information provided | 1 |
| Phone number provided | 1 |
| Message contains at least 30 characters | 1 |

**Maximum Score:** 7 points

Leads scoring 4 or above are classified as **Qualified**. Lower-scoring leads are classified as **Needs Review**.

### 5. Data Storage
Lead information, qualification scores, timestamps, and notification statuses are stored in Google Sheets.

The spreadsheet serves as the central lead management database.

### 6. Qualified Lead Notifications
Qualified leads trigger an automated Gmail notification containing their submitted information and qualification score.

The workflow subsequently updates the lead's notification status:

- `Sent` - Notification delivered successfully.
- `Failed` - Notification delivery failed.
- `Not Required` - Lead did not meet the qualification threshold.

### 7. Error Handling and Recovery

The system incorporates multiple failure-handling mechanisms.

**Workflow-Level Error Handling**
- Database save failures trigger an email alert.
- Failed database operations return an HTTP 500 response.
- Email notification failures are tracked in Google Sheets.
- Notification status is updated to `Failed` when delivery fails.

**Dedicated Error Handler**

A separate n8n error-handler workflow is configured to handle workflow execution failures. This provides an additional layer of error management beyond the main workflow's individual failure routes.

## Key Features

- Webhook-based lead collection.
- Required-field validation.
- Duplicate lead detection.
- Rule-based lead scoring.
- Automated lead qualification and routing.
- Google Sheets database integration.
- Automated qualified-lead email notifications.
- Notification delivery tracking.
- Database failure alerts.
- HTTP response handling.
- Dedicated error-handler workflow.

## Technologies Used

- **n8n:** Workflow automation and orchestration.
- **JavaScript:** Lead scoring and data processing.
- **Google Sheets API:** Lead storage and record management.
- **Gmail API:** Automated email notifications.
- **REST API / HTTP:** Webhook communication.
- **JSON:** Structured data exchange.
- **Postman:** Webhook testing and request validation.

## Repository Structure

- `Lead Capture & Qualification System.json` - Main automation workflow.
- `Lead Capture - Error Handler.json` - Dedicated error-handler workflow.
- `screenshots/` - Workflow screenshots and implementation visuals.

## Setup and Configuration

1. Install or access an n8n instance.
2. Import the main workflow JSON into n8n.
3. Import the dedicated error-handler workflow.
4. Configure Google Sheets credentials and connect the lead management spreadsheet.
5. Configure Gmail credentials.
6. Assign the dedicated error workflow in the main workflow's settings.
7. Ensure the Google Sheet contains the required columns.
8. Activate the workflows.
9. Test the webhook using Postman with valid, incomplete, duplicate, and different lead submissions.

**Note:** Credentials and account-specific configurations must be supplied by the user. The exported workflow does not provide access to the original connected accounts.

## Project Objectives

This project demonstrates practical implementation of:

- API and webhook integration.
- Workflow orchestration.
- Conditional logic and data validation.
- JavaScript-based business rules.
- Database operations and record management.
- Automated email communication.
- Error handling and execution monitoring.

The objective is to create a structured lead management process that captures, evaluates, stores, and routes incoming business enquiries with minimal manual intervention.

<img width="932" height="255" alt="Screenshot 1" src="https://github.com/user-attachments/assets/d979944a-1c96-4583-8643-e463d13d06d3" />
<img width="972" height="551" alt="Screenshot 2" src="https://github.com/user-attachments/assets/5848aaba-0dd1-4fe4-b600-4ca5db6d3bc7" />
<img width="1011" height="466" alt="Screenshot 3" src="https://github.com/user-attachments/assets/8d8cfacb-1010-450f-80d2-35e47825cba3" />
<img width="876" height="602" alt="Screenshot 9" src="https://github.com/user-attachments/assets/3d466961-3677-4958-a6b1-783ba972e957" />
