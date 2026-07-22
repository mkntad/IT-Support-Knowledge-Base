 Windows Update Problems

##  Objective
Resolve Windows Update failures, stuck downloads, and update installation errors on client machines.

##  Common Error Messages
- "Updates failed. There were problems installing some updates..."
- "Error 0x80070002" / "0x80240020" / "0x80070422"
- "We couldn't complete the updates. Undoing changes."
- "Checking for updates..." (Stuck indefinitely)

---

##  Troubleshooting Steps

### **Issue: Update Installation Fails with Error Code**

**Step 1: Run Built-in Troubleshooter**
- Open Settings → Update & Security → Troubleshoot
- Click "Additional troubleshooters"
- Select "Windows Update" and click "Run the troubleshooter"
- Follow the on-screen prompts and apply fixes

**Step 2: Clear Windows Update Cache (SoftwareDistribution)**
- Open Command Prompt as Administrator
- Stop services by running: 
  `net stop wuauserv`
  `net stop cryptSvc`
  `net stop bits`
  `net stop msiserver`
- Rename the cache folders by running:
  `ren C:\Windows\SoftwareDistribution SoftwareDistribution.old`
  `ren C:\Windows\System32\catroot2 catroot2.old`
- Restart services by running:
  `net start wuauserv`
  `net start cryptSvc`
  `net start bits`
  `net start msiserver`
- Reboot the computer and check for updates again

**Step 3: Run System File Checks**
- Open Command Prompt as Administrator
- Run `DISM.exe /Online /Cleanup-image /Restorehealth`
- Wait for completion, then run `sfc /scannow`
- Restart the machine if repairs were made

---

### **Issue: Windows Update Stuck Downloading or Installing**

**Symptoms:**
- Download progress frozen at a specific percentage (e.g., 0% or 99%) for hours
- High CPU or disk usage by "System" or "Windows Update"

**Resolution:**
1. Verify internet connectivity and ensure no firewall or proxy is blocking Microsoft update servers
2. Open Services (`services.msc`)
3. Locate "Background Intelligent Transfer Service" (BITS), right-click, and select Restart
4. Locate "Windows Update", right-click, and select Restart
5. If the download remains frozen, perform the **SoftwareDistribution cache clear** outlined above

---

### **Issue: "Undoing Changes" Loop**

**Symptoms:**
- Machine restarts repeatedly, displays "We couldn't complete the updates, Undoing changes", and rolls back

**Resolution:**
1. Boot the machine into Safe Mode
2. Navigate to `C:\Windows\SoftwareDistribution\Download` and delete all contents inside this folder
3. Open Command Prompt as Administrator and run `chkdsk c: /f` to check for file system corruption
4. Reboot normally and try installing updates one by one rather than all at once

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- Windows Update failure results in a Blue Screen of Death (BSOD) or boot loop
- The machine requires a complete operating system reinstall to function
- WSUS (Windows Server Update Services) or Group Policy issues block updates network-wide
- Disk space is critically low and system partition resize is required

---

##  Security Notes

- Do not disable the Windows Update service permanently to bypass errors
- Ensure missing security patches are prioritized to maintain organizational compliance
- Document any third-party antivirus software disabled during troubleshooting

---

##  Expected Resolution Time
- Windows Update Troubleshooter: 5-10 minutes
- Cache clearing & DISM/SFC scans: 20-40 minutes
- Fixing boot loops / Safe Mode repair: 30-60 minutes

---

##  When to Escalate
- If update failures cause critical line-of-business applications to crash
- If the system remains stuck in an infinite rollback loop after clearing the cache
- If more than 5 machines in the same department experience the same update error code

---

##  What to Document in Ticket
- Specific error codes (e.g., 0x80070002)
- KB numbers of the specific updates failing to install
- Results of the SFC and DISM scans
- Actions taken (e.g., cache cleared, services restarted)
