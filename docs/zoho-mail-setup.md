# docs/zoho-mail-setup.md

# Professional Email Setup — Zoho Mail
# info@[your-domain].com

**Prepared by:** Frosty Solutions  
**Website:** frostycloud.net  
**Date:** March 2026  
**Service:** Zoho Mail (Free Plan)  
**Cost:** Free for 1 user  

---

## Overview

Zoho Mail allows you to send and receive email using your custom 
domain address (e.g. info@yourdomain.com). This guide walks through 
the complete setup process.

**Requirements:**
- Access to your domain registrar (DNS settings)
- A Zoho account (free to create)
- VPN if accessing from mainland China

---

## Step 1 — Create Zoho Mail Account

1. Go to **zoho.com/mail**
2. Click **Sign Up Free**
3. Select **Forever Free Plan** (1 user, 5GB)
4. Enter your details and create your account

---

## Step 2 — Add Your Domain

1. After signing up, Zoho will ask you to add a domain
2. Enter your domain name (e.g. yourdomain.com)
3. Click **Add Domain**
4. Zoho will show you a TXT verification record — copy it

---

## Step 3 — Verify Domain in Alibaba Cloud

1. Log into your Alibaba Cloud account at **account.aliyun.com**
2. Go to **Domain** → **DNS Settings** for your domain
3. Click **Add Record**
4. Add the TXT record provided by Zoho:
   - **Type:** TXT
   - **Host:** @ (or leave blank)
   - **Value:** paste the Zoho verification code
5. Save the record
6. Go back to Zoho and click **Verify**
7. Wait up to 30 minutes for verification to complete

---

## Step 4 — Add MX Records

After domain verification, Zoho will provide MX records.
Add these in Alibaba Cloud DNS settings:

| Type | Host | Value | Priority |
|---|---|---|---|
| MX | @ | mx.zoho.com | 10 |
| MX | @ | mx2.zoho.com | 20 |
| MX | @ | mx3.zoho.com | 50 |

---

## Step 5 — Add SPF and DKIM Records

These records improve email deliverability and prevent spam flags.
Zoho will provide these — add them in Alibaba Cloud DNS:

**SPF Record:**
- Type: TXT
- Host: @
- Value: v=spf1 include:zoho.com ~all

**DKIM Record:**
- Type: TXT
- Host: zoho._domainkey
- Value: provided by Zoho during setup

---

## Step 6 — Create Email Address

1. In Zoho Mail admin, go to **Mail Accounts**
2. Click **Add Account**
3. Create: info@yourdomain.com
4. Set a password
5. Save

---

## Step 7 — Set Up on iPhone

1. Open **Settings** on iPhone
2. Go to **Mail → Accounts → Add Account**
3. Select **Other**
4. Select **Add Mail Account**
5. Enter:
   - Name: Your Name or Store Name
   - Email: info@yourdomain.com
   - Password: your Zoho password
   - Description: Store Email
6. For incoming mail server:
   - Host: imap.zoho.com
   - Username: info@yourdomain.com
   - Password: your Zoho password
7. For outgoing mail server:
   - Host: smtp.zoho.com
   - Username: info@yourdomain.com
   - Password: your Zoho password
8. Save

Alternatively download the **Zoho Mail app** from the App Store 
and log in directly.

---

## Step 8 — Set Up on Computer

1. Go to **mail.zoho.com**
2. Log in with your Zoho credentials
3. All emails sent to info@yourdomain.com will appear here
4. You can send emails as info@yourdomain.com directly

---

## DNS Propagation

DNS changes can take up to 24-48 hours to fully propagate globally.
During this time email may not work consistently. This is normal.

---

## Troubleshooting

**Emails not arriving:**
- Check DNS records are saved correctly in Alibaba Cloud
- Wait 24-48 hours for propagation
- Check Zoho spam folder

**Cannot send emails:**
- Verify SMTP settings are correct
- Check Zoho account is active
- Ensure VPN is connected if accessing from mainland China

**Domain verification failed:**
- Wait 30 minutes and try again
- Confirm TXT record was saved correctly in Alibaba Cloud
- Contact Zoho support if issue persists

---

*Document prepared by Frosty Solutions — frostycloud.net — March 2026*
