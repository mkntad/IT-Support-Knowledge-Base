# Email Sync Issues

##  Objective
Resolve local synchronization drops, discrepancies between local folders and Outlook Web App (OWA), and offline folder corruption.

## ⚠ Common Error Messages
- "Disconnected" or "Trying to connect..." in bottom status bar
- "Task 'Microsoft Exchange Server' reported error (0x8004010F) : 'The operation failed. An object could not be found.'"
- "Your mailbox has been temporarily moved on Microsoft Exchange server."

---

##  Troubleshooting Steps

### **Issue: Outlook Disconnected / Status Shows "Working Offline"**

**Step 1: Check Offline Status Toggle**
- Look at the bottom right corner of the Outlook window
- If it reads "Working Offline", navigate to the Send / Receive tab on the top ribbon
- Click the "Work Offline" button to deselect it and toggle the status back to online

**Step 2: Force Folder Synchronization**
- Select the folder that is missing recent emails (e.g., Inbox)
- Navigate to the Send / Receive tab
- Click "Update Folder" to force a sync call to the cloud architecture
- Check the bottom bar to confirm progress reads "Synchronizing..."

---

### **Issue: Mismatch Between OWA and Desktop Client (OST Corruption)**

**Symptoms:**
- User can see new emails on their mobile device or web browser but not in desktop Outlook
- Folders are missing sub-items locally

**Resolution:**
1. Verify the problem is local by opening a web browser and logging into `://office.com`
2. If OWA is correct, close desktop Outlook
3. Press `Windows Key + R` → Type `%localappdata%\Microsoft\Outlook` and press Enter
4. Locate the `.ost` data file corresponding to the user's email address
5. Rename the file by appending `.old` to the extension (e.g., `user@domain.com.ost.old`)
6. Relaunch Outlook; the application will automatically build a brand new, uncorrupted local cache file from the server

---

### **Issue: Sync Limits Restricting Viewable Mail**

**Symptoms:**
- User can only see emails from the last 12 months; older mail has vanished locally

**Resolution:**
1. Open Outlook → File → Account Settings → Account Settings
2. Select the email account and click "Change"
3. Locate the slider labeled "Download email for the past:" under Offline Settings
4. Drag the slider to the right to select "All" (or a preferred threshold like 3 Years if local disk space is restricted)
5. Click Next → Done, then restart Outlook to begin the historical download loop

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- Local cache rebuilds fail due to physical hardware sector damage on the storage drive
- Emails are missing entirely from the cloud servers (OWA is empty)
- Retention policies have inadvertently permanently purged the target user directories
- Exchange Online cloud sync metrics display active tenant disruption alerts

---

##  Security Notes

- Ensure BitLocker drive encryption is active before storing full historical mailboxes offline via `.ost`
- Do not convert `.ost` files into unprotected local `.pst` storage archives unless authorized by data preservation policies

---

##  Expected Resolution Time
- Offline toggle correction: 2 minutes
- Sync slider adjustment: 5 minutes (+ download processing time)
- Corrupted `.ost` file replacement: 15-30 minutes

---

##  When to Escalate
- If data corruption persists after multiple `.ost` regenerations
- If compliance or legal discovery requests require immediate mail structure retrieval
- If email delivery failures are global across the corporate domain network

---

##  What to Document in Ticket
- Current sync status shown in the lower right status bar
- Disk footprint size of the local `.ost` data file
- Comparison confirmation between desktop behavior and OWA behavior
- Any localized sync logs found inside the Outlook "Sync Issues" system folder

--- 
