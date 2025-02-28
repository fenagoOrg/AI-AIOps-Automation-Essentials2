# Use Case: Automated Lead Capture and Follow-up.
This project will automate the process of collecting leads from a Google Form, storing them in a Google Sheet, and sending a welcome email via Gmail to each new lead.


### Step 1: 
#### Set Up a Google Form for Lead Collection
1. Go to Google Forms.
2. Click Blank Form and name it "Lead Capture Form."
3. Add the following fields:
- 	Name (Short answer)
- 	Email (Short answer)
- 	Phone Number (Short answer)
- 	Company Name (Short answer)
4. Click the Responses tab and link it to a Google Sheet by clicking the Google Sheets icon.
5. Name the sheet "Lead Data" and save.

### Step 2:
#### Create a Scenario in MAKE.com

1. Log in to MAKE.com.
2. Click Create a new scenario.
3. Click the + button to add a module.

### Step 3: 
#### Google Sheets Module (Trigger)

1. Search for Google Sheets and select "Watch New Rows" (Trigger).
2. Click Add connection and authorize access to your Google Sheets.
3. Select the spreadsheet "Lead Data" and choose the worksheet 
(e.g., "Sheet1").
4. Choose "Row Added" as the trigger event.
5. Click OK to save.

### Step 4: 
#### Gmail Module (Send "Reaching Out" Email)

1. Click + after the Google Sheets module.
2. Search for Gmail and select "Send an Email."
3. Click Add connection and authenticate your Gmail account.
4. In the To field, click the variable selector and choose Email from Google Sheets.
5. Enter a Subject: "Thank you for contacting us!"

```html
	Hi {{Name}},  
	Thank you for reaching out! Our team will get back to you soon.  
	Regards,  
	[Your Business Name]
```

### Step 5: 
#### Add Slack Module (Notification)
1. Click + → Search Slack → Select Send a Message.
2. Connect your Slack workspace.
3. Choose the channel (e.g., #leads-notification).
Message Content

```html
🚀 New Lead Alert!  
Name: {{Name}}  
Email: {{Email}}  
Message: {{Message}}  
```
4.Click OK.


### Step 6: 
#### Test and Activate the Flow**
1. Click Run Once to test with a form submission.
2. If everything works fine, click Turn on Scheduling to automate.
3. ✅ Final Flow Components:

5. Google Form (Lead collection)
6. Google Sheets (Store data)
7. MAKE.com - Google Sheets Trigger (Detect new leads)
8. MAKE.com - Gmail Module (Send confirmation email)
9. MAKE.com - Slack Module (Notify team)
