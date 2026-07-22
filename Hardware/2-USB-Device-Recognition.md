# USB Device Recognition

##  Objective
Isolate hardware communication faults, refresh host controller root hubs, and resolve unrecognized peripheral states on client workstations.

## ⚠ Common Error Messages
- "USB Device Not Recognized"
- "The last USB device you connected to this computer malfunctioned"
- "Device descriptor request failed (Code 43)"
- "Unknown USB Device (Configuration descriptor request failed)"

---

##  Troubleshooting Steps

### **Issue: Unrecognized USB Controller / Code 43 Error State**

**Step 1: Force Power Cycle the Motherboard Bus**
- If troubleshooting a desktop, shut down the system completely
- Unplug the main power supply cable from the back of the computer tower
- Press and hold down the physical power button on the front of the chassis for 15-20 seconds to drain remaining residual electrical current from the motherboard capacitors
- Reconnect the power cable, boot into Windows, and plug the USB device back in

**Step 2: Refresh the Universal Serial Bus Controllers Array**
- Open Device Manager (`devmgmt.msc`)
- Scroll down to the bottom and expand the "Universal Serial Bus controllers" section
- Right-click on the "USB Root Hub" entries (or "Generic USB Hub") and select "Uninstall device"
- If prompted to confirm, click Uninstall (Note: Your USB mouse or keyboard may stop responding briefly if connected to that specific hub)
- Click "Action" in the top menu bar of Device Manager and select "Scan for hardware changes"
- Windows will instantly scan the hardware buses and automatically reinstall fresh copies of the root controller drivers

---

### **Issue: External USB Storage / Mass Storage Device Not Mounting**

**Symptoms:**
- The USB flash drive or external hard drive chimes when plugged in but does not appear in File Explorer under "This PC".

**Resolution:**
1. Press `Windows Key + X` and select "Disk Management" from the power-user menu
2. Look at the lower visual panel to find the external disk block (it may say "Unallocated", "Not Initialized", or show a healthy partition with no drive letter)
3. If it has no letter assignment: Right-click the healthy partition volume → Select "Change Drive Letter and Paths..." → Click "Add" → Choose an available letter (e.g., E:, F:, G:) → Click OK
4. If it reads "Offline" due to a policy conflict: Right-click the disk descriptor box on the left side and choose "Online"
5. If the disk shows as "Unallocated", the data payload is likely missing or the disk must be formatted (Verify with user before formatting)

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- USB host controllers persistently throw Code 10 errors that do not resolve after chipset driver updates
- Physical damage is evident inside the chassis USB ports (bent pins, cracked tabs) causing electrical shorts
- Corporate Endpoint Data Loss Prevention (DLP) or Group Policies completely block USB hardware initialization across the network

---

##  Security Notes

- **NEVER** insert unknown or unverified USB flash drives found in public areas into corporate systems (BadUSB/Rubber Ducky protection)
- Encrypt all authorized external company storage drives using BitLocker To Go or approved corporate encryption suites

---

##  Expected Resolution Time
- USB hub driver refresh cycle: 3-5 minutes
- Hardware power drain reset: 5 minutes
- Disk Management volume mounting: 5 minutes

---

##  When to Escalate
- If external hard drives draw too much power and repeatedly trip the physical motherboard over-current protection thresholds
- If administrative restrictions require creating targeted Registry overrides for specific hardware IDs

---

##  What to Document in Ticket
- Type of USB peripheral being attached (Storage, HID, Audio Interface, Camera)
- Error string or Code identifier listed inside the Device Manager properties screen
- Result of testing the device on a separate, known-good reference workstation

---
--- 
