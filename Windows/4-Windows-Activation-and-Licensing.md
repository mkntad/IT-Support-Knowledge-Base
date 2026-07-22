# Windows Activation & Licensing

##  Objective
Resolve Windows activation failures, license expiration notifications, and product key invalidation issues.

## ⚠️ Common Error Messages
- "Windows is not activated"
- "Your Windows license will expire soon"
- "Error 0xC004C003" (Product key blocked)
- "Error 0x8007232B" (DNS name does not exist / KMS server unreachable)

---

##  Troubleshooting Steps

### **Issue: Error 0x8007232B / KMS Server Unreachable**

**Step 1: Check Network and VPN Status**
- Verify if the machine is an enterprise domain asset that uses KMS (Key Management Service)
- Connect the machine to the corporate network via Ethernet/Wi-Fi or establish an official VPN tunnel
- Run Command Prompt as Administrator and type: `ping ://yourdomain.com` (replace with your organization's actual KMS server address)

**Step 2: Force Activation via Command Line**
- Open Command Prompt as Administrator
- Force Windows to point to the correct KMS server: `slmgr.vbs /skms <kms_server_address>:<port>`
- Attempt to trigger activation online: `slmgr.vbs /ato`
- Wait for a popup dialog confirming success

---

### **Issue: Error 0xC004C003 (Invalid / Blocked Product Key)**

**Symptoms:**
- Freshly imaged machine or hardware-replaced machine refuses to activate
- Error indicates the licensing server rejected the product key

**Resolution:**
1. Check if the machine had a digital license embedded in the motherboard (OEM license)
2. Run Command Prompt as Administrator and extract the embedded key:
   `wmic path softwarelicensingservice get OA3xOriginalProductKey`
3. Copy the 25-character key displayed
4. Go to Settings → Update & Security → Activation → Change product key
5. Paste the extracted key and click Next to activate

---

### **Issue: "Your Windows License Will Expire Soon"**

**Symptoms:**
- A persistent pop-up warning appears on screen even though Windows currently shows as activated

**Resolution:**
1. Open Command Prompt as Administrator 
2. Check the detailed license expiration status by running: slmgr.vbs /dlv
3. Look at the " Product Key CHannel" row; if it says VOLUME_KMS, the machine simply needs to talk to the corporate netwrok to renew its rolling 180-day lease
4. If it is a retails machine, reset the licensing status by running: slmgr.vbs /rearm
5. Restart the computer, go to Activation settings, and re-enter the valid license key

##  Escalation Criteria

**Escalate to Level 2/3 if:**
-The organization has run out of available seats on the Multiple Activation Key (MAK) or KMS tier
-The digital entitlement license needs to be transferred between different corporate Microsoft Accounts
-The machine requires upgrading from Windows Home to Windows Pro but errors out repeatedly
-Downgrade rights must be exercised for legacy software compatibility


---

##  Security Notes
-Do not use unauthorized key generators, cracks, or public activation workarounds
-Never share corporate MAK or KMS keys with unauthorized staff or external third parties
-Maintain clear mapping records of keys assigned to specific physical hardware assets



---

##  Expected Resolution Time
-KMS activation via VPN: 5 minutes
-OEM key extraction and manual injection: 10 minutes
-License rearming and reboot: 10 minutes


---

##  When to Escalate
-If the entire department or site reports activation loss simultaneously (KMS server outage)
-If the extracted BIOS OEM key fails activation on a clean Microsoft vendor image
-If an audit reveals non-compliant licensing deployment across active production machines


---

##  What to Document in Ticket
-Current Windows Edition (e.g., Windows 11 Pro, Windows 10 Enterprise)
-Specific activation error code encountered
-License channel identified (Retail, OEM, Volume:KMS, Volume:MAK)
-Complete output or error message thrown by slmgr.vbs /ato