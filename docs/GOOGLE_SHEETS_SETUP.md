# Google Sheets Integration Guide
## Form Data Collection Setup

---

## Overview

This guide explains how to set up Google Sheets integration to automatically capture form submissions from the Business Buddy website. When users submit the lead capture form, their data will be automatically saved to a Google Sheets spreadsheet.

## Why Google Sheets?

**Advantages:**
- ✅ Free and accessible
- ✅ Real-time data collection
- ✅ Easy to share with team members
- ✅ No backend server required
- ✅ Built-in data analysis tools
- ✅ Can trigger email notifications
- ✅ Export to other tools (CRM, email marketing)

**Limitations:**
- ⚠️ Requires manual setup
- ⚠️ Not suitable for extremely high traffic
- ⚠️ Limited to 1,000 requests per day (can be increased)
- ⚠️ No built-in spam protection (need to add)
- ⚠️ Web App URL visible in client-side code (public endpoint)

---

## Prerequisites

- Google Account
- Basic understanding of Google Sheets
- Access to Google Apps Script
- Website hosted and accessible

---

## Step-by-Step Setup

### Step 1: Create a Google Sheets Spreadsheet

1. Go to [Google Sheets](https://sheets.google.com)
2. Click "Blank" to create a new spreadsheet
3. Name it "Business Buddy - Lead Form Submissions"
4. Create headers in the first row:

| A | B | C | D | E |
|---|---|---|---|---|
| Timestamp | Name | Email | Company | Status |

**Header Descriptions:**
- **Timestamp**: Automatic date/time of submission
- **Name**: User's full name
- **Email**: User's email address
- **Company**: Company name (optional field)
- **Status**: For lead qualification (New, Contacted, Qualified, etc.)

### Step 2: Create Google Apps Script

1. In your Google Sheet, go to **Extensions > Apps Script**
2. Delete any existing code
3. Paste the following script:

```javascript
/**
 * Business Buddy Lead Form Handler
 * Receives form submissions and saves to Google Sheets
 */

// Configuration
const SHEET_NAME = 'Sheet1'; // Change if your sheet has a different name
const NOTIFICATION_EMAIL = 'hello@bizbud.co.th'; // Change to your email

/**
 * Handles POST requests from the website form
 */
function doPost(e) {
  try {
    // Get the active spreadsheet
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(SHEET_NAME);
    
    // Parse the incoming data
    const data = JSON.parse(e.postData.contents);
    
    // Extract form fields
    const timestamp = new Date();
    const name = data.name || '';
    const email = data.email || '';
    const company = data.company || '';
    const status = 'New';
    
    // Validate required fields
    if (!name || !email) {
      return ContentService.createTextOutput(JSON.stringify({
        'status': 'error',
        'message': 'Name and email are required'
      })).setMimeType(ContentService.MimeType.JSON);
    }
    
    // Validate email format
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
      return ContentService.createTextOutput(JSON.stringify({
        'status': 'error',
        'message': 'Invalid email format'
      })).setMimeType(ContentService.MimeType.JSON);
    }
    
    // Append the data to the sheet
    sheet.appendRow([
      timestamp,
      name,
      email,
      company,
      status
    ]);
    
    // Send email notification (optional)
    sendNotificationEmail(name, email, company);
    
    // Return success response
    return ContentService.createTextOutput(JSON.stringify({
      'status': 'success',
      'message': 'Form submitted successfully'
    })).setMimeType(ContentService.MimeType.JSON);
    
  } catch (error) {
    // Log error
    Logger.log('Error: ' + error.toString());
    
    // Return error response
    return ContentService.createTextOutput(JSON.stringify({
      'status': 'error',
      'message': error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}

/**
 * Handles GET requests (for testing)
 */
function doGet(e) {
  return ContentService.createTextOutput(JSON.stringify({
    'status': 'success',
    'message': 'Business Buddy Lead Form API is running'
  })).setMimeType(ContentService.MimeType.JSON);
}

/**
 * Sends email notification when a new lead is submitted
 */
function sendNotificationEmail(name, email, company) {
  try {
    const subject = '🎯 New Lead: ' + name;
    const body = `
New lead form submission from Business Buddy website:

Name: ${name}
Email: ${email}
Company: ${company || 'Not provided'}
Timestamp: ${new Date().toLocaleString('th-TH')}

View all leads: ${SpreadsheetApp.getActiveSpreadsheet().getUrl()}

---
This is an automated notification from Business Buddy Lead Form System.
    `;
    
    MailApp.sendEmail(NOTIFICATION_EMAIL, subject, body);
  } catch (error) {
    Logger.log('Email notification error: ' + error.toString());
    // Don't fail the submission if email fails
  }
}

/**
 * Test function to verify setup
 */
function testFormSubmission() {
  const testData = {
    postData: {
      contents: JSON.stringify({
        name: 'Test User',
        email: 'test@example.com',
        company: 'Test Company'
      })
    }
  };
  
  const result = doPost(testData);
  Logger.log(result.getContent());
}
```

4. **Update Configuration**:
   - Change `SHEET_NAME` if your sheet has a different name
   - Change `NOTIFICATION_EMAIL` to your actual email address

5. Save the project:
   - Click the disk icon or `Ctrl+S` (Windows) / `Cmd+S` (Mac)
   - Name it "BizBud Lead Form Handler"

### Step 3: Deploy as Web App

1. Click **Deploy > New deployment**
2. Click the gear icon next to "Select type"
3. Choose **Web app**
4. Configure the deployment:
   - **Description**: "Business Buddy Lead Form v1"
   - **Execute as**: Me (your@email.com)
   - **Who has access**: Anyone
5. Click **Deploy**
6. **Important**: Copy the **Web App URL** (looks like: `https://script.google.com/macros/s/ABC123.../exec`)
7. Click **Done**

### Step 4: Authorize the Script

1. After deploying, you'll see an authorization prompt
2. Click **Authorize access**
3. Choose your Google account
4. Click **Advanced**
5. Click **Go to BizBud Lead Form Handler (unsafe)**
6. Review permissions and click **Allow**

### Step 5: Test the Web App

#### Option A: Test in Browser
1. Copy your Web App URL
2. Paste it in a new browser tab
3. You should see: `{"status":"success","message":"Business Buddy Lead Form API is running"}`

#### Option B: Test with Apps Script
1. In Apps Script editor, select function `testFormSubmission` from dropdown
2. Click **Run**
3. Check your Google Sheet - a test row should appear
4. Check your email for notification

### Step 6: Update Website Code

1. Open your `index.html` file
2. Find this line in the JavaScript:
   ```javascript
   const GOOGLE_SHEETS_URL = 'YOUR_GOOGLE_SHEETS_WEB_APP_URL_HERE';
   ```
3. Replace with your actual Web App URL:
   ```javascript
   const GOOGLE_SHEETS_URL = 'https://script.google.com/macros/s/ABC123.../exec';
   ```
4. Save and deploy your website

### Step 7: Test End-to-End

1. Visit your live website
2. Scroll to the contact form
3. Fill out the form with test data
4. Submit the form
5. Check your Google Sheet - the data should appear
6. Check your email for notification

---

## Advanced Configuration

### Adding Spam Protection

Add this function to detect and prevent spam:

```javascript
function isSpam(name, email, company) {
  // Check for suspicious patterns
  const spamKeywords = ['viagra', 'casino', 'forex', 'lottery', 'winner'];
  const text = (name + email + company).toLowerCase();
  
  for (let keyword of spamKeywords) {
    if (text.includes(keyword)) {
      return true;
    }
  }
  
  // Check for too many numbers in name
  const numberCount = (name.match(/\d/g) || []).length;
  if (numberCount > 3) {
    return true;
  }
  
  // Check for suspicious email domains
  const suspiciousDomains = ['tempmail.com', 'throwaway.email'];
  const domain = email.split('@')[1];
  if (suspiciousDomains.includes(domain)) {
    return true;
  }
  
  return false;
}
```

Then add this check in your `doPost` function:

```javascript
// Check for spam
if (isSpam(name, email, company)) {
  return ContentService.createTextOutput(JSON.stringify({
    'status': 'error',
    'message': 'Submission rejected'
  })).setMimeType(ContentService.MimeType.JSON);
}
```

### Rate Limiting

Add this to prevent abuse:

```javascript
const RATE_LIMIT_PER_EMAIL = 3; // Max submissions per email per day

function checkRateLimit(email) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(SHEET_NAME);
  const data = sheet.getDataRange().getValues();
  
  const today = new Date();
  today.setHours(0, 0, 0, 0);
  
  let count = 0;
  for (let i = 1; i < data.length; i++) {
    const rowDate = new Date(data[i][0]);
    const rowEmail = data[i][2];
    
    if (rowEmail === email && rowDate >= today) {
      count++;
    }
  }
  
  return count < RATE_LIMIT_PER_EMAIL;
}
```

### Adding UTM Parameters

Track where leads come from:

```javascript
// In doPost function, add:
const utm_source = data.utm_source || '';
const utm_medium = data.utm_medium || '';
const utm_campaign = data.utm_campaign || '';

// Append to row:
sheet.appendRow([
  timestamp,
  name,
  email,
  company,
  status,
  utm_source,
  utm_medium,
  utm_campaign
]);
```

Update website to send UTM parameters:

```javascript
// Get URL parameters
const urlParams = new URLSearchParams(window.location.search);

// Add to form data
body: JSON.stringify({
  name: name,
  email: email,
  company: company,
  timestamp: new Date().toISOString(),
  utm_source: urlParams.get('utm_source'),
  utm_medium: urlParams.get('utm_medium'),
  utm_campaign: urlParams.get('utm_campaign')
})
```

---

## Troubleshooting

### Issue 1: "Authorization required" error

**Solution:**
1. Re-deploy the script
2. Make sure "Execute as: Me" is selected
3. Re-authorize the script
4. Clear browser cache

### Issue 2: Data not appearing in sheet

**Solution:**
1. Check the Web App URL is correct
2. Test the Web App directly in browser
3. Check browser console for errors
4. Verify sheet name matches `SHEET_NAME` in script

### Issue 3: CORS errors

**Solution:**
- This is expected with 'no-cors' mode
- Form will still work, but you won't see response details
- Error handling is built into the code

### Issue 4: No email notifications

**Solution:**
1. Check email address is correct
2. Check spam folder
3. Verify MailApp permissions
4. Test with `testFormSubmission()` function

### Issue 5: "Too many requests" error

**Solution:**
1. Implement rate limiting (see Advanced Configuration)
2. Consider upgrading to Google Workspace for higher limits
3. Add CAPTCHA to form (reCAPTCHA v3)

---

## Data Management

### Exporting Data

**To CSV:**
1. File > Download > Comma-separated values (.csv)

**To Excel:**
1. File > Download > Microsoft Excel (.xlsx)

**To Google Data Studio:**
1. Data > Connect to Data Studio
2. Create visualization dashboard

### Backing Up Data

**Option 1: Automatic Backup Script**
```javascript
function backupSheet() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName(SHEET_NAME);
  const backupSheet = sheet.copyTo(ss);
  backupSheet.setName('Backup_' + new Date().toLocaleDateString());
}

// Set trigger: Edit > Current project's triggers > Add Trigger
// Run: backupSheet
// Event: Time-driven, Week timer, Every Monday
```

**Option 2: Google Drive Backup**
1. Make a copy of the entire spreadsheet weekly
2. Use Google Takeout for comprehensive backup

### Data Analysis

**Basic Metrics:**
```
=COUNTA(B2:B) // Total submissions
=COUNTIF(E2:E,"New") // New leads
=COUNTIF(E2:E,"Contacted") // Contacted leads
```

**Time-based Analysis:**
```
=COUNTIFS(A2:A,">"&TODAY()-7,A2:A,"<"&TODAY()) // Leads this week
=COUNTIFS(A2:A,">"&EOMONTH(TODAY(),-1),A2:A,"<"&EOMONTH(TODAY(),0)) // Leads this month
```

---

## Security Best Practices

### 1. Understand URL Visibility
- **Important**: The Web App URL will be visible in client-side code
- This is expected and acceptable for public form submissions
- Anyone can view it in browser developer tools
- The URL itself is a public endpoint (this is by design)
- Focus on securing the Apps Script logic instead:
  - Validate all inputs
  - Implement rate limiting
  - Add spam protection
  - Don't trust client-side data

### 2. Protect Your Google Sheet
- Share sheet only with necessary team members
- Use "Editor" access for team
- Use "Viewer" access for stakeholders
- Don't make the sheet publicly editable

### 2. Limit Sheet Access
- Share sheet only with necessary team members
- Use "Editor" access for team
- Use "Viewer" access for stakeholders

### 3. Monitor for Abuse
- Set up alerts for unusual activity
- Review submissions regularly
- Implement rate limiting

### 4. Data Privacy Compliance
- Add privacy policy to website
- Inform users how data is used
- Provide opt-out mechanism
- Delete data upon request (GDPR compliance)

---

## Alternatives to Google Sheets

If Google Sheets doesn't meet your needs, consider:

### 1. Formspree
- **Pros**: Easy setup, handles backend
- **Cons**: Paid plans for more features
- **URL**: https://formspree.io

### 2. Netlify Forms
- **Pros**: Built-in if hosting on Netlify
- **Cons**: Limited free tier
- **URL**: https://www.netlify.com/products/forms/

### 3. Google Forms
- **Pros**: Very easy, no coding
- **Cons**: Less flexible, different UI
- **URL**: https://www.google.com/forms

### 4. Airtable
- **Pros**: More powerful than Sheets, better UI
- **Cons**: Requires API key, more complex
- **URL**: https://airtable.com

### 5. Custom Backend
- **Pros**: Full control, scalable
- **Cons**: Requires server, more complex
- **Options**: Node.js, Python, PHP

---

## Integration with Other Tools

### Zapier Integration
1. Create Zap: Google Sheets → Gmail/Slack/CRM
2. Trigger: New row in Google Sheets
3. Action: Send email, Slack message, create CRM contact

### Make (formerly Integromat)
1. Create scenario: Google Sheets → Other apps
2. More complex workflows possible
3. Visual workflow builder

### Google Data Studio
1. Connect Google Sheets as data source
2. Create dashboard with charts
3. Share with team for real-time insights

---

## Monitoring & Maintenance

### Daily Tasks
- [ ] Check for new submissions
- [ ] Respond to leads within 24 hours
- [ ] Update lead status in sheet

### Weekly Tasks
- [ ] Review submission patterns
- [ ] Check for spam/test submissions
- [ ] Export backup of data
- [ ] Analyze conversion metrics

### Monthly Tasks
- [ ] Review and optimize form fields
- [ ] Analyze traffic sources (UTM)
- [ ] Update email notification template
- [ ] Review API usage/limits

### Quarterly Tasks
- [ ] Complete security audit
- [ ] Review data retention policy
- [ ] Update privacy policy if needed
- [ ] Consider scaling to proper backend

---

## FAQ

**Q: Is Google Sheets integration free?**  
A: Yes, completely free for reasonable traffic levels.

**Q: What's the submission limit?**  
A: Default is 1,000 requests per day. This can be increased with Google Workspace.

**Q: Can I use this for multiple forms?**  
A: Yes, add different sheets or track form name in submissions.

**Q: Is the data secure?**  
A: Reasonably secure. Don't collect sensitive data (passwords, credit cards).

**Q: Can I customize email notifications?**  
A: Yes, edit the `sendNotificationEmail()` function in the script.

**Q: What if my Web App URL is exposed?**  
A: Deploy a new version to get a new URL. Consider adding authentication.

**Q: Can I integrate with my CRM?**  
A: Yes, use Zapier or Make to connect Google Sheets to your CRM.

**Q: How do I handle GDPR compliance?**  
A: Add privacy policy, get consent, provide data deletion on request.

---

## Support

If you encounter issues:
1. Check the Troubleshooting section above
2. Review Apps Script execution logs (View > Logs)
3. Test with `testFormSubmission()` function
4. Check Google Apps Script documentation
5. Contact your development team

---

**Last Updated**: November 2024  
**Version**: 1.0  
**Maintained by**: Business Buddy Development Team
