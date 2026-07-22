# License Management & Activation

## Objective
Resolve Office 365 licensing activation flags, subscription conflicts, and product reduction feature locks.

## ⚠️ Common Error Messages
- "Product Deactivated" / "Unlicensed Product"
- "We couldn't verify your Microsoft 365 subscription"
- "Account Notice. Your Microsoft 365 subscription has an issue..."
- "The products we found in your account cannot be used to activate..."

---

## Troubleshooting Steps

### **Issue: Unlicensed Product Banner / Verification Failure**

**Step 1: Validate Admin Center Assignment**
- Log into the Microsoft 365 Admin Center (`://microsoft.com`)
- Navigate to Users → Active Users
- Search for the impacted user and click their profile
- Go to the "Licenses and apps" tab
- Ensure a valid license containing desktop apps (e.g., M365 Business Premium, Office 365 E3/E5) is checked
- Save any modifications and wait 5 minutes

**Step 2: Sign Out and Re-Authenticate Desktop Apps**
- Open Word or Excel
- Click File → Account (or Office Account)
- Click "Sign Out" under the User Information panel
- Sign out of all listed corporate or personal accounts
- Close all Office applications completely
- Relaunch Word, click "Sign In", and enter the authorized M365 domain credentials

---

### **Issue: Cached License Conflict Clearing**

**Symptoms:**
- M365 apps keep pulling old, expired, or previous corporate vendor licenses from the hardware configuration

**Resolution:**
1. Open Command Prompt as Administrator
2. Navigate to the Office installation directory by running:
   `cd "C:\Program Files\Microsoft Office\Office16"` (Use `Program Files (x86)` if 32-bit Office is running)
3. Check active keys by running: `cscript ospp.vbs /dstatus`
4. Locate the last 5 characters of the installed product key listed in the results (e.g., KH723)
5.Strip the license out by running: cscript ospp.vbs /unpkey:<last_5_characters>
6.Relaunch any Office application to prompt a clean, verified activation check 

 ### Escalation Criteria
**Escalate to Level 2/3 if:

-Activation scripts return errors indicating complete server communication blockage
-Shared Computer Activation (SCA) fails to function across multi-user Virtual Desktop Infrastructure (VDI) environments
-Enterprise volume licensing pools show seat starvation despite active billing contracts 
###  Security Notes

-Do not use bypass utilities or evaluation extension tools to circumvent license expirations
-Audit software asset deployments periodically to ensure corporate regulatory compliance metrics are maintained

### ⏱ Expected Resolution Time
-Admin Center verification: 5 minutes
-Account re-authentication: 5-10 minutes
-Command-line ospp.vbs license clearing: 10-15 minutes 

###  When to Escalate
-If global billing issues cause tenant-wide soft-deletion or feature lockouts
-If valid keys are repeatedly rejected by Microsoft regional authentication networks 

###  What to Document in Ticket
-Exact license sku assigned to user profile in Admin Center
-Current activation status printout from the ospp.vbs /dstatus query run locally
-Count of currently active devices bound to the user profile account 

