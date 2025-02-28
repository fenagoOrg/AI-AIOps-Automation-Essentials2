### Step 1: 
#### Set Up a Google Form for Lead Collection
1. Go to Google Forms.
2. Click Blank Form and name it "Lead Capture Form."
3. Add the following fields:
	Name (Short answer)
	Email (Short answer)
	Phone Number (Short answer)
	Company Name (Short answer)
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
#### Gmail Module (Send Welcome Email)

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
#### Test the Automation

1. Click Run Once in MAKE.com.
2. Fill out the Google Form with test data.
3. Check the Google Sheet for the new entry.
4. Verify that the email is sent to the provided email address.

### Step 6: 
#### Activate the Scenario

1. Click the Clock Icon (Scheduling) at the bottom.
2. Toggle the scenario to ON.
3. Set the frequency (e.g., Every 5 minutes).
4. Click Save.
