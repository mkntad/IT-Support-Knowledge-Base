# Account Lockout Resolution

##  Objective
Unlock domain and cloud user profiles, identify hidden background authentication sources causing rapid lock loops, and restore system access.

##  Common Error Messages
- "The referenced account is currently locked out and may not be logged on to."
- "Your account has been temporarily locked to prevent unauthorized use. Try again later."
- "Sign-in was blocked because it contains suspicious activity (Error 50053)."

---

##  Troubleshooting Steps

### **Issue: Simple Account Unlock Request**

**Step 1: Authenticate the User and Uncheck the Lock Flag**
- Run an out-of-band identity check to ensure the request is legitimate.
- **For Local Domain Controllers:** Open Active Directory Users and Computers. Locate the user → Right-click and choose Properties → Go to the Account tab. Check the box labeled **"Unlock account"** → Click Apply and OK.
- **For Cloud Accounts:** In Microsoft Entra ID, locate the User profile. Check if the "Block sign-in" switch is set to Yes. If it is locked automatically due to security risks, navigate to Protection → Identity Protection → Risky Users, select the account, and click **"Dismiss user risk"** to clear the automated lock engine.

---

### **Issue: Persistent / Loop Lockouts (Account Instantly Re-locks)**

**Symptoms:**
- The user account is unlocked by IT support, but within seconds or minutes it automatically flags as locked again before the user can even type their new password on their workstation.

**Resolution:**
1. Instruct the user to turn off all secondary corporate devices (smartphones, tablets, secondary testing laptops).
2. Open the user's primary workstation and open **Credential Manager** via Windows search. Clear out all cached corporate entries under "Windows Credentials".
3. Open Windows Services (`services.msc`) and verify that no local background tasks or automation scripts are running using outdated administrative credentials.
4. Check if the user has any mapped network drives or scheduled printer jobs pending that might be attempting background authentications using old credentials.
5. If the source domain machine cannot be found, download the official Microsoft **Account Lockout Status (LockoutStatus.exe)** diagnostic tool to pinpoint which exact Active Directory Domain Controller is capturing the bad authentication calls in real time.

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- An account continues to lock out globally across the network even when all physical user hardware targets are entirely powered down.
- Lockout log captures indicate a high-volume internal network scanning tool or malware strain is actively attempting to brute-force domain admin privileges.

---

##  Security Notes

- Do not modify or circumvent default corporate domain Account Lockout Threshold Group Policies (e.g., relaxing rules from 5 bad attempts up to 20 attempts) without explicit written authorization from the Chief Information Security Officer (CISO).
- Keep track of repeating account lock alerts as they frequently serve as indicators of compromised user endpoints.

---

##  Expected Resolution Time
- Direct Active Directory account unlock: 2 minutes
- Tracking and clearing cached bad credential loops: 15-20 minutes
- Domain Controller log tracking using diagnostic utilities: 20-30 minutes

---

##  When to Escalate
- If the account lockout behavior aligns with a suspected distributed denial-of-service (DDoS) targeting infrastructure gateways.
- If corporate security operation center (SOC) sensors flag the lockout behavior as an indicator of an active lateral-movement attack sequence.

---

##  What to Document in Ticket
- Count of consecutive lock cycles observed during the support window.
- List of secondary endpoints (mobile mail apps, old laptops) checked and remediated.
- Device ID or IP address pinpointed by domain authentication audit logs as the origin of the bad credential attempts.

---
--- 
