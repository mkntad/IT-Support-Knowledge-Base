### BIOS & Hardware Diagnostics

##  Objective

Run built-in manufacturer hardware assessment engines, access motherboard configuration utilities, and identify physical hardware component drops.

## Common Error Messages

-"No bootable device found"
-"S.M.A.R.T. Status Bad: Backup and Replace"
-"Thermal trip detected: System shut down to prevent damage"
-Machine emits repetitive audible beep pattern sequences when hitting the power button

## 🔍 Troubleshooting Steps

# Issue: System Fails to Boot / Running Pre-Boot Diagnostics

Step 1: Execute Manufacturer Specific Diagnostics Loop

-Shut the computer down completely
-Power the system back on and instantly tap the designated manufacturer diagnostic key repeatedly until the boot loader switches into the hardware testing panel:
-Dell: Tap F12 → Select "Diagnostics" or "Pre-boot System Assessment"
-HP: Tap F2 or Esc → Select "System Diagnostics"
-Lenovo: Tap F11 or restart and hold the Enter key to bring up the startup interrupt options, then select diagnostics
-Choose "Thorough Test" or "Extended Scan" to force the tool to stress test the internal storage drive sectors, system RAM modules, and cooling fan operation paths

Step 2: Parse Diagnostic Results and Codes

-Monitor the test run until completion or failure
-If a component fails, the engine will stop and display an explicit error string code accompanied by a validation tag (e.g., Dell Error Code: 2000-0142, validation 123456, which indicates hard drive mechanical failure)
-Document the exact code array for processing immediate under-warranty vendor physical drive or memory module replacement requests

# Issue: Checking Storage Health via OS (S.M.A.R.T. Diagnostics)

Symptoms:

-The computer exhibits severe system lockups, file read operations drop to a halt, or Windows throws warnings about imminent disk failure events.

Resolution:

-Open Command Prompt as Administrator
-Query the storage drive instrumentation framework directly by running:
wmic diskdrive get status
-Review the status column line printout:
-If it reads OK, the drive logic array is passing basic internal operations
-If it reads Pred Fail, the hard drive or solid-state drive has tripped its storage monitoring safety lines and is actively dying. Back up all user data files instantly and prep an image drive deployment setup

##  Escalation Criteria

Escalate to Level 2/3 if:

-Motherboard component modules pass all physical tests but fail to retain BIOS configuration settings after restarts (indicates dead CMOS coin battery)
-BIOS firmware files must be flashed manually to support newly integrated system microcode architectures
-Advanced RAID arrays lose sync layout profiles or drop physical volumes inside server rack configurations

##  Security Notes
-Restrict unauthorized entry into the system firmware menus by enforcing complex BIOS Supervisor Passwords across all corporate laptop deployments
-Ensure Secure Boot configurations remain enabled within the BIOS interface to guard against rootkit malware initialization routines

## Expected Resolution Time
-Fast-mode diagnostic test passes: 5-10 minutes
-Thorough/Extended sector verification testing runs: 30-60+ minutes
-S.M.A.R.T. local status verification: 2 minutes

## 📞 When to Escalate
-If a system fails to perform power-on self-test operations (POST) entirely and only flashes error ledger lights on the chassis trim
-If firmware password recovery tokens must be obtained directly from system vendors to bypass administrative lockout screens

## 📝 What to Document in Ticket
-Hardware test output error strings, failure codes, and tracking verification numbers
-Motherboard BIOS firmware version reference string (retrievable inside Windows via the msinfo32 tool)
-Action taken concerning local user profile data preservation (e.g., data backed up to cloud cloud space or external local target) 
