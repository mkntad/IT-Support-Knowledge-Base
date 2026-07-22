 ### Account Recovery & Unlocking

###  Objective
Unlock compromised or locked corporate accounts, update MFA authentication paths, and manage Self-Service Password Reset (SSPR) procedures.

### ⚠ Common Error Messages
-"Your account has been locked. Contact your support person to unlock it."
-"Sign-in was blocked because it contains suspicious activity."
-"We're sorry, but we're having trouble signing you in. (Error Code: 50058 / 50140)" 

###  Troubleshooting Steps
***Issue: Account Blocked via Azure Entra ID Protection

Step 1: Confirm Lockout Cause

-Log into the Microsoft Entra admin center (://microsoft.com)
-Navigate to Identity → Users → All Users
-Search for the user and select their profile
-Check "Sign-in logs" to review risk assessments or conditional access blocks 

Step 2: Unblock Sign-In / Remediate User

-On the user overview panel, check if "Block sign-in" is toggled to Yes
-Click "Edit properties" and switch "Block sign-in" to No if manually locked
-If flagged for high risk: Navigate to Protection → Identity Protection → Risky Users
-Select the user account and click "Dismiss user risk" or trigger an immediate secure password reset call 

***Issue: Resetting Multi-Factor Authentication (MFA) Setup

Symptoms:

-User lost their smartphone or deleted the Microsoft Authenticator app and cannot pass login prompts 

Resolution:

-In Entra Admin Center, locate the target User Profile
-Click "Authentication methods" under the Manage subsection
-Review registered authentication methods (Phones, Authenticator Apps)
-Click "Require re-register MFA" from the top menu bar options
-The next time the user connects to an M365 app, they will automatically run through the initial verification wizard to associate their new phone or token device

###  Escalation Criteria
Escalate to Level 2/3 if:

-Global Administrator accounts are locked out or compromised
-Malicious actors have altered primary domain registration details or mail routing entries
-Legal/Security teams require complete technical forensic account tracking logs preserved for external audit 

###  Security Notes
-ALWAYS complete a strict identity verification check (e.g., photo ID, manager verification call) before changing secondary MFA delivery numbers or phone lines
-Never send temporary registration links or fallback bypass codes over unsecured platforms

### Expected Resolution Time
-Manual Entra ID unlock: 5 minutes
-MFA registration reset: 5 minutes
-Risk remediation and propagation: 10-15 minutes

###  When to Escalate
-If persistent phishing attacks continue generating high-risk alerts across multiple active personnel profiles
-If admin dashboard access is restricted during active security incidents

###  What to Document in Ticket
-Method utilized to successfully verify user identity prior to profile adjustment
-IP addresses and error tracking details pulled from the Entra ID active sign-in logs
-Exact remediation updates performed within administrative panel
