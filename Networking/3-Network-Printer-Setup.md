 # Network Printer Setup

##  Objective
Configure enterprise network printers, map shared print queues, and fix stalled driver processing errors.

##  Common Error Messages
- "Windows cannot connect to the printer."
- "Operation failed with error 0x0000011b."
- "Printer is in an error state."
- "The print spooler service is not running."

---

##  Troubleshooting Steps

### **Issue: Mapping Printer Over Network Fails (Error 0x0000011b / Permissions)**

**Step 1: Map directly via TCP/IP Port Address**
- Open Settings → Devices → Printers & scanners
- Click "Add a printer or scanner"
- Wait a few seconds and select "The printer that I want isn't listed"
- Select the bubble for "Add a printer using an IP address or hostname" and click Next
- Select "TCP/IP Device" from the device type dropdown list
- Input the exact physical IP address assigned to the printer device (e.g., `10.0.50.25`)
- Uncheck "Query the printer and automatically select the driver to use" and hit Next

**Step 2: Inject Manufacturer Specific Drivers Manually**
- When prompted for a driver package file layout, click "Have Disk..."
- Browse to the pre-downloaded, extracted type-3 or type-4 printer driver directory from the vendor (HP, Ricoh, Canon, etc.)
- Choose the `.inf` configuration file layout, select the exact printer model family designation, and finalize the installation script

---

### **Issue: Stalled Print Jobs / Spooler Freeze**

**Symptoms:**
- Document orders gather in the queue panel but fail to feed into the hardware engine; clicking delete leaves documents hanging on "Deleting...".

**Resolution:**
1. Open Command Prompt as Administrator
2. Stop the local print orchestration engine by executing:
   `net stop spooler`
3. Open Windows File Explorer and navigate directly into the system folder layout path:
   `C:\Windows\System32\spool\PRINTERS`
4. Delete every single file contained within this specific repository folder to empty the dead cache queue
5. Return to your Command Prompt window and wake up the print service engine by executing:
   `net start spooler`
6. Re-open the file panel and try firing a simple single page test pattern layout page to confirm operation

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- Group Policy Object (GPO) automated department deployment mapping sets fail to map drivers over network shares
- The server hosting the shared centralized print management queue architecture crashes or loses drive volumes
- Firmware updates must be applied to physical hardware sets due to software processing engine changes

---

##  Security Notes

- Do not configure universal print permission models to allow guest visibility into restricted accounting or human resources physical tray units
- Restrict printer configuration access web panels behind complex administrative passwords

---

##  Expected Resolution Time
- Clear local spooler queues: 5 minutes
- Direct IP manual port setup mapping: 10 minutes
- Driver injection updates and test configuration runs: 10-15 minutes

---

##  When to Escalate
- If an entire office department loses communication visibility to their shared standard copier hardware set
- If processing errors cause consecutive host machine blue screen failures on your client network

---

##  What to Document in Ticket
- Target physical network printer device manufacturer model and asset tracking tag numbers
- Target device static IP path setup mapping configurations
- Driver profile model name deployed on the workstation image profile

---
