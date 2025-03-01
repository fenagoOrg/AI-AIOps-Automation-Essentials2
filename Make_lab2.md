# Automated Customer Inquiry Response & Follow-Up Workflow

This project automates the processing of customer inquiries in real time using five components:
1. A custom webhook to receive inquiry data.
2. Logging inquiries in a Google Sheet.
3. Sending an auto-response email via the built-in Email module (Email by Make).
4. Filtering inquiries for urgency.
5. Creating a follow-up event in Google Calendar for urgent inquiries.

---

## Table of Contents
1. [Overview](#overview)
2. [Workflow Steps](#workflow-steps)
   - [Step 1: Create a Custom Webhook Trigger](#step-1-create-a-custom-webhook-trigger)
   - [Step 2: Set Up a Google Sheet to Log Inquiries](#step-2-set-up-a-google-sheet-to-log-inquiries)
   - [Step 3: Send an Auto-Response Email via Email by Make](#step-3-send-an-auto-response-email-via-email-by-make)
   - [Step 4: Add a Filter for Urgent Inquiries](#step-4-add-a-filter-for-urgent-inquiries)
   - [Step 5: Create a Follow-Up Event in Google Calendar](#step-5-create-a-follow-up-event-in-google-calendar)
3. [Finalizing and Testing](#finalizing-and-testing)
4. [Notes](#notes)

---

## Overview
This workflow processes customer inquiries in real time. It receives inquiry data through a custom webhook, logs the data in a Google Sheet, sends an auto-response email using Email by Make (configured with Microsoft SMTP), filters for urgent inquiries, and creates a follow-up event in Google Calendar for those marked as urgent.

---

## Workflow Steps

### Step 1: Create a Custom Webhook Trigger
1. Log in to [MAKE.com](https://www.make.com) and create a new scenario.
2. Click the **+ button** and search for the **Webhooks** module.
3. Select **Custom webhook** as the trigger.
4. Click **Add** to create a new webhook (e.g., **"Customer Inquiry Webhook"**). A unique webhook URL will be generated.
5. Use this URL to send inquiry data (for testing, you can use tools like Postman or MAKE.com’s testing feature).

sample image
![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/1.1.png?raw=true)
---

### Step 2: Set Up a Google Sheet to Log Inquiries
1. Open Google Sheets and create a new spreadsheet titled **"Customer Inquiries"**.
2. Create columns for:
   - **Timestamp**
   - **Name**
   - **Email**
   - **Inquiry**
   - **Urgency** (e.g., mark as "urgent" if needed)
3. In the MAKE.com scenario, click the **+ button** after the webhook module.
4. Add the **Google Sheets** module and select **"Add a Row"**.
5. Connect your Google Sheets account and choose the **"Customer Inquiries"** spreadsheet (usually “Sheet1”).
6. Map the incoming webhook data (e.g., **Name**, **Email**, **Inquiry**, **Urgency**) to the corresponding columns.
7. Save the module.

_Note: For the connection part, you might have to log in to your Google account._

Sample image
![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/1.2.png?raw=true)
---

### Step 3: Send an Auto-Response Email via Email by Make
1. Click **+** after the Google Sheets module.
2. Search for the **Email** module provided by Make (commonly listed as **"Send an Email"** under Email by Make).
3. This module is built in, so no external connection or API keys are required.
4. In the **To** field, map the email address from the webhook data.
5. Set the **Subject** to "We’ve received your inquiry!".
6. In the **Body**, enter your auto-response message. For example:
   ```html
   Hi {{Name}},
   
   Thank you for contacting us. We have received your inquiry: "{{Inquiry}}"
   
   We will get back to you shortly.
   
   Best regards,
   Your Company Name

7. Save the configuration.

Note: You will have to log in to your Microsoft account in order for this component to work. Choose the Microsoft SMTP option from the dropdown.

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/1.3.png?raw=true)
------------


### Step 4: Add a Filter for Urgent Inquiries
1. Click on the connection line after the Email module to add a **Filter**.
2. Set a filter condition to check if the inquiry is urgent. For example:
   - Check if the **Urgency** field equals "urgent", or
   - Check if the **Inquiry** text contains the word "urgent"
3. Only inquiries that meet this condition will proceed to the next module.

---

### Step 5: Create a Follow-Up Event in Google Calendar
1. After the filter, click **+** to add a new module.
2. Search for **Google Calendar** and select **"Create an Event"**.
3. Connect your Google Calendar account.
4. Choose the calendar where you want to create the event (or create a new one titled **"Follow-ups"**).
5. Configure the event details:
   - **Connection:** Select your connected Google Calendar account.
   - **Calendar ID:** Enter your calendar’s ID (for your primary calendar, this is usually your email address).
   - **Event Name:** Enter a dynamic title, for example: "Follow-up: Inquiry from {{Name}}"
6. Save the module.

Sample Image:
![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/1.4.png?raw=true)
---

### Finalizing and Testing
1. **Run the Scenario:**  
   Click **Run Once** in MAKE.com and send a test inquiry using the webhook URL.
2. **Verify the Following:**
   - The inquiry is logged in the **Google Sheet**.
   - An auto-response email is sent via the **Email by Make** module.
   - If the inquiry is marked as urgent, a follow-up event is created in Google Calendar.
3. Activate the scenario by toggling it **ON** and set the desired scheduling frequency.

Final flow:
![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/8.png?raw=true)

---

### Notes
- **Google Sheets Connection:** You may need to log in to your Google account to authorize access.
- **Email Module:** Ensure you log in with your Microsoft account if using the Microsoft SMTP option.
- **Testing:** Use test data to verify that each component works as expected before activating the scenario.

---

*End of Documentation*
