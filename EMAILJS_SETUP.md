# EmailJS Setup Guide for Contact Form

## Step 1: Create EmailJS Account
1. Go to [https://www.emailjs.com](https://www.emailjs.com)
2. Click "Sign Up" and create a free account
3. Verify your email address

## Step 2: Add Email Service (Gmail)
1. In EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Select **Gmail**
4. Click **Connect Account** and authorize your Gmail
5. Copy the **Service ID** (e.g., `service_abc123`)

## Step 3: Create Email Template
1. Go to **Email Templates**
2. Click **Create New Template**
3. Use this template content:

**Template Name:** Contact Form Submission

**Subject:** New Contact Form Submission from {{from_name}}

**Content:**
```
You have received a new message from your website contact form:

Name: {{from_name}}
Email: {{from_email}}
Phone: {{phone}}
Company: {{company}}

Message:
{{message}}

---
This email was sent from your Saphinox website contact form.
```

4. Click **Save** and copy the **Template ID** (e.g., `template_xyz789`)

## Step 4: Get Your Public Key
1. Go to **Account** → **General**
2. Copy your **Public Key** (e.g., `abcDEF123xyz`)

## Step 5: Update contact.html
Open `contact.html` and replace these three values at the bottom of the file:

```javascript
emailjs.init({
  publicKey: "YOUR_PUBLIC_KEY",  // Replace with your Public Key
});

emailjs.sendForm('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', this)
//                ^^^^^^^^^^^^^^^^   ^^^^^^^^^^^^^^^^^^
//                Replace these two values
```

## Example:
```javascript
emailjs.init({
  publicKey: "abcDEF123xyz",
});

emailjs.sendForm('service_abc123', 'template_xyz789', this)
```

## Step 6: Test Your Form
1. Open `contact.html` in your browser
2. Fill out the form and submit
3. Check your Gmail inbox for the notification

## Troubleshooting
- **Not receiving emails?** Check your EmailJS dashboard for failed sends
- **CORS errors?** Make sure you're testing on a web server, not file://
- **Free tier limit:** 200 emails/month

## Need Help?
- EmailJS Documentation: https://www.emailjs.com/docs/
- Support: https://www.emailjs.com/support/
