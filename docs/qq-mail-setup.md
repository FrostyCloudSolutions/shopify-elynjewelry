# docs/qq-mail-setup.md

# Professional Email Setup — QQ Mail
# info@[your-domain].com

**Prepared by:** Frosty Solutions  
**Website:** frostycloud.net  
**Date:** March 2026  
**Service:** QQ Mail with Custom Domain  
**Cost:** Free (personal account with domain email feature)  

---

## Overview

QQ Mail allows you to send and receive email using your custom domain 
address (e.g. info@yourdomain.com) linked to your existing QQ account. 
This service works in mainland China without a VPN.

**Requirements:**
- Existing QQ account
- Access to your domain registrar (DNS settings)
- Alibaba Cloud account login

---

## Step 1 — Log into QQ Mail

1. Go to **mail.qq.com**
2. Log in with your existing QQ account credentials

---

## Step 2 — Go to Domain Email Settings

1. Click **Settings (设置)** in the top right corner
2. Click **Domain Email (域名邮箱)**
3. Click **Apply for Domain Email (申请域名邮箱)**
4. Enter your domain name and submit

---

## Step 3 — Get DNS Records from QQ Mail

QQ Mail will provide two DNS records:
- A **CNAME record** for domain verification
- An **MX record** for email routing

Copy both records exactly as shown.

---

## Step 4 — Add DNS Records in Alibaba Cloud

1. Log into your Alibaba Cloud account at **account.aliyun.com**
2. Go to **Domain** → **DNS Settings** for your domain
3. Click **Add Record** and add the CNAME record:
   - **Type:** CNAME
   - **Host:** as provided by QQ Mail
   - **Value:** as provided by QQ Mail
4. Click **Add Record** again and add the MX record:
   - **Type:** MX
   - **Host:** @ (or blank)
   - **Value:** as provided by QQ Mail
   - **Priority:** 10
5. Save both records

---

## Step 5 — Verify Domain in QQ Mail

1. Go back to QQ Mail domain email settings
2. Click **Verify (验证)**
3. QQ Mail will automatically check your DNS records
4. Verification can take up to 24-48 hours

---

## Step 6 — Create Email Address

1. Once verified, go to **Domain Email Management**
2. Click **Add Email Account**
3. Create: info@yourdomain.com
4. Set a password
5. Save

---

## Step 7 — Set Up on iPhone

1. Open **Settings** on iPhone
2. Go to **Mail → Accounts → Add Account**
3. Select **Other → Add Mail Account**
4. Enter:
   - Name: Your Name or Store Name
   - Email: info@yourdomain.com
   - Password: your QQ domain email password
5. For incoming mail server:
   - Host: imap.qq.com
   - Username: info@yourdomain.com
   - Password: your password
6. For outgoing mail server:
   - Host: smtp.qq.com
   - Username: info@yourdomain.com
   - Password: your password
7. Save

Alternatively download the **QQ Mail app (QQ邮箱)** from the 
App Store and log in directly.

---

## Step 8 — Sending as info@yourdomain.com

When composing a new email in QQ Mail:
1. Click the **From** field
2. Select **info@yourdomain.com** from the dropdown
3. Your email will be sent from your custom domain address

---

## Important Notes

- QQ Mail domain email is free for personal accounts
- Works in mainland China without VPN
- Integrates with existing QQ and WeChat ecosystem
- If QQ charges for domain email in future, consider Zoho Mail 
  as an alternative (see Zoho Mail Setup document)

---

## DNS Propagation

DNS changes can take up to 24-48 hours to fully propagate.
During this time email may not work consistently. This is normal.

---

## Troubleshooting

**Verification failed:**
- Wait 24-48 hours and try again
- Confirm DNS records are saved correctly in Alibaba Cloud
- Check CNAME and MX records match exactly what QQ Mail provided

**Emails not arriving:**
- Check MX record is correct
- Wait for DNS propagation
- Check QQ Mail spam folder

**Cannot send as custom domain:**
- Verify domain email account was created successfully
- Check From field dropdown shows custom domain option
- Ensure domain verification completed successfully

---

*Document prepared by Frosty Solutions — frostycloud.net — March 2026*
