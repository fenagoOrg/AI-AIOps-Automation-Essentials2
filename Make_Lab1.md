# Automated Lead Capture and Follow-up Workflow

This project automates the process of collecting leads using a Google Form, storing them in a Google Sheet, sending a confirmation email via the built-in Email module, and notifying your team via Slack.

---

## Table of Contents
1. [Overview](#overview)
2. [Workflow Steps](#workflow-steps)
   - [Step 1: Set Up a Google Form for Lead Collection](#step-1-set-up-a-google-form-for-lead-collection)
   - [Step 2: Create a Scenario in MAKE.com](#step-2-create-a-scenario-in-makecom)
   - [Step 3: Configure Google Sheets Module (Trigger)](#step-3-configure-google-sheets-module-trigger)
   - [Step 4: Configure Email by Make Module (Send "Reaching Out" Email)](#step-4-configure-email-by-make-module-send-reaching-out-email)
   - [Step 5: Add Slack Module for Team Notification](#step-5-add-slack-module-for-team-notification)
   - [Step 6: Test and Activate the Flow](#step-6-test-and-activate-the-flow)
3. [Final Flow Components](#final-flow-components)

---

## Overview
This workflow collects lead data submitted via a Google Form, logs the information into a Google Sheet, sends a personalized confirmation email to the lead using the Email by Make module, and posts a notification to a Slack channel to alert your team about the new lead.

---

## Workflow Steps

### Step 1: Set Up a Google Form for Lead Collection
1. **Access Google Forms:**  
   Go to [Google Forms](https://forms.google.com).

2. **Create a New Form:**  
   Click **Blank Form** and name it **"Lead Capture Form."**

3. **Add Fields:**  
   - **Name** (Short answer)  
   - **Email** (Short answer)  
   - **Phone Number** (Short answer)  
   - **Company Name** (Short answer)

4. **Link to Google Sheets:**  
   Click the **Responses** tab, then click the Google Sheets icon to link the form to a new sheet.  
   - Name the sheet **"Lead Data"** and save.


---

### Step 2: Create a Scenario in MAKE.com
1. **Log in to MAKE.com:**  
   Open [MAKE.com](https://www.make.com) and sign in.

2. **Create a New Scenario:**  
   Click **Create a new scenario**.

3. **Add the First Module:**  
   Click the **+ button** to add a module.

---

### Step 3: Configure Google Sheets Module (Trigger)
1. **Search and Select Module:**  
   Search for **Google Sheets** and select **"Watch New Rows"** (Trigger).

2. **Authorize Connection:**  
   Click **Add connection** and authorize access to your Google Sheets account.

3. **Select Your Spreadsheet:**  
   Choose the **"Lead Data"** spreadsheet and select the appropriate worksheet (typically **Sheet1**).

4. **Set the Trigger Event:**  
   Choose **"Row Added"** as the trigger event.

5. **Save the Module.**

Sample image:
![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/11.png?raw=true)

---

### Step 4: Configure Email by Make Module (Send "Reaching Out" Email)
1. **Add the Email Module:**  
   Click **+** after the Google Sheets module.

2. **Search and Select Email Module:**  
   Search for the **Email** module provided by Make (commonly labeled **"Send an Email"** under Email by Make).  
   This built-in module avoids the configuration complications sometimes encountered with external email services.

3. **Configure the Email:**
   - **To:**  
     Use the variable selector to choose the **Email** field from the Google Sheets data.
   - **Subject:**  
     Enter:  
     `Thank you for contacting us!`
   - **Body:**  
     Enter your message (plain text or HTML). For example:
     ```
     Hi {{Name}},
     
     Thank you for reaching out! Our team will get back to you soon.
     
     Regards,
     [Your Business Name]
     ```
4. **Save the Configuration.**

Sample Image:

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/12.png?raw=true)


### Step 5: Add Slack Module for Team Notification
1. **Add the Slack Module:**  
   Click **+** after the Email module.

2. **Search and Select Slack Module:**  
   Search for **Slack** and select **"Send a Message."**

3. **Configure Slack Settings:**

   - **Connection\***:  
     Click the **Connection\*** field, then select or add your Slack connection by following the prompts to authorize access to your Slack workspace.

   - **Enter a channel ID or name\***:  
     Enter the channel name (e.g., `#leads-notification`) or the channel ID where you want the message to be posted.

   - **Channel type\***:  
     Select **Public channel** if you're using a public channel. (For private channels, additional settings may be required.)

   - **Map Text:**  
     Enter the primary message content as plain text (acts as a fallback if using Blocks). For example:
     ```
     🚀 New Lead Alert!
     Name: {{Name}}
     Email: {{Email}}
     Company: {{Company Name}}
     ```
     
   - **Blocks (Optional):**  
     If you want to use Slack’s Block Kit for a rich formatted message, configure Blocks here. Otherwise, leave this section empty.

4. **Save the Slack Module Configuration.**

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/13.png?raw=true)

---

### Step 6: Test and Activate the Flow
1. **Test the Flow:**  
   Click **Run Once** in MAKE.com and submit a test entry via your Google Form.

2. **Verify Each Component:**
   - The new lead data is added to the **Google Sheet** ("Lead Data").
   - A confirmation email is sent to the lead via the **Email by Make** module.
   - A notification message is posted in your designated **Slack** channel.

3. **Activate the Scenario:**  
   Once testing is successful, click **Turn on Scheduling** to automate the flow.

---

## Final Flow Components
1. **Google Form:** Collects lead data.
2. **Google Sheets:** Stores lead information.
3. **MAKE.com - Google Sheets Trigger:** Detects new leads by watching for new rows.
4. **MAKE.com - Email Module:** Sends a personalized confirmation email.
5. **MAKE.com - Slack Module:** Notifies your team about new leads.

Final flow :

![](https://github.com/Neha-Chiluka/langflow-labs/blob/main/images/7.png?raw=true)
---

*End of Documentation*
