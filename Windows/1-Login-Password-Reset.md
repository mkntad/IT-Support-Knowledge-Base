# Windows Login & Password Reset Issues

##  Objective
Resolve user login failures and perform password resets for Windows domain machines.

##  Common Error Messages
- "The username or password is incorrect"
- "Your password has expired"
- "Account is locked"
- "Local user cannot log in to domain"

---

##  Troubleshooting Steps

### **Issue: Incorrect Password**

**Step 1: Verify Account Status**
- Ask user if they've recently changed their password
- Confirm they're using the correct domain (DOMAIN\username vs just username)
- Check if Caps Lock is on

**Step 2: Check Active Directory (if you have access)**
- Open Active Directory Users and Computers
- Locate the user account
- Right-click → Properties → Account tab
- Verify "Account is disabled" is NOT checked

**Step 3: Reset Password (IT Support)**
- In Active Directory Users and Computers, right-click user → Reset Password
- Set temporary password (e.g., "TempPass2024!")
- Check "User must change password at next logon"
- Share password securely via phone or secure channel (NOT email)

**Step 4: Confirm Resolution**
- Have user log in with temporary password
- Confirm they're prompted to change password
- Test access to network resources

---

### **Issue: Account Locked**

**Symptoms:**
- Login attempts rejected after several tries
- Message: "The account is locked"

**Resolution:**
1. In Active Directory Users and Computers, find the account
2. Right-click → Properties → Account tab
3. Uncheck "Account is locked out"
4. Click Apply → OK
5. Wait 5 minutes for replication
6. User can now log in again

**Why it happens:** Too many failed login attempts (security feature)

---

### **Issue: Password Expired**

**Symptoms:**
- "Your password has expired and must be changed"
- Cannot log in with current password

**Resolution Option 1 (User at Machine):**
1. At login screen, press Ctrl+Alt+Delete
2. Click "Change a password"
3. Enter old password and new password (2x)
4. Press Enter

**Resolution Option 2 (Admin via AD):**
1. In Active Directory, find user account
2. Right-click → Reset Password
3. Give user new temporary password
4. Uncheck "User must change password at next logon" (or check it for security)

---

### **Issue: Temporary Profile / Permission Denied**

**Symptoms:**
- User logs in but gets "Temporary user profile"
- Desktop appears blank or minimal
- Cannot access personal files

**Root Cause:**
- Active Directory replication issue
- Local vs. domain profile corruption

**Resolution:**
1. Have user log out completely
2. Wait 5-10 minutes (allows AD sync)
3. Log back in
4. If issue persists, restart the machine

**Advanced (if issue continues):**
- Delete corrupted local profile (requires admin)
- User will get a fresh profile on next login
- User's files on server will still be intact (but OneDrive/local docs may be lost)

---

## Escalation Criteria

**Escalate to Level 2/3 if:**
- Account shows as "disabled" but you don't have permissions to enable it
- User's account is compromised (suspicious activity)
- Multiple users cannot log in (domain controller issue)
- Password reset doesn't resolve login failure
- User needs to recover data from corrupted profile

---

## Security Notes

- **NEVER** share passwords via email or chat
- Use secure password delivery (phone call or in-person)
- Force password change after reset
- Enforce strong password policy (minimum 12 characters recommended)
- Document all password resets in your ticketing system

---

## Expected Resolution Time
- Simple reset: 5-10 minutes
- Locked account: 2-5 minutes
- Corrupted profile: 15-30 minutes (+ time for profile rebuild)

---

##  When to Escalate
- If issue persists after following these steps
- If you suspect account compromise
- If multiple users affected (domain issue)

---

## What to Document in Ticket
Summary: User unable to log in - password reset required

Details:

-User account: [username]
-Error message: "The username or password is incorrect"
-Steps taken: Verified account is active, reset password
-Resolution: Provided temporary password
-User confirmed: [Yes/No]
-Time spent: 10 minutes
-Next steps: User to change password at next login 
