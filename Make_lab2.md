# 2. Automated Customer Inquiry Response & Follow-Up

### Overview
This workflow processes customer inquiries in real time using five components:
1. A custom webhook to receive inquiry data.
2. Logging inquiries in a Google Sheet.
3. Sending an auto-response email via the built-in Email module (Email by Make).
4. Filtering inquiries for urgency.
5. Creating a follow-up event in Google Calendar for urgent inquiries.

### Steps

#### Step 1: Create a Custom Webhook Trigger
1. Log in to [MAKE.com](https://www.make.com) and create a new scenario.
2. Click the **+ button** and search for the **Webhooks** module.
3. Select **Custom webhook** as the trigger.
4. Click **Add** to create a new webhook (e.g., **"Customer Inquiry Webhook"**). A unique webhook URL will be generated.
5. Use this URL to send inquiry data (for testing, you can use tools like Postman or MAKE.com’s testing feature).

#### Step 2: Set Up a Google Sheet to Log Inquiries
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

Note: For the connection part you might have to login into your google account.

#### Step 3: Send an Auto-Response Email via Email by Make
1. Click **+** after the Google Sheets module.
2. Search for the **Email** module provided by Make (commonly listed as **"Send an Email"** under Email by Make).
3. This module is built in, so no external connection or API keys are required.
4. In the **To** field, map the email address from the webhook data.
5. Set the **Subject** to "We’ve received your inquiry!".
6. In the **Body**, enter your auto-response message. For example:

Note: You will have to login into your microsoft account in order for this component to work. ( Choose Microsoft STMP option from the dropdown)

```html
Hi {{Name}},

Thank you for contacting us. We have received your inquiry: "{{Inquiry}}"

We will get back to you shortly.

Best regards, Your Company Name
```

7. Save the configuration.

#### Step 4: Add a Filter for Urgent Inquiries
1. Click on the connection line after the Email module to add a **Filter**.
2. Set a filter condition to check if the inquiry is urgent. For example:
- Check if the **Urgency** field equals "urgent"
- Or check if the **Inquiry** text contains the word "urgent"
3. Only inquiries that meet this condition will proceed to the next module.

#### Step 5: Create a Follow-Up Event in Google Calendar
1. After the filter, click **+** to add a new module.
2. Search for **Google Calendar** and select **"Create an Event"**.
3. Connect your Google Calendar account.
4. Choose the calendar where you want to create the event (or create a new one titled **"Follow-ups"**).
5. Configure the event details:
- **Connection:** Select your connected account.
- **Create an Event:** (This should be preset in the module.)
- **Calendar ID:** Enter your calendar’s ID (for your primary calendar, this is usually your email address).
- **Event Name:** Enter a dynamic title, for example: "Follow-up: Inquiry from {{Name}}"
6. Save the module.

### Finalizing and Testing
1. **Run the Scenario:** Click **Run Once** and send a test inquiry using the webhook URL.
2. Verify the following:
- The inquiry is logged in the **Google Sheet**.
- An auto-response email is sent via the **Email by Make** module.
- If the inquiry is marked as urgent, a follow-up event is created in Google Calendar.
3. Activate the scenario by toggling it **ON** and set the desired scheduling frequency.
