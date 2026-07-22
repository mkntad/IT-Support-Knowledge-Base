  # Outlook Configuration & Email Setup

##  Objective
Configure Outlook to connect to Microsoft 365 mailbox and resolve common sync issues.

---

##  Setup: New User Configuration

### **Step 1: Gather Information**
- User's email address (user@company.com)
- Office 365 password (should be set in Active Directory)
- Office 365 license status (verify in Admin Center)

### **Step 2: Open Outlook**

**If Outlook is not installed:**
1. Have user go to office.com
2. Sign in with their work email
3. Click the app launcher (grid icon)
4. Select "Office apps" or install from account.microsoft.com

**If Outlook is installed:**
1. Open Outlook
2. Click File → Add Account
3. Enter work email: user@company.com

### **Step 3: Automatic Configuration**

Outlook should auto-configure if:
- Office 365 tenant is properly configured
- User's email is in correct format
- Exchange Online is enabled

**If auto-config fails:**

1. Click "Advanced Options"
2. Enter these settings:
   - **Email:** user@company.com
   - **Server:** outlook.office365.com
   - **Port:** 993 (IMAP) or 465 (SMTP)
   - **Encryption:** TLS or SSL
   - **Username:** user@company.com
   - **Password:** [O365 password]

3. Click "Connect"

### **Step 4: Verify Connection**

- Send test email from Outlook
- Confirm receipt in Outlook Web Access (OWA)
- Check Calendar sync
- Verify Contacts appear

---

## Common Issues & Fixes

### **Issue: "Incorrect Username or Password"**

**Check:**
1. Is the email format correct? (should be full email, not just username)
2. Is password correct? (case-sensitive)
3. Is account licensed? (check in Microsoft 365 Admin Center)

**Resolution:**
- Confirm password in Active Directory matches Office 365
- Force password sync (may take 15 min)
- Reset password if needed
- Try removing and re-adding the account in Outlook

---

### **Issue: "Can't connect to the server"**

**Check:**
1. Is internet connection working?
2. Are Office 365 servers up? (check office status page)
3. Is firewall blocking port 993/465?

**Resolution:**
- Restart Outlook
- Check Windows Defender Firewall isn't blocking
- If on corporate network, verify VPN is connected
- Try Outlook Web Access (OWA) at outlook.office.com as a workaround

---

### **Issue: Email not syncing**

**Symptoms:**
- New emails appear in web but not in Outlook
- Takes hours for emails to appear
- Calendar not updating

**Resolution:**
1. Check sync settings:
   - Go to File → Options → Advanced
   - Under "Offline Settings", select your account
   - Click "Download mailbox"
   - Select what to sync (Mail, Calendar, etc.)

2. Restart Outlook (full close, not just minimize)

3. If issue persists:
   - Remove account: File → Account Settings → Remove
   - Restart Outlook
   - Re-add account

---

### **Issue: Outlook keeps asking for password**

**Causes:**
- Modern Authentication not enabled
- Expired cached credentials
- Password recently changed

**Resolution:**
1. Clear cached credentials:
   - Windows: Control Panel → Credential Manager → Remove Office 365 credentials
   - Mac: Keychain Access → Find Office 365 entry → Delete

2. Restart Outlook

3. Re-enter credentials when prompted

4. Check "Remember password" when you sign in

---

##  Outlook Web Access (OWA) - Alternative

If Outlook desktop app continues to have issues, user can access email via:
- **URL:** outlook.office.com
- **Browser:** Chrome, Edge, Safari
- **Features:** Works everywhere, no installation needed
- **Limitation:** Requires internet connection

---

##  Security Best Practices

- Do NOT save password in apps on shared computers
- Enable Multi-Factor Authentication (MFA)
- Educate users on phishing emails
- Disable auto-download of images in suspicious emails

---

##  Documentation for Ticket

Summary: New user Outlook setup / Outlook connection issue

Details:

-User: [name]
-Email: [address]
-Issue: Email not syncing / Cannot connect
-Steps taken: [list steps]
-Resolution: [outcome]
-Time spent: [minutes]

Status:  Resolved /  Escalated to L2
Next: User to test sending/receiving ema

