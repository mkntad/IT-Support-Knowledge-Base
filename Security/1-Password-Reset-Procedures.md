# Password Reset Procedures

##  Objective
Securely verify user identities, execute password overrides in Active Directory and Microsoft Entra ID, and assist users with Self-Service Password Reset (SSPR) protocols.

##  Common Error Messages
- "The username or password is incorrect."
- "Your password has expired and must be changed."
- "The password does not meet the length, complexity, or history requirements of the domain."
- "We're sorry, but we cannot reset your password at this time because your account is not configured for password reset."

---

##  Troubleshooting Steps

### **Issue: Standard Remote User Password Reset**

**Step 1: Perform Strict Out-of-Band Identity Verification**
- **CRITICAL:** Never execute a password reset without validating the user's identity first.
- Verify identity via an approved corporate method (e.g., manager verification, face-to-face video call matching their badge photo, or a one-time SMS verification token sent to a pre-registered mobile number).
- Document the successful verification method in the ticket.

**Step 2: Reset the Password via Hybrid/Cloud Administration Tools**
- **For Hybrid/On-Premises Accounts:** Open Active Directory Users and Computers (ADUC) → Locate the user account → Right-click and choose "Reset Password".
- **For Cloud-Only Accounts:** Log into the Microsoft Entra admin center (`://microsoft.com`) → Navigate to Identity → Users → All Users → Search for the user → Click "Reset password" at the top of their overview page.
- Input a complex, randomly generated temporary password (e.g., `Tr@nsit926!`).
- Ensure the option **"User must change password at next logon"** is checked.
- Communicate the temporary credential over a secure, private communication line (e.g., voice call or encrypted SMS). **NEVER** transmit passwords via standard email or open chat channels.

---

### **Issue: Self-Service Password Reset (SSPR) Wizard Fails**

**Symptoms:**
- User attempts to use the corporate password self-service portal (`://microsoftonline.com`) but receives an error stating they lack the appropriate setup or permissions.

**Resolution:**
1. Open the Microsoft Entra admin center and verify that SSPR is administratively enabled for the user's specific security group.
2. If enabled, click on the target User profile and select **Authentication methods**.
3. Verify that the user has at least two valid verification fields registered (such as an alternate email address, office phone number, or Microsoft Authenticator app binding).
4. If missing, clear the existing bad phone/email records, assign a temporary password, and instruct the user to complete their security proof registration at `aka.ms/setupsecurityinfo` immediately upon logging back into their profile.

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- High-profile executive or VIP accounts require manual administrative interventions.
- Multi-factor authentication mechanisms fail to send out automated phone verifications or SMS notifications globally across the tenant.
- A user account shows signs of an active brute-force or persistent credential-stuffing attack coming from a coordinated botnet array.

---

##  Security Notes

- Do not reuse universal temporary passwords across different corporate users (e.g., avoiding `Welcome2026!`).
- Maintain a strict zero-trust posture: treat all inbound password reset requests over incoming voice calls as unverified until explicit secondary identity screening passes.

---

##  Expected Resolution Time
- Identity verification and manual AD/Entra reset: 5 minutes
- SSPR attribute registration audit: 5-10 minutes
- Remote device profile password synchronization check: 10 minutes

---

## When to Escalate
- If an automated password change succeeds but the user is still blocked from accessing third-party integrated Single Sign-On (SSO) web business portals.
- If you suspect a user's phone line has been hijacked via a SIM-swap exploit to bypass secondary authentication security gates.

---

## What to Document in Ticket
- Specific identity verification method executed prior to generating credentials.
- Target directory platform adjusted (On-premises AD, Azure Hybrid Sync, Cloud-Only Entra ID).
- Timestamp indicating when the secure temporary password distribution line was completed.

---
--- 
